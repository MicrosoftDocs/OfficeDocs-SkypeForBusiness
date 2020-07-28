---
title: Manage your apps in the Microsoft Teams admin center
author: LanaChin
ms.author: v-lanac
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
ms.reviewer: ritikag
search.appverid: MET150
f1keywords: 
- ms.teamsadmincenter.manageapps.overview
description: Learn how to manage your Teams apps on the Manage apps page of the Microsoft Teams admin center
appliesto: 
- Microsoft Teams
localization_priority: Normal
---
Manage your apps in the Microsoft Teams admin center
======================================================

As an admin, the **Manage apps** page in the Microsoft Teams admin center is where you view and manage all Teams apps for your organization. Here, you can see the org-level status and properties of apps, approve or upload new custom apps to your organization's app store, block or allow apps at the org level, and manage org-wide app settings.

The **Manage apps** page gives you a view into all available apps in your organization's app store, providing you with the information you need to decide which apps to allow or block across your organization. You can then use [app permission policies](teams-app-permission-policies.md), [app setup policies](teams-app-setup-policies.md), and [custom app policies and settings](teams-custom-app-policies-and-settings.md) to configure the app experience for specific users in your organization.

In the left navigation of the Microsoft Teams admin center, go to **Teams apps** > **Manage apps**. You must be a global admin or Teams service admin to access the page.

> [!NOTE]
> The **Manage apps** page isn't available yet in Microsoft 365 Government Community Cloud (GCC) deployments of Teams.

## View apps

You can view every app in your organization's app store including the following information about each app.

![Screenshot of the Managed apps page](media/manage-apps.png)

- **Name**: The app name. Click the app name to see more information about the app. This includes a description of the app, whether it's allowed or blocked, version, categories that apply to the app, certification status, supported capabilities, and app ID. Here's an example:

  ![Screenshot of the apps details page for an app](media/manage-apps-app-details.png)
  
