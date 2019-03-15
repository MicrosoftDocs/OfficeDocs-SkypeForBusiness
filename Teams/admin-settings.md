---
title: Admin settings for apps in Microsoft Teams
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 03/12/2018
ms.topic: article
ms.service: msteams
search.appverid: MET150
ms.reviewer: ritikag 
description: "Learn to allow and enable apps in Microsoft Teams including side-loading of external apps."
localization_priority: Normal
ms.custom:
- NewAdminCenter_Update
f1keywords: ms.teamsadmincenter.apppolicies.adminsettings
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
appliesto: 
- Microsoft Teams
---

Admin settings for apps in Microsoft Teams
==========================================
> [!IMPORTANT]
> [!INCLUDE [new-teams-sfb-admin-center-notice](includes/new-teams-sfb-admin-center-notice.md)]

Apps provide out-of-the-box tools for your organization to get more out of Teams. These apps combine the functionality of tabs, messaging extensions, connectors, and bots provided by Microsoft, built by a third-party, or by developers in your organization.

You manage apps for your organization in **Teams apps** in the Microsoft Teams admin center. You can set policies to control what apps are available to Teams users in your organization, customize Teams by pinning apps that are most important for your users, and specify whether users can upload custom apps (also known as sideloading). These policies and settings give you granular control over what apps are available, how they appear in Teams, and who can use them based on the needs of your organization.

## App permissions policies

With app permission policies, you can block or allow apps, either org-wide or for specific users. Blocked apps will not appear in the end user experience and all interactions with those apps are disabled.

### Example scenarios using app permission policies:
* Disabling app that pose a permission or data loss risk to the organization.
* Gradually rolling out new 3rd-party or custom built apps to specific end users.
* Simplfying the end user experience, especially when initially rolling out Teams.

To learn more, go to [Manage app permission policies in Microsoft Teams](teams-app-permission-policies.md)

## App setup policies

App setup policies let you customize the app experience for your users. You choose the apps that you want to pin to the app bar in the Teams clients and the order in which they appear, on web, desktop, and mobile clients.

### Example scenarios using app permission policies:
* Driving awareness and adoption of core apps. For example, you can prepin a custom recruiting and talent management app for users in your HR organization.
* Selectively pinning core Teams features, such as chat, teams, and calling. Doing so can help ensure users are engaged in specific activities within Teams.

To learn more, go to [Manage app setup policies in Microsoft Teams](teams-app-setup-policies.md)

## Custom app policies and settings

Teams allows developers within your organization to build, test, and deploy custom apps to other users in the tenant. Custom apps can be added to Teams by uploading an app package in a .zip file directly to a team. You can use the App setup policies to control who in your organization can upload custom apps. You can also control org-wide settings over whether or not users can interact with specific custom  apps.

To learn more, go to [Manage custom app policies and settings in Microsoft Teams](teams-custom-app-policies-and-settings.md)

-----------
OLD CONTENT
## Allow external apps in Teams

By default, **Allow external apps in Microsoft Teams** is turned on, with all apps selected. If you turn off this setting, all external third-party apps are disabled. 

## Enable external apps by default

#### :trophy: Best practice: Manage external apps individually 
 
To turn on some apps (and turn off others), turn off **Allow sideloading of external apps**. Then turn off any apps you don't want your users to use. Optional: Turn off **Enable new external apps by default** (if you want to control new apps). 

> [!NOTE]
> Default apps, such as those built by Microsoft, are not affected by the **Enable new external apps by default** setting. New apps are enabled by default when released by Microsoft.

When this setting is turned on, users can activate new apps as soon as they're added to the Teams app catalog. To open the Teams app catalog, click **Store** at the bottom of Teams, then click **Apps**. If you want to control which apps are available, turn off this setting. Of course, if you turn it off, you have to remember to review new apps periodically so your organization doesn't miss out on cool new apps. 

Sideloading is how you add an app to Teams by uploading a zip file directly to a team. Sideloading lets you test an app as it's being developed. It also lets you build an app for internal use only and share it with your team without submitting it to the Teams app catalog in the Office Store. 

Only team owners, or members who are granted permissions, can sideload apps into Teams.  

## Create and upload custom apps 

To learn more about apps, see [Develop apps for Teams](https://docs.microsoft.com/microsoftteams/platform/concepts/apps/apps-overview). 
