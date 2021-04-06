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

## Step 1: Collect Teams logs

This section has three parts:

1. Enabling Audit Logs in **Microsoft 365**.
2. Registering an App in **Microsoft Azure** to permit authentication and authorization for log collection.
3. Registering the API subscription that will allow log collection via Microsoft 365 API via **PowerShell**.

### Enable Audit logs in Microsoft 365

Because Teams logs activity through Microsoft 365, audit logs aren't collected by default. Turn on this feature via [these steps](/microsoft-365/compliance/turn-audit-log-search-on-or-off?view=o365-worldwide&viewFallbackFrom=o365-worldwide%c2%a0). Teams data is collected in the Microsoft 365 audit under *Audit.General*.

### Register an App in Microsoft Azure for log collection

> [!TIP]
> Before you begin, you will need to record you **Application ID / Client ID**, and your **Tenant ID** for later use. Be sure to capture them as you walk through app registration steps below. You will see both IDs.
>- After your app is created, click App Registration on the quick launch side-bar > Find your new app's display name > copy the Application (client) ID.
>- Click Overview on the quick launch side-bar > copy the Directory (tenant) ID.

Authenticate and authorize an Azure Active Directory (Azure AD) app to collect log data from the API.

1. Navigate to your *Azure AD* blade in the Azure portal.
2. Click on *App registrations* in the quick launch side-bar.
3. Select *New registration*.
4. Name your Teams log collecting app and click *Register*.
5. Click along this path: *API Permissions* > *Add a permission* > *Office 365 Management APIs* > *Application permissions*.
6. Expand Activity Feed and check *ActivityFeed.Read*.
7. Choose *Grand admin consent* here. Click Yes when prompted asking if you mean it.
8. Click *Certificates and Secrets* in the side-bar> *New client secret* button.
9. On the New client secret window, enter a description for the new Client Secret, make sure you choose 'Never' for Expiration, and click *Add*.

> [!IMPORTANT]
> It's **critical** to copy the new client secret into a password manager entry that goes under the name of the newly created app. You won't be able to get back to look at this secret after the closing out of the Azure blade (*blade* being the Azure term for window).

### Register the API with PowerShell to collect Teams logs

The final step in setup is to collect and register the API subscription so that you can collect your log data. This is done via PowerShell REST calls to the Microsoft 365 Management Activity API.

Be ready to supply **Application (client) ID**, the new **Client Secret**, your **URL domain for M365**, and **Directory (tenant) ID** values in the PowerShell cmdlet below.

```PowerShell
$ClientID = "<Application (client) ID>"  
$ClientSecret = "<Client secret>"  
$loginURL = "https://login.microsoftonline.com/"  
$tenantdomain = "<domain>.onmicrosoft.com"  

$TenantGUID = "<Directory (tenant) ID>"  
$resource = "https://manage.office.com"  
$body = @{grant_type="client_credentials";resource=$resource;client_id=$ClientID;client_secret=$ClientSecret}
$oauth = Invoke-RestMethod -Method Post -Uri $loginURL/$tenantdomain/oauth2/token?api-version=1.0 -Body $body  
$headerParams = @{'Authorization'="$($oauth.token_type) $($oauth.access_token)"}
$publisher = New-Guid
Invoke-WebRequest -Method Post -Headers $headerParams -Uri "https://manage.office.com/api/v1.0/$tenantGuid/activity/feed/subscriptions/start?contentType=Audit.General&PublisherIdentifier=$Publisher"
```

## Step 2: Deploy a Sentinel Playbook to ingest the Teams logs

Azure Sentinel Playbooks (also called Logic Apps) will allow Azure to ingest your collected Teams data. The Logic App queries Office 365 to find the audit data it writes into the Azure Sentinel workspace.