- **Certification**: If the app has gone through certification, you'll see either **Microsoft 365 certified** or **Publisher attestation**. Click the link to view certification details for the app. If you see "**--**", we don't have certification information for the app. To learn more about certified apps in Teams, read [Microsoft 365 App Certification program](https://docs.microsoft.com/teams-app-certification/all-apps).  

- **Categories**: Categories that apply to the app.

- **App status**: Status of the app at the org level, which can be one of the following:

    - **Allowed**: The app is available for all users in your organization.
    
    - **Blocked**: The app is blocked and not available for any users in your organization.
    
    - **Blocked org-wide**: The app is blocked in org-wide app settings.
    
      It's important to know that this column represents the allowed and blocked status of apps that were formerly on the **Org-wide settings** pane. You now view, block, and allow apps at the org-wide on the **Manage apps** page. 

- **Version**: App version.

To see the information that you want in the table, click **Edit Column** in the upper-right corner to add or remove columns to the table.

## Publish a custom app to your organization's app store

### Approve a new custom app

You can use your app catalog to test and distribute custom applications that are built specifically for your organization. 
A Teams app package is created by using [Teams App Studio](https://docs.microsoft.com/microsoftteams/platform/get-started/get-started-app-studio). When you have the app package, you can add it to your app catalog. While all users in your organization can view the app catalog, only global admins and Teams service admins can publish and manage it.

You can get the app package in the following ways:

- The developer can submit the app to the tenant app catalog directly through their IDE or using the Apps Submission API. The app will be listed in the table with an **App publishing status** of **Submitted** and an **App status** of **Blocked**. You can then review and publish the app directly from the app details page.
- The developer can send you the app package in .zip format. To upload the app to your tenant app catalog, click **Upload new app** to upload the app package. The app isn't highlighted after it's uploaded so you'll need to search your app catalog to find it.

To update an app after it's published or uploaded, in the list of apps on the **Manage apps** page, click the app name, and then click **Update**. Doing this replaces the existing app in your app catalog and all app permission policies and app setup policies remain enforced for the updated app.

To learn more, see [Use the Teams App Submission API to submit and approve your custom apps](submit-approve-custom-apps.md).

### Upload a new custom app

You can test and distribute custom apps that are built specifically for your organization on the Manage apps page. The developer creates a Teams app package using [Teams App Studio](https://docs.microsoft.com/microsoftteams/platform/get-started/get-started-app-studio), and then sends it to you in .zip format. When you have the app package, you can upload it to your organization's app store. While all users in your organization can view your organization's app store, only global admins and Teams service admins can upload apps to it and manage it.

To upload a new custom app to your organization's app store, select **Upload** to upload the app package. The app isn't highlighted after it's uploaded so you'll need to search the list of apps on the Manage apps page to find it.

You can get the app package in the following ways:

- The developer can submit the app to the tenant app catalog directly through their IDE or using the Apps Submission API. The app will be listed in the table with an **App publishing status** of **Submitted** and an **App status** of **Blocked**. You can then review and publish the app directly from the app details page.
- The developer can send you the app package in .zip format. To upload the app to your tenant app catalog, click **Upload new app** to upload the app package. The app isn't highlighted after it's uploaded so you'll need to search your app catalog to find it.

To update an app after it's published or uploaded, in the list of apps on the **Manage apps** page, click the app name, and then click **Update**. Doing this replaces the existing app in your app catalog and all app permission policies and app setup policies remain enforced for the updated app.

To learn more, see [Upload your custom apps in the Microsoft Teams admin center](upload-custom-apps.md).


## Allow and block apps

The **Manage apps** page is where you allow or block individual apps at the org level. It shows every available app and its current org-level app status. (Blocking and allowing apps at the org level has moved from the **Org-wide app settings** pane to here.)

To allow or block an app, select it, and then click **Allow** or **Block**. When you block an app, all interactions with that app are disabled and the app doesn't appear in Teams for any users in your organization.

When you block or allow an app on the **Manage apps** page, that app is blocked or allowed for all users in your organization.  When you block or allow an app in a Teams app permission policy, it's blocked or allowed for users who are assigned that policy. For a user to be able to install and interact with any app, you must allow the app at the org level on the **Manage apps** page and in the app permission policy that's assigned to the user.

 > [!NOTE]
 > To uninstall an app, right-click on the app and then click **Uninstall** or use the **More apps** menu on the lefthand side. 

## Manage org-wide app settings

Use org-wide app settings to control whether users can install third-party apps and whether users can upload or interact with custom  apps in your organization. Org-wide app settings govern the behavior for all users and override any other app permission policies assigned to users. You can use them to control malicious or problematic apps.

> [!NOTE]
> To learn how to use org-wide app settings in Microsoft 365 Government - GCC deployments of Teams, see [Manage app permission policies in Teams](teams-app-permission-policies.md).

1. On the **Manage apps** page, select **Org-wide app settings**. You can then configure the settings you want in the panel.

    ![Screenshot of org-wide app settings](media/manage-apps-org-wide-app-settings.png)
    
2. Under **Third-party apps**, turn off or turn on these settings to control access to third-party apps:

    - **Allow third-party apps**: This controls whether users can use third-party apps. If you turn off this setting, your users won't be able to install or use any third-party apps and the app status of these apps is displayed as **Blocked org-wide** in the table.

        > [!NOTE]
        > When **Allow third-party apps** is off, [outgoing webhooks](https://docs.microsoft.com/microsoftteams/platform/webhooks-and-connectors/what-are-webhooks-and-connectors) are disabled, which means that users can't create them. When this setting is on, outgoing webhooks are enabled for all users and you can control them at the user level by allowing or blocking the Outgoing Webhook app through [app permission policies](teams-app-permission-policies.md). <br><br>Note that if you have existing [app permission policies](teams-app-permission-policies.md) for **Microsoft apps** that use the **Allow specific apps and block all others** setting, and you want to enable outgoing webhooks for users, add the Outgoing Webhook app to the list.
    - **Allow any new third-party apps published to the store by default**: This controls whether new third-party apps that are published to the Teams app store become automatically available in Teams. You can only set this option if you allow third-party apps.

3. Under **Custom apps**, turn off or turn on **Allow interaction with custom apps**. This setting controls whether users can interact with custom apps. To learn more, see [Manage custom app policies and settings in Teams](teams-custom-app-policies-and-settings.md).
4. Click **Save** for org-wide app settings to take effect.

## Related topics

- [Admin settings for apps in Teams](admin-settings.md)
