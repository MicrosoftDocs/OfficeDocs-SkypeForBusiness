---
title: "Azure Sentinel and Microsoft Teams"
author: MicrosoftHeidi
ms.author: tracyp
manager: dansimp
ms.topic: reference
ms.service: msteams
audience: admin
ms.reviewer:
description: Security advice and learnings for IT admins on using Sentinel to monitor and hunt threats that may arise in Teams.
localization_priority: Priority
search.appverid: MET150
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
  - remotework
ms.custom: 
- Security
appliesto: 
  - Microsoft Teams
---

# Azure Sentinel and Microsoft Teams

> [!IMPORTANT]
> Azure Sentinel now has an integrated connector. For more information, see [Connect Office 365 Logs to Azure Sentinel](/azure/sentinel/connect-office-365). This is the recommended route for collecting these logs and supersedes the collection methods described below.

Teams serves a central role in both communication and data sharing in the Microsoft 365 Cloud. Because the Teams service touches on so many underlying technologies in the Cloud, it can benefit from human and automated analysis not only when it comes to *hunting in logs*, but also in *real-time monitoring of meetings*. Azure Sentinel offers admins these solutions.

> [!NOTE]
> Need a refresher on Azure Sentinel? [This article](/azure/sentinel/overview) is just the thing.

## Sentinel and Microsoft Teams Activity Logs

This article focuses on collecting Teams activity logs in Azure Sentinel. Aside from allowing administrators to put security management under one pane of glass (including any selected 3rd party devices, Microsoft Threat Protection, and other Microsoft 365 Workloads), Sentinel workbooks, and runbooks can make security monitoring systematic. A good first step in this process is collecting the needed logs for analysis.

> [!NOTE]
> More than one Microsoft 365 subscription can be surfaced in the same instance of Azure Sentinel. This will allow for [realtime monitoring](/azure/sentinel/livestream) and hunting for threats in historical log file s. Administrators will be able to hunt using [cross-resource queries](/azure/azure-monitor/log-query/cross-workspace-query), that is within a single resource group, across resource groups, or in another subscription.

## Step 1: Collect Teams logs: Enable Audit logs in M365

Because Teams logs activity through M365, audit logs aren't collected by default. Turn on this feature via [these steps](https://docs.microsoft.com/microsoft-365/compliance/turn-audit-log-search-on-or-off). Teams data is collected in the M365 audit under *Audit.General*.

## Step 2: Connect Office 365 logs to Azure Sentinel

Azure Sentinel provides a built-in connector for Office 365 logs, which enables you to ingest Teams data into Azure Sentinel together with other Office 365 data.
 
In Azure Sentinel, enable the Office 365 data connector. For more information, see the [Azure Sentinel documentation](/azure/sentinel/connect-office-365).

## Helpful hunting KQL queries

Use these queries to familiarize yourself with your Teams data and Teams environment. Knowing how the environment should look and behave is a good first step in recognizing suspicious activity. From there, you can branch out into threat hunting.

### Federated external users query

Get the list of Teams sites that have federated external users. These users will have a domain name / UPN suffix that isn't owned by your organization. In this example query, the organization owns contoso.com.

```Kusto
OfficeActivity
| where TimeGenerated > ago(7d)
| where Operation =~ "MemberAdded"
| where parse_json(Members)[0].Role == 3
| project TeamName, Operation, UserId, Members
| mv-expand bagexpansion=array Members
| evaluate bag_unpack(Members)
```

