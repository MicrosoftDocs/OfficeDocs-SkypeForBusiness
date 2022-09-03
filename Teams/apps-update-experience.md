---
title: Apps update experience in Microsoft Teams
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
  - M365-collaboration
f1.keywords: 
  - NOCSH
appliesto: 
- Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: In this article, learn how Microsoft apps, custom apps, and third-party apps in Microsoft Teams are updated and how admins facilitate it.
---

# Teams app updates and admin role

Teams admins can help their end-users get the latest version of the apps. To do so they have the following the following roles:

* [Updates to third-party apps](#updates-to-third-party-apps) that are available in Teams store when a new version is provided by the app developer or vendor.
* [Updates to custom apps](#updates-to-custom-apps) that are available only in your organization when your developer submits a new version.

## Updates to third-party apps

For users to install and use an app, they must give permissions to the app to access the required services and information. In most cases, after a new version of an app is available in the Teams Store, the installed app is automatically updated for all users. However, a few specific changes in the new version of the app require a user permission again. This repeat user acceptance ensures awareness about the changes such as functionality or access to personal information. Teams admins can [provide permissions to an app on behalf of the users](app-permissions-admin-center.md).

If app developers make one or more the following changes to their apps, then the end-users must approve the update of app.

* Add or remove a bot. Change the ID of the bot using the `botId` property.
* Change the `isNotificationOnly` property of an existing bot, that may change the bot's notifications.
* Change `SupportsCalling`, `SupportsVideo`, and `SupportsFiles` properties of an existing bot to add capability to call, play video, and upload or download files.
* Permissions inside Authorization are added or changed.
* Add or remove a messaging extension, add a group tab, add a connector, or add a channel.
* Change parameters in the [`webApplicationInfo`](/microsoftteams/platform/resources/schema/manifest-schema#webapplicationinfo) in the manifest file.

<!--- image update
:::image type="content" source="media/manage-your-custom-apps-update1.png" alt-text="New version available." lightbox="media/manage-your-custom-apps-update1.png":::

:::image type="content" source="media/manage-your-custom-apps-update2.png" alt-text="Upgrade option for an app." lightbox="media/manage-your-custom-apps-update2.png":::
--->

## Updates to custom apps

Custom apps that are created and deployed within your organization are available to the users on your tenant or organization. Teams admin update the custom apps to new versions as provided by developers within the organization. For more information, see [how admins manage custom apps](custom-app-overview.md).

## Related article

* [Understand manifest schema for updates done in apps](/microsoftteams/platform/resources/schema/manifest-schema).
* [Know about custom app management](custom-app-overview.md).
