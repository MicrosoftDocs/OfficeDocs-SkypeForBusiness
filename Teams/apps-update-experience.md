---
title: Apps update experience in Microsoft Teams
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.subservice: teams-apps
audience: Admin
ms.date: 04/14/2023
ms.collection: 
  - M365-collaboration
f1.keywords: 
  - NOCSH
appliesto: 
- Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn how Teams apps get updated to a newer version and how admins can consent to app updates.
---

# Role of an admin in upgrading Teams apps to new version

Teams app developers provide newer version of their apps to enhance the experience of the users. Depending on the organization settings, either Teams administrators or users or both can consent to the apps. When you or your users add an app to Teams for the first time, you or the users consent to the permissions. When the app updates, it only requires consent again, if the new version has more functionality or requests more information within your organization.

As a Teams administrator, you can update Teams apps to help the users get the latest version of apps by performing one of the following tasks:

* When a new app version is available in Teams store, allow users to update it.
* When your developer submits a new version of a custom app, [update or approve the submission](#custom-apps) and allow users to update it.

## Conditions when an app updates and requires consent

Apps update on their own if there's no change in functionality or request for organization's data. When one or more of the following changes are made to an app, it doesn't update on its own. Users can provide consent when they try to use the app for the first time.

* Add a bot. Change the ID of the bot using the `botId` property.
* Change the `isNotificationOnly` property of an existing bot that may change the bot's notifications.
* Change `SupportsCalling`, `SupportsVideo`, and `SupportsFiles` properties of an existing bot to add capability to call, play video, and upload or download files.
* Change parameters in the `webApplicationInfo` in the manifest file.
* Add or remove permissions in authorization.
* Add or remove a messaging extension, group tab, connector, or channel.

App developers can change the above values in the [app manifest file](/microsoftteams/platform/resources/schema/manifest-schema).

Teams simplifies the app update experience for its users by requiring their consent for new app versions only once. When a user consents, Teams updates the app in the chats, channels, and meetings where the user is added. Users don't need to update the app separately in each context.

> [!NOTE]
> When any of the above mentioned changes are done in a newer version of an app, then you can't consent on behalf of the users. Users must individually provide consent to update the app on their own. Azure AD admin must [allow users to consent](/azure/active-directory/manage-apps/configure-user-consent?pivots=portal).

## Contexts in which apps upgrade

A user can use an app in more than one context in Teams. When a user consents, the app is updated in their chats, channels, and meetings but only in the contexts where the previous version of the app was added. Users don't need to update the app separately in each context.

* Personal app context - When a user is using an app in their private workspace.

    :::image type="content" source="media/update-app-personal.png" alt-text="Screenshot that shows personal app context." lightbox="media/update-app-personal2.png":::

* Tab app context - When a user opens an app from a tab within a team, meeting, or group chat.

    :::image type="content" source="media/update-app-tab.png" alt-text="Screenshot that shows tab app context." lightbox="media/update-app-tab2.png":::

* Bot app context - When a bot app initiates update in a chat with users.

    :::image type="content" source="media/update-app-bot.png" alt-text="Screenshot that shows bot app context." lightbox="media/update-app-bot2.png":::

## Custom apps

Custom apps that are created and deployed within your organization are available to the users on your organization. Teams admin updates a custom app to its new version in one of the following ways:

* If developers send the app package to you, then upload it to your organization's app catalog in Teams.
* If developers submit the app via Teams, then review and approve the request for the app to be available in your organization's app catalog in Teams.

For more information, see [how admins manage custom apps](teams-custom-app-policies-and-settings.md).

For custom apps to update, after you upload the new version of the app to Teams, users must individually provide their consent if it's required.

## Considerations for app upgrades

* If an app's newer version doesn't require any new permissions, then it updates to the new version automatically.

* For updated apps, Teams administrators can't consent on behalf of the users. Users must individually provide their consent if it's required. Azure AD admin must [allow users to consent](/azure/active-directory/manage-apps/configure-user-consent?pivots=portal).

* A team owner can add an app in a team and view the update button when there's an available app update. It can be done  from the Manage Teams page in Teams admin center or the apps page in the Teams store.

* When an app is updated in a team, all team members can access the updated app. However, team members must still give their consent to use the same app in their other contexts.

* After updating in a context, the app automatically updates only in the contexts that the user is a member of and the previous version of the app was added. The app isn't updated in teams and groups that the user isn't a part of. The new version of the app isn't added to teams or groups where the app wasn't originally added.

## Related articles

* [Understand manifest schema for updates done in apps](/microsoftteams/platform/resources/schema/manifest-schema).
* [How Azure AD admin allows users to consent](/azure/active-directory/manage-apps/configure-user-consent?pivots=portal)
* [Know about custom app management](teams-custom-app-policies-and-settings.md).