Use [this](https://github.com/Azure/Azure-Sentinel/tree/master/Playbooks/Get-O365Data) ARM template to deploy your Sentinel Playbook.

Things to remember:

1. You will need to walk through the ARM template and replace certain of the values with values appropriate for your own environment.
2. You will need to allow time between the ingestion of logs and looking at the results in Azure Sentinel.

   Wait for 5 to 10 minutes, understanding that if there is no data within the past 5 minutes you will see an error message. Check Audit logs and keep in mind that because Teams information is in the Audit.General events, which collects more than Teams logs, results should appear within 5 to 10 minutes on systems that are in use. If using a text environment, be certain to use Teams in order to generate logging.

![Graphic that shows the logic app classes.](media/tracyp-teams-sentinel-logic-app.png#thumbnail)

 <p><details><summary> Explanation of actions in the graphic:
  
  </summary>

  •	Recurrence is the Logic App Trigger that tells the workflow to run every hour.
  <p>
  •	The Current Time action is very basic and just gets the current time.
  <p>
  • Initialize Variable creates a variable called NextPage and sets it to 1. This will be used later in order to handle pagination from the O365 API.
  <p>
  •	Initialize Variable 2 creates an empty variable called Start Time.
  <p>
  •	Run Query and list results is an Azure Monitor action that will query the workspace for the last O365 log that was entered from the Logic App.
  <p>
  •	Condition 4 is used to check whether the Run Query and list results query returned any data. This is done to check if this is the very first time the Logic App has been used. If no data is returned, StartTime variable is set to Now – 24 hours. If data is returned, StartTime is set to the last record TimeGenerated. This is done so that the query can get data from the last entry till now in the poll against the O365 API, or in the last 24 hours if this is the first run.
  <p>
  •	Initialize Variable 3 creates a variable called AvailableUri. This is a string with the URL built using the StartTime and CurrentTime as start and end times, respectively.
  <p>
  •	The Until condition is a loop that allows the logic app to keep polling the API to see if there is more data (pagination). As long as NextPage variable is 1 the loop will continue. Later this variable will be updated if there are no more pages left to retrieve.
  <p>
  •	Inside the Until loop, the first HTTP step Connects to the AvailableURI. This URI returns a list of available content and each contents URI. There's more on how this works at this URL: https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-reference#list-available-content.
  <p>
  •	Next a check is run to make sure data is returned. The Condition checks if the length of the body is 0. If so there is no data to write to Log Analytics. If the value is greater than 0, there is data to process.
  <p>
  •	If data is detected, it must next be processed. Parse JSON defines a schema of the returned data. This allows logic apps to use the parsed data as Dynamic content in later steps.
  <p>
  •	Since the returned list of available data is an Array, a For Each action is used to loop through the list of available content.
  <p>
  •	Next is grabbing the content.  HTTP is used again to get the contentUri (a dynamic property created from Parse JSON), which is the URL of the data to retrieve.
  <p>
  •	Parse JSON is also used to parse the returned data. You can find some sample content at this URL: https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-reference#list-available-content.
  <p>
  •	The data returned is also an array. A For Each loop can be used here as well. In this loop, the workflow takes the current item of data and uses the Send Data action to write the data to Log Analytics.
  <p>
  • Since there may be multiple pages of available content, a condition checks if the NextPageUri is not NULL. If it is NULL, or empty, NextPage is set to 0, which ends the Until loop. If it contains a URL, the AvaibleUri variable is updated to that URL. This way, the next run of the Until loop uses a next available URL, and not the starting URL.

  </details>

> [!TIP]
> You may choose to use an *Azure Function* to ingest those logs, instead, and if you do, the information on how to deploy is [here](https://github.com/Azure/Azure-Sentinel/tree/master/DataConnectors/O365%20Data), or [here](https://github.com/Azure/Azure-Sentinel/tree/master/DataConnectors/O365%20DataCSharp), depending on your preference.

With the connector (whichever of the options above you chose) running, you should see a custom table called O365API_CL in the Azure Sentinel workspace. This will house your Teams logs.

## Step 3: Use Sentinel to monitor Microsoft Teams

Identity is an important attack vector to monitor when it comes to Microsoft Teams. Because Azure Active Directory (Azure AD) is the underpinning of Microsoft 365's directory, including Teams, collecting and hunting for threats in Azure AD logs around authentication will be useful in capturing suspicious behavior around identity. You can use the built-in connector to pull Azure AD data into Azure Sentinel, and use these [detection](https://github.com/Azure/Azure-Sentinel/tree/master/Detections/SigninLogs) and [hunting](https://github.com/Azure/Azure-Sentinel/tree/master/Hunting%20Queries/SigninLogs) queries to look for problems.

Regarding attacks specific to Microsoft Teams, threats to data, for example, Azure Sentinel also has means to monitor for them and hunt them down.

### Create a parser for your data

The first thing to do in order to make sense of the large set of collected data is to give it meaning by parsing it. This is done with a Kusto Query Language (KQL) Function that makes the data easier to use.

> [!NOTE]
> KQL functions are KQL queries saved as a data-type called 'function'. KQL functions have an alias that can be entered into the query box in Sentinel to quickly run the query again. For more about KQL functions and how to build a parser function, read [this Tech Community article](https://techcommunity.microsoft.com/t5/azure-sentinel/using-kql-functions-to-speed-up-analysis-in-azure-sentinel/ba-p/712381).
 
 The parser below is a customizable example aimed at selecting a subset of the Office 365 Management API fields relevant to *Teams*. There is also a suggested parser [GitHub](https://github.com/Azure/Azure-Sentinel/blob/master/Parsers/Teams_parser.txt), but the parser below can be modified to fit different needs and preferences.

```kusto
O365API_CL
| where Workload_s =~ "MicrosoftTeams"
| project TimeGenerated,
          Workload=Workload_s,
          Operation=Operation_s,
          TeamName=columnifexists('TeamName_s', ""),
          UserId=columnifexists('UserId_s', ""),
          AddOnName=columnifexists('AddOnName_s', AddOnGuid_g),
          Members=columnifexists('Members_s', ""),
          Settings=iif(Operation_s contains "Setting", pack("Name", columnifexists('Name_s', ""), "Old Value", columnifexists('OldValue_s', ""), "New Value", columnifexists('NewValue_s', "")),""),
          Details=pack("Id", columnifexists('Id_g', ""),  "OrganizationId", columnifexists('OrganizationId_g', ""), "UserType", columnifexists('UserType_d', ""), "UserKey", columnifexists('UserKey_g', ""), "TeamGuid", columnifexists('TeamGuid_s', "")) 
```
 Save the parser as a KQL function, with an alias of TeamsData. It will be used for the queries to follow. Details on configuring and using a KQL function as a parser can be found in this [Tech Community article](https://techcommunity.microsoft.com/t5/azure-sentinel/using-kql-functions-to-speed-up-analysis-in-azure-sentinel/ba-p/712381).

## Helpful hunting KQL queries

Use these queries to familiarize yourself with your Teams data and Teams environment. Knowing how the environment should look and behave is a good first step in recognizing suspicious activity. From there, you can branch out into threat hunting.

#### Federated external users query

Get the list of Teams sites that have federated external users. These users will have a domain name / UPN suffix that *isn't* owned by your organization. In this example query, the organization owns contoso.com.

```kusto
TeamsData
| where TimeGenerated > ago(7d)
| where Operation =~ "MemberAdded"
| extend UPN = tostring(parse_json(Members)[0].Upn)
| where UPN !endswith "contoso.com"
| where parse_json(Members)[0].Role == 3
| project TeamName, Operation, UserId, Members, UPN
```

> [!TIP]
> To learn more about External and Guest access types in Teams see [this article](./communicate-with-users-from-other-organizations.md), or the *Participant Types* section in the [Teams Security Guide](./teams-security-guide.md).

#### Who recently joined / Whose role changed

Query a specific user to check if they were added to a Teams channel in the last 7 days, or within a week:

```kusto
TeamsData
| where TimeGenerated > ago(7d)
| where Operation =~ "MemberAdded"
| where Members contains "UserName"
```

Was a user's role changed for a Team in the last 7 days:

```kusto
TeamsData
| where TimeGenerated > ago(7d)
| where Operation =~ "MemberRoleChanged"
| where Members contains "Role" and Members contains "1"
```

#### External users from unknown or new organizations

In Teams, you can add external users to your environment or channels. Organizations often have a limited number of key partnerships and add users from among these partners. This KQL looks at external users added to teams who come from organizations that haven't been seen or added before.

```kusto
// If you have more than 14 days worth of Teams data change this value 
let data_date = 14d; 
// If you want to look at users further back than the last day change this value 
let lookback_data = 1d; 
let known_orgs = ( 
TeamsData  
| where TimeGenerated > ago(data_date) 
| where Operation =~ "MemberAdded" or Operation =~ "TeamsSessionStarted" 
// Extract the correct UPN and parse our external organization domain 
| extend UPN = iif(Operation == "MemberAdded", tostring(parse_json(Members)[0].UPN), UserId) 
| extend Organization = tostring(split(split(UPN, "_")[1], "#")[0]) 
| where isnotempty(Organization) 
| summarize by Organization); 
TeamsData  
| where TimeGenerated > ago(lookback_data) 
| where Operation =~ "MemberAdded" 
| extend UPN = tostring(parse_json(Members)[0].UPN) 
| extend Organization = tostring(split(split(UPN, "_")[1], "#")[0]) 
| where isnotempty(Organization) 
| where Organization !in (known_orgs) 
// Uncomment the following line to map query entities is you plan to use this as a detection query 
//| extend timestamp = TimeGenerated, AccountCustomEntity = UPN 
```

#### External users who were added and then removed

Attackers with some level of existing access may add a new external account to Teams to access and exfiltrate data. They may also quickly remove that user to hide that they made access. This query hunts for external accounts that are added to Teams and swiftly removed to help identify suspicious behavior.

```kusto
// If you want to look at user added further than 7 days ago adjust this value 
let time_ago = 7d; 
// If you want to change the timeframe of how quickly accounts need to be added and removed change this value 
let time_delta = 1h; 
TeamsData  
| where TimeGenerated > ago(time_ago) 
| where Operation =~ "MemberAdded" 
| extend UPN = tostring(parse_json(Members)[0].UPN) 
| project TimeAdded=TimeGenerated, Operation, UPN, UserWhoAdded = UserId, TeamName, TeamGuid = tostring(Details.TeamGuid) 
| join ( 
TeamsData  
| where TimeGenerated > ago(time_ago) 
| where Operation =~ "MemberRemoved" 
| extend UPN = tostring(parse_json(Members)[0].UPN) 
| project TimeDeleted=TimeGenerated, Operation, UPN, UserWhoDeleted = UserId, TeamName, TeamGuid = tostring(Details.TeamGuid)) on UPN, TeamGuid 
| where TimeDeleted < (TimeAdded + time_delta) 
| project TimeAdded, TimeDeleted, UPN, UserWhoAdded, UserWhoDeleted, TeamName, TeamGuid 
// Uncomment the following line to map query entities is you plan to use this as a detection query 
//| extend timestamp = TimeAdded, AccountCustomEntity = UPN 
```

#### New bot or application added

Teams has the ability to include apps or bots in a Team to extend the feature set. This includes custom apps and bots. In some cases, an app or bot could be used to establish persistence in Teams without needing a user account, as well as access files and other data. This query hunts for apps or bots that are new to Teams.

```kusto
// If you have more than 14 days worth of Teams data change this value 
let data_date = 14d; 
let historical_bots = ( 
TeamsData 
| where TimeGenerated > ago(data_date) 
| where isnotempty(AddOnName) 
| project AddOnName); 
TeamsData 
| where TimeGenerated > ago(1d) 
// Look for add-ins we have never seen before 
| where AddOnName in (historical_bots) 
// Uncomment the following line to map query entities is you plan to use this as a detection query 
//| extend timestamp = TimeGenerated, AccountCustomEntity = UserId 
```

#### User accounts who are Owners of large numbers of Teams

Attackers looking to elevate their privileges may assign themselves Owner privileges of a large number of diverse teams, when, usually, users create and own a small number of teams around specific topics. This KQL query looks for suspicious behavior.

```kusto
// Adjust this value to change how many teams a user is made owner of before detecting 
let max_owner_count = 3; 
// Change this value to adjust how larger timeframe the query is run over. 
let time_window = 1d; 
let high_owner_count = (TeamsData 
| where TimeGenerated > ago(time_window) 
| where Operation =~ "MemberRoleChanged" 
| extend Member = tostring(parse_json(Members)[0].UPN)  
| extend NewRole = toint(parse_json(Members)[0].Role)  
| where NewRole == 2 
| summarize dcount(TeamName) by Member 
| where dcount_TeamName > max_owner_count 
| project Member); 
TeamsData 
| where TimeGenerated > ago(time_window) 
| where Operation =~ "MemberRoleChanged" 
| extend Member = tostring(parse_json(Members)[0].UPN)  
| extend NewRole = toint(parse_json(Members)[0].Role)  
| where NewRole == 2 
| where Member in (high_owner_count) 
| extend TeamGuid = tostring(Details.TeamGuid) 
// Uncomment the following line to map query entities is you plan to use this as a detection query 
//| extend timestamp = TimeGenerated, AccountCustomEntity = Member 
```

#### Many Team deletions by a single user

Attackers can cause disruptions and jeopardize projects and data by deleting multiple teams. Because teams are generally deleted by individual Owners, a central deletion of many teams can be a sign of trouble. This KQL looks for single users who delete multiple teams.

```kusto
 // Adjust this value to change how many Teams should be deleted before including
 let max_delete = 3;
 // Adjust this value to change the timewindow the query runs over
 let time_window = 1d;
 let deleting_users = (
 TeamsData 
 | where TimeGenerated > ago(time_window)
 | where Operation =~ "TeamDeleted"
 | summarize count() by UserId
 | where count_ > max_delete
 | project UserId);
 TeamsData
 | where TimeGenerated > ago(time_window)
 | where Operation =~ "TeamDeleted"
 | where UserId in (deleting_users)
 | extend TeamGuid = tostring(Details.TeamGuid)
 | project-away AddOnName, Members, Settings
 // Uncomment the following line to map query entities is you plan to use this as a detection query
 //| extend timestamp = TimeGenerated, AccountCustomEntity = UserId
```

#### Expanding your thread hunting opportunities

You can expand your hunting by combining queries from resources like Azure Active Directory (Azure AD), or other Office 365 workloads with your Teams queries. One example is combining detection of suspicious patterns in Azure AD SigninLogs, and using that information while hunting for Team Owners.

```kusto
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
TeamsData
| where TimeGenerated > ago(time_window)
| where Operation =~ "MemberRoleChanged"
| extend Member = tostring(parse_json(Members)[0].UPN) 
| extend NewRole = toint(parse_json(Members)[0].Role) 
| where NewRole == 2
| where Member in (failed_signins)
| extend TeamGuid = tostring(Details.TeamGuid)
```

Also, you can make the SigninLogs detections specific to Teams by adding a filter for only Teams-based sign-ins by using:

```kusto
| where AppDisplayName startswith "Microsoft Teams"
```

To help explain using `where AppDisplayName starts with "Microsoft Teams"` further, the KQL below demonstrates a successful logon from one IP address with failure from a different IP address, but scoped only to Teams sign-ins:

```kusto
let timeFrame = 1d;
let logonDiff = 10m;
SigninLogs 
  | where TimeGenerated >= ago(timeFrame) 
  | where ResultType == "0" 
  | where AppDisplayName startswith "Microsoft Teams"
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

[Turn audit log search on or off](/microsoft-365/compliance/turn-audit-log-search-on-or-off?view=o365-worldwide&viewFallbackFrom=o365-worldwide%c2%a0)

[What is Azure Sentinel](/azure/sentinel/overview)
