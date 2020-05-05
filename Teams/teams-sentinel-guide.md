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






<!--*Thank you for content collaboration, Pete Bryan, Nicholas DiCola, and Matthew Lowe.*-->

## More information

[Registering your application in Azure AD](https://docs.microsoft.com/skype-sdk/ucwa/registeringyourapplicationinazuread%C2%A0%20%20%C2%A0)

[Turn audit log search on or off](https://docs.microsoft.com/microsoft-365/compliance/turn-audit-log-search-on-or-off?view=o365-worldwide&viewFallbackFrom=o365-worldwide%C2%A0)

[What is Azure Sentinel](https://docs.microsoft.com/en-us/azure/sentinel/overview)