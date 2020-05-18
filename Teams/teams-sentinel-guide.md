---
title: "Azure Sentinel and Microsoft Teams"
author: MicrosoftHeidi
ms.author: tracyp
manager: serdars
ms.topic: reference
ms.service: msteams
audience: admin
ms.reviewer:
description: Security advice and learnings for ITAdmins on using Sentinel to monitor and hunt threats that may arise in Teams.
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

Teams serves a central role in both communication and data sharing in the Microsoft 365 Cloud. Because the Teams service touches on so many underlying technologies in the Cloud, it can benefit from human and automated analysis not only when it comes to *hunting in logs*, but also in *real-time monitoring of meetings*. Azure Sentinel offers admins these solutions.

> [!NOTE]
> Need a refresher on Azure Sentinel? [This article](https://docs.microsoft.com/azure/sentinel/overview) is just the thing.

## Sentinel and Microsoft Teams Activity Logs

This article focuses on collecting Teams activity logs in Azure Sentinel. Aside from allowing administrators to put security management under one pane of glass (including any selected 3rd party devices, Microsoft Threat Protection, and other Microsoft 365 Workloads), Sentinel workbooks, and runbooks can make security monitoring systematic. A good first step in this process is collecting the needed logs for analysis.

> [!NOTE]
> More than one Microsoft 365 subscription can be surfaced in the same instance of Azure Sentinel. This will allow for [realtime monitoring](https://docs.microsoft.com/azure/sentinel/livestream) and hunting for threats in historical log file s. Administrators will be able to hunt using [cross-resource queries](https://docs.microsoft.com/azure/azure-monitor/log-query/cross-workspace-query), that is within a single resource group, across resource groups, or in another subscription.

## Step 1: Collect Teams logs

This section has three parts:

1. Enabling Audit Logs in **Microsoft 365** (M365).
2. Registering an App in **Microsoft Azure** to permit authentication and authorization for log collection.
3. Registering the API subscription that will allow log collection via M365 API via **PowerShell**.

### Enable Audit logs in M365

Because Teams logs activity through M365, audit logs aren't collected by default. Turn on this feature via [these steps](https://docs.microsoft.com/microsoft-365/compliance/turn-audit-log-search-on-or-off?view=o365-worldwide&viewFallbackFrom=o365-worldwide%C2%A0). Teams data is collected in the M365 audit under *Audit.General*.

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

The final step in setup is to collect and register the API subscription so that you can collect your log data. This is done via PowerShell REST calls to the M365 Management Activity API.

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
  •	Inside the Until loop, the first HTTP step Connects to the AvailableURI. This URI returns a list of available content and each contents URI. There's more on how this works [here](https://docs.microsoft.com/en-us/office/office-365-management-api/office-365-management-activity-api-reference#list-available-content).
  <p>
  •	Next a check is run to make sure data is returned. The Condition checks if the length of the body is 0. If so there is no data to write to Log Analytics. If the value is greater than 0, there is data to process.
  <p>
  •	If data is detected, it must next be processed. Parse JSON defines a schema of the returned data. This allows logic apps to use the parsed data as Dynamic content in later steps.
  <p>
  •	Since the returned list of available data is an Array, a For Each action is used to loop through the list of available content.
  <p>
  •	Next is grabbing the content.  HTTP is used again to get the contentUri (a dynamic property created from Parse JSON), which is the URL of the data to retrieve.
  <p>
  •	Parse JSON is also used to parse the returned data. You can find some sample content [here](https://docs.microsoft.com/en-us/office/office-365-management-api/office-365-management-activity-api-reference#list-available-content).
  <p>
  •	The data returned is also an array. A For Each loop can be used here as well. In this loop, the workflow takes the current item of data and uses the Send Data action to write the data to Log Analytics.
  <p>
  • Since there may be multiple pages of available content, a condition checks if the NextPageUri is not NULL. If it is NULL, or empty, NextPage is set to 0, which ends the Until loop. If it contains a URL, the AvaibleUri variable is updated to that URL. This way, the next run of the Until loop uses a next available URL, and not the starting URL.

  </details>

> [!TIP]
> You may choose to use an *Azure Function* to ingest those logs, instead, and if you do, the information on how to deploy is [here](https://github.com/Azure/Azure-Sentinel/tree/master/DataConnectors/O365%20Data), or [here](https://github.com/Azure/Azure-Sentinel/tree/master/DataConnectors/O365%20DataCSharp), depending on your preference.

With the connector (whichever of the options above you chose) running, you should see a custom table called O365API_CL in the Azure Sentinel workspace. This will house your Teams logs.

## Step 3: Use Sentinel to monitor Microsoft Teams

Identity is an important attack vector to monitor when it comes to Microsoft Teams. Because Azure Active Directory (Azure AD) is the underpinning of Microsoft 365's directory, including Teams, collecting and hunting for threats in Azure AD logs around authentication will be useful in capturing suspicious behaviour around identity. You can use the built-in connector to pull Azure AD data into Azure Sentinel, and use these [detection](https://github.com/Azure/Azure-Sentinel/tree/master/Detections/SigninLogs) and [hunting](https://github.com/Azure/Azure-Sentinel/tree/master/Hunting%20Queries/SigninLogs) queries to look for problems.

Regarding attacks specific to Microsoft Teams, threats to data, for example, Azure Sentinel also has means to monitor for them and hunt them down.

## Create a parser for your data

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

## Helfpul hunting KQL queries

Use these queries to familiarize yourself with your Teams data and Teams environment. Knowing how the environment should look and behave is a good first step in recognizing suspicious activity. From there, you can branch out into threat hunting.

### Federated external users query

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
> To learn more about External and Guest access types in Teams see [this article](https://docs.microsoft.com/en-us/microsoftteams/communicate-with-users-from-other-organizations), or the *Participant Types* section in the [Teams Security Guide](https://docs.microsoft.com/en-us/microsoftteams/teams-security-guide).



<!--*Thank you for content collaboration, Pete Bryan, Nicholas DiCola, and Matthew Lowe.*-->

## More information

[Registering your application in Azure AD](https://docs.microsoft.com/skype-sdk/ucwa/registeringyourapplicationinazuread%C2%A0%20%20%C2%A0)

[Turn audit log search on or off](https://docs.microsoft.com/microsoft-365/compliance/turn-audit-log-search-on-or-off?view=o365-worldwide&viewFallbackFrom=o365-worldwide%C2%A0)

[What is Azure Sentinel](https://docs.microsoft.com/en-us/azure/sentinel/overview)