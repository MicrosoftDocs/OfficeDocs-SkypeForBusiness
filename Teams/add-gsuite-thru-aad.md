---
title: Install and integrate the Google Workspace Marketplace add-on in Teams
author: cichur
ms.author: v-cichur
ms.reviewer: aravin
manager: serdars
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn how to install and integrate the Google Workspace Marketplace add-on in Microsoft Teams
localization_priority: Normal
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

# Set up Google Workspace Marketplace Teams app

Using the Google Workspace Marketplace Teams app lets Google calendar users schedule and join a Microsoft Teams meeting directly from Google Workspace. Users will get access to Teams meetings features including video and audio conferencing, screen sharing, meeting chat, digital whiteboards, and more. Stay connected and organized to get more done together across work, school, and life.

The Google Workspace Marketplace Teams app must be enabled by a Teams admin before tenant users can access the app.

## Enable Google Workspace in the Azure Active Directory

As a tenant administrator, you can enable or disable a Google Workspace Marketplace Teams app from your organization's admin account using the Azure Active Directory (AAD) portal.

1. Sign in to the AAD portal.

2. Select **Enterprise applications** > **All applications**.

 ![Azure portal showing all applications](media/aad-add-google-workspace.png)

3. Search for **Microsoft Teams meeting add-on for Google Workspace**.

4. Select **Enable**.

 ![Azure portal showing the google workspace properties](media/google-workspace-properties.png)

5. (Optional) To disable the addon, select **Disable** instead of **Enable** in Step 4.

## Disable Google Workspace Marketplace Teams app using PowerShell

```powershell
Connect-AzureAD

$displayName = 'Microsoft Teams meeting add-on for Google Workspace'
$appId = '7969c887-ba98-48bb-8832-6c9239929d7c'

# Check if a service principal already exists for the app
$servicePrincipal = Get-AzureADServicePrincipal -Filter "appId eq '$appId'"
if ($servicePrincipal) {
    # Service principal exists already, disable it
    Set-AzureADServicePrincipal -ObjectId $servicePrincipal.ObjectId -AccountEnabled $false
    Write-Host "Disabled existing Service Principal \n"
} else {
    # Service principal does not yet exist, create it and disable it at the same time
    New-AzureADServicePrincipal -AppId $appId -DisplayName $displayName
    $servicePrincipal = New-AzureADServicePrincipal -AppId $appId -DisplayName $displayName -AccountEnabled $false
    Write-Host "Created and disabled the Service Principal \n"
}
```

For more information, see [Create an Azure service principal with Azure PowerShell](https://docs.microsoft.com/powershell/azure/create-azure-service-principal-azureps?view=azps-5.0.0).

## Delete a Google Workspace Marketplace app

See the Google documentation [Delete a Google Workspace Marketplace app](https://support.google.com/a/answer/6216211?hl=en) for instructions.