> [!TIP]
> To learn more about External and Guest access types in Teams see [Communicate with users from other organizations](communicate-with-users-from-other-organizations.md), or the [Participant Types](teams-security-guide.md#participant-types) section in the Teams Security Guide.

### Who recently joined / Whose role changed

Query a specific user to check if they were added to a Teams channel in the last 7 days, or within a week:

```Kusto
OfficeActivity
| where TimeGenerated > ago(7d)
| where Operation =~ "MemberAdded"
| where Members has "<DisplayName>" or Members has "<UserPrincipalName>"
| project TeamName, Operation, UserId, Members
```

Was a user's role changed for a Team in the last 7 days:

```Kusto
OfficeActivity
| where TimeGenerated > ago(7d)
| where Operation =~ "MemberRoleChanged"
| project TeamName, Operation, UserId, Members
| mv-expand bagexpansion=array Members
| evaluate bag_unpack(Members)
| where Role == '1'
``` 

### External users from unknown or new organizations

In Teams, you can add external users to your environment or channels. Organizations often have a limited number of key partnerships and add users from among these partners. This KQL looks at external users added to teams who come from organizations that haven't been seen or added before.

For more information, see the query in the [Azure Sentinel community github](https://github.com/Azure/Azure-Sentinel/blob/master/Hunting%20Queries/OfficeActivity/ExternalUserFromNewOrgAddedToTeams.yaml).

### External users who were added and then removed

Attackers with some level of existing access may add a new external account to Teams to access and exfiltrate data. They may also quickly remove that user to hide that they made access. This query hunts for external accounts that are added to Teams and swiftly removed to help identify suspicious behavior.

For more information, see the query in the [Azure Sentinel community github](https://github.com/Azure/Azure-Sentinel/blob/master/Detections/OfficeActivity/ExternalUserAddedRemovedInTeams.yaml).

### New bot or application added

Teams has the ability to include apps or bots in a Team to extend the feature set. This includes custom apps and bots. In some cases, an app or bot could be used to establish persistence in Teams without needing a user account, as well as access files and other data. This query hunts for apps or bots that are new to Teams.

For more information, see the query in the [Azure Sentinel community github](https://github.com/Azure/Azure-Sentinel/blob/master/Hunting%20Queries/OfficeActivity/NewBotAddedToTeams.yaml).

### User accounts who are Owners of large numbers of Teams

Attackers looking to elevate their privileges may assign themselves Owner privileges of a large number of diverse teams, when, usually, users create and own a small number of teams around specific topics. This KQL query looks for suspicious behavior.

For more information, see the query in the [Azure Sentinel community github](https://github.com/Azure/Azure-Sentinel/blob/master/Hunting%20Queries/OfficeActivity/MultiTeamOwner.yaml).

### Many Team deletions by a single user

Attackers can cause disruptions and jeopardize projects and data by deleting multiple teams. Because teams are generally deleted by individual Owners, a central deletion of many teams can be a sign of trouble. This KQL looks for single users who delete multiple teams.

For more information, see the query in the [Azure Sentinel community github](https://github.com/Azure/Azure-Sentinel/blob/master/Hunting%20Queries/OfficeActivity/MultipleTeamsDeletes.yaml).

### Expanding your threat hunting opportunities

You can expand your hunting by combining queries from resources like Azure Active Directory (Azure AD), or other Office 365 workloads with your Teams queries. One example is combining detection of suspicious patterns in Azure AD SigninLogs, and using that information while hunting for Team Owners.

```Kusto
let timeRange = 1d;
let lookBack = 7d;
let threshold_Failed = 5;
let threshold_FailedwithSingleIP = 20;
let threshold_IPAddressCount = 2;
let isGUID = "[0-9a-z]{8}-[0-9a-z]{4}-[0-9a-z]{4}-[0-9a-z]{4}-[0-9a-z]{12}";
let azPortalSignins = SigninLogs
| where TimeGenerated >= ago(timeRange)
// Azure Portal only and exclude non-failure Result Types
| where AppDisplayName has "Azure Portal" and ResultType !in ("0", "50125", "50140")
// Tagging identities not resolved to friendly names
| extend Unresolved = iff(Identity matches regex isGUID, true, false);
// Lookup up resolved identities from last 7 days
let identityLookup = SigninLogs
| where TimeGenerated >= ago(lookBack)
| where not(Identity matches regex isGUID)
| summarize by UserId, lu_UserDisplayName = UserDisplayName, lu_UserPrincipalName = UserPrincipalName;
// Join resolved names to unresolved list from portal signins
let unresolvedNames = azPortalSignins | where Unresolved == true | join kind= inner (
   identityLookup ) on UserId
| extend UserDisplayName = lu_UserDisplayName, UserPrincipalName = lu_UserPrincipalName
| project-away lu_UserDisplayName, lu_UserPrincipalName;
// Join Signins that had resolved names with list of unresolved that now have a resolved name
let u_azPortalSignins = azPortalSignins | where Unresolved == false | union unresolvedNames;
let failed_signins = (u_azPortalSignins
| extend Status = strcat(ResultType, ": ", ResultDescription), OS = tostring(DeviceDetail.operatingSystem), Browser = tostring(DeviceDetail.browser)
| extend FullLocation = strcat(Location,'|', LocationDetails.state, '|', LocationDetails.city)
| summarize TimeGenerated = makelist(TimeGenerated), Status = makelist(Status), IPAddresses = makelist(IPAddress), IPAddressCount = dcount(IPAddress), FailedLogonCount = count()
by UserPrincipalName, UserId, UserDisplayName, AppDisplayName, Browser, OS, FullLocation
| mvexpand TimeGenerated, IPAddresses, Status
| extend TimeGenerated = todatetime(tostring(TimeGenerated)), IPAddress = tostring(IPAddresses), Status = tostring(Status)
| project-away IPAddresses
| summarize StartTime = min(TimeGenerated), EndTime = max(TimeGenerated) by UserPrincipalName, UserId, UserDisplayName, Status, FailedLogonCount, IPAddress, IPAddressCount, AppDisplayName, Browser, OS, FullLocation
| where (IPAddressCount >= threshold_IPAddressCount and FailedLogonCount >= threshold_Failed) or FailedLogonCount >= threshold_FailedwithSingleIP
| project UserPrincipalName);
OfficeActivity
| where TimeGenerated > ago(time_window)
| where Operation =~ "MemberRoleChanged"
| mv-expand bagexpansion=array Members
| evaluate bag_unpack(Members)
| where Role == '2'
| where Members in (failed_signins)
```

Also, you can make the SigninLogs detections specific to Teams by adding a filter for only Teams-based sign-ins by using:

```Kusto
| where AppDisplayName has 'Teams'
```

To help explain using where AppDisplayName has "Teams" further, the KQL below demonstrates a successful logon from one IP address with failure from a different IP address, but scoped only to Teams sign-ins:

```Kusto
let timeFrame = 1d;
let logonDiff = 10m;
SigninLogs 
  | where TimeGenerated >= ago(timeFrame) 
  | where ResultType == "0" 
  | where AppDisplayName has "Teams"
  | project SuccessLogonTime = TimeGenerated, UserPrincipalName, SuccessIPAddress = IPAddress, AppDisplayName, SuccessIPBlock = strcat(split(IPAddress, ".")[0], ".", split(IPAddress, ".")[1])
  | join kind= inner (
      SigninLogs 
      | where TimeGenerated >= ago(timeFrame) 
      | where ResultType !in ("0", "50140") 
      | where ResultDescription !~ "Other"  
      | where AppDisplayName startswith "Microsoft Teams"
      | project FailedLogonTime = TimeGenerated, UserPrincipalName, FailedIPAddress = IPAddress, AppDisplayName, ResultType, ResultDescription
  ) on UserPrincipalName, AppDisplayName 
  | where SuccessLogonTime < FailedLogonTime and FailedLogonTime - SuccessLogonTime <= logonDiff and FailedIPAddress !startswith SuccessIPBlock
  | summarize FailedLogonTime = max(FailedLogonTime), SuccessLogonTime = max(SuccessLogonTime) by UserPrincipalName, SuccessIPAddress, AppDisplayName, FailedIPAddress, ResultType, ResultDescription 
  | extend timestamp = SuccessLogonTime, AccountCustomEntity = UserPrincipalName, IPCustomEntity = SuccessIPAddress
```

## Important information and updates

**Thank you for content collaboration, Pete Bryan, Nicholas DiCola, and Matthew Lowe.** Pete Bryan and the people he collaborates with will continue to develop detection and hunting queries for Teams, so keep in touch with this [GitHub](https://github.com/Azure/Azure-Sentinel/tree/master/Hunting%20Queries/TeamsLogs) repository for updates.  Monitor for updates to the [parser](https://github.com/Azure/Azure-Sentinel/blob/master/Parsers/Teams_parser.txt) and [logic app](https://github.com/Azure/Azure-Sentinel/tree/master/Playbooks/Get-O365Data) used in this article. You can also join and contribute to the [Azure Sentinel community](https://github.com/Azure/Azure-Sentinel/wiki). Thank you! Happy hunting.

[Registering your application in Azure AD](/skype-sdk/ucwa/registeringyourapplicationinazuread%C2%A0%20%20%C2%A0)


[Turn audit log search on or off](https://docs.microsoft.com/microsoft-365/compliance/turn-audit-log-search-on-or-off)

[What is Azure Sentinel](/azure/sentinel/overview)
