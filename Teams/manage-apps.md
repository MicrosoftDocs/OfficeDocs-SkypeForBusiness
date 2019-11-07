---
title: Manage apps in the Microsoft Teams admin center
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
ms.reviewer: rowille
search.appverid: MET150
f1keywords: 
- ms.teamsadmincenter.manageapps.overview
description: Manage your Microsoft Teams apps in the Teams admin center.
appliesto: 
- Microsoft Teams
localization_priority: Normal
---
Manage apps in the Microsoft Teams admin center
======================================================

As an admin, the **Manage apps** page in the Microsoft Teams admin center is where you view and manage all Teams apps in your organization's app catalog. Here, you can see the org-level status and and properties of apps, upload new custom apps to your tenant app catalog, block or allow apps org-wide, and manage org-wide app settings.

The **Manage apps** page gives you a view into all available apps in your tenant catalog, providing you with the information you need to decide which apps to allow or block across your organization. You can then use [app permission policies](teams-app-permission-policies.md), [app setup policies](teams-app-setup-policies.md), and [custom app policies and settings](teams-custom-app-policies-and-settings.md) to configure the app experience for specific users in your organization.

In the left navigation of the Microsoft Teams admin center, go to **Teams apps** > **Manage apps**. You must be a global admin or teams service admin to access the page.

## View apps in your tenant app catalog

The **Manage apps** page lists every app in your tenant app catalog and includes the following information about each app:

- **Name**: The app name. Click the app name to see more information about the app.    
- **Certification**: If the app has gone through certification, you'll see either **Microsoft 365 certified** or **Publisher attestation**. Click the link to view certification details for the app. If you see "**--**", we don't have certification information for the app. To learn more about certified apps in Teams, read [Microsoft Teams App Security and Compliance](https://docs.microsoft.com/teams-app-certification/all-apps).  
- **Categories**: The categories that apply to the app.
- **App status**: The status of the app at the organizational level, which can be one of the following:
    - **Allowed**: The app is available for users in your organization.
    - **Blocked**: The app is blocked and not available for users in your organization.
    - **Allowed but org-wide disabled**: The app is allowed but disabled in org-wide app settings.
- **Version**: The app version.

To see the information that you want in the table, click **Edit Column** in the upper-right corner to add or remove columns to the table.

## Upload a new app

To upload a new custom app to your tenant app catalog, click **Upload new app** to upload your app manifest file in .zip format. If the .zip file isn't a valid Teams app manifest, the upload will fail.

> ??? **DO WE NEED TO ADD STEPS HERE?**

You can still [upload apps by using the Teams client](https://support.office.com/article/add-an-app-to-teams-b2217706-f7ed-4e64-8e96-c413afd02f77). --> Use this URL instead? [Publish apps in the Microsoft Teams Tenant Apps Catalog](https://docs.microsoft.com/en-us/MicrosoftTeams/tenant-apps-catalog-teams).

## Allow and block apps

The **Manage apps** page is where you allow or block individual apps at the org-wide level. Previously, you did this by adding apps to the blocked list on the app permission policy page. With the **Manage apps** page, you see every available app and its current org-wide app status.

To allow or block an app, select it, and then click **Allow** or **Block**. When you block an app, all interactions with that app are disabled and the app doesn't appear in Teams for users.

## Manage org-wide app settings

Use org-wide app settings to control whether users can install third-party apps and whether users can upload or interact with custom (sideloaded) apps in your organization. Org-wide app settings govern the behavior for all users and override any other app permission policies assigned to users. You can use them to control malicious or problematic apps.

1. In the left navigation of the Microsoft Teams admin center, go to **Teams apps** > **Manage apps**.
2. Select **Org-wide settings**. You can then configure the settings you want in the panel. 
    ![Screenshot of org-wide app settings](media/app-permission-policies-org-wide-settings.png)
3. Under **Third-party apps**, turn off or turn on these settings to control access to third-party apps:

    - **Allow third-party apps in Teams**: This controls whether users can use third-party apps. If you turn off this setting, your users won't be able to install or use any third-party apps. For apps that you allowed, the status shows as **Allowed but disabled org-wide**.
    - **Allow any new third-party apps published to the store by default**: This controls whether new third-party apps that are published to the Teams app store become automatically available in Teams. You can only set this option if you allow third-party apps.

4. Under **Custom apps**, turn off or turn on **Allow interaction with custom apps**. This setting controls whether users can interact with custom (sideloaded) apps. Keep in mind that this is different from allowing users to *upload* custom apps. ??? **Is this accurate?**
5. Click **Save** for org-wide app settings to take effect.

## Related topics

- [Admin settings for apps in Teams](admin-settings.md)
- [Manage your line-of-business apps in Teams](manage-your-lob-apps.md)