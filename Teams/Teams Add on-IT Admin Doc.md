---
title: Install and integrate Google Workspace calendar add-ons in Teams
author: cichur
ms.author: v-cichur
ms.reviewer: aravin
manager: serdars
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn how to install and integrate Google Workspace calendar add-ons in Microsoft Teams
localization_priority: Normal
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---


# Enable or disable Google Workspace Marketplace Teams app

Using the Google Workspace Marketplace Teams app lets Google calendar users schedule and join a Microsoft Teams meeting directly from Google Workspace. Users will get access to Teams meetings features including video and audio conferencing, screen sharing, meeting chat, digital whiteboards, and more. Stay connected and organized to get more done together across work, school, and life.

The Google Workspace Marketplace Teams app needs to be enabled by a Teams admin before tenant users can access the app.

## Enable Google Workspace in the AAD Portal

As a tenant administrator, you can enable or disable a Google Workspace Marketplace Teams app from your organization's admin account using the AAD portal.

1. Sign in to the Azure portal.

2. Select **Manage** > **All applications**.

3. Search for **Microsoft Teams Gsuite Addon** or **Microsoft Teams Google Workspace Addon**.

4. Select **Enable**.

 > [!Note]
 > If you want to disable the GSuite Addon or the Microsoft Teams Google Workspace Addon, select **Disable** instead of **Enable** in Step 4.

 ![Azure portal with addons selected](media/aad-portal-addon.png)

 ![Azure portal with gsuite addons selected](media/aad-portal-google-addon.png)

## Disable Google Workspace Marketplace Teams app using PowerShell

The basic PowerShell command is`Remove-AzAdServicePrincipal -DisplayName ServicePrincipalName`.

See [Create an Azure service principal with Azure PowerShell](https://docs.microsoft.com/powershell/azure/create-azure-service-principal-azureps?view=azps-5.0.0) for more information.

## Delete a Google Workspace Marketplace app

See the [Google documentation Delete a Google Workspace Marketplace app](https://support.google.com/a/answer/6216211?hl=en) for instructions.
