---
title: Microsoft Teams apps update experience and admin role
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.subservice: teams-apps
audience: Admin
ms.date: 07/31/2023
ms.collection: 
  - M365-collaboration
f1.keywords: 
  - NOCSH
appliesto: 
- Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn how third-party and custom apps get updated in Teams to a newer version and how admins can control the app updates.
---

# Role of an admin to upgrade Teams apps to a newer version

When an app is installed for the first time it may require consent of an admin depending on the permissions that the app needs. When a new version of an installed app is made available in the store, then one of the following scenario occurs:

* If there are changes in app permissions or [some selected functionality](#conditions-when-an-app-update-requires-consent), then the app update requires consent from the app user.
* If the updated version of the app doesn't require new permissions and doesn't have only basic functionality changes, then it updates automatically.

As a Teams administrator, you can update Teams apps to help the users get the latest version of apps by performing one of the following tasks:

* When a new app version is available in Teams store, allow users to upgrade to the new version.
* When your developer submits a new version of a custom app, [update or approve the submission](#admin-upload-of-updated-custom-apps) and allow users to upgrade to the new version.

## Conditions when an app update requires consent

Apps update on their own if there's no change in functionality or request for organization's data. When one or more of the following changes are made to an app, it doesn't update on its own. Users must provide consent when they use the app after the update is made available.

* Add a bot or change the ID of the bot using the `botId` property.
* Change the `isNotificationOnly` property of an existing bot that may change the bot's notifications.
* Change `SupportsCalling`, `SupportsVideo`, and `SupportsFiles` properties of an existing bot to add capability to call, play video, and upload or download files.
* Change parameters in the `webApplicationInfo` in the manifest file.
* Add or remove permissions in authorization.
* Add a messaging extension.

When creating the new version of an app, the developer can change the above values in the [app manifest file](/microsoftteams/platform/resources/schema/manifest-schema). Any of these changes lead to a change in app permissions. Hence, an update requires admin approval.

## Update to new version by users and admins

If an app update doesn't require consent, then it automatically updates. If consent is required, then Teams simplifies the app update experience by requiring user consent only once. When a user consents, Teams updates the app in the chats, channels, and meetings where the user is added. Users don't need to update the app separately in each context.

To update their app, users must individually provide their consent. Admins can't consent on behalf of the users but can update an app manually.

| Who can consent to app update | How to update | Conditions and scope of update |
|---|---|---|
| User | Select [Update on the consent prompt](#contexts-in-which-apps-upgrade). | [Azure AD admin must allow user consent](/azure/active-directory/manage-apps/configure-user-consent?pivots=portal). |
| Admin | Open a team in Teams client and update an app from the team's settings page. | Team and channel |
| Team owner | Open a team in Teams client and update an app from their team's settings page. | In the teams that they own. For other contexts, users still need to provide their consent. |

If none of above method is used to update, then an app is never updated. User can update the app in personal context, if team owner doesn't allow app update in team context. However, the user continues to use different versions of the app in personal and team contexts.

## Contexts in which apps upgrade

A user can use an app in more than one context in Teams. When a user consents to an app update, the app is updated in their chats, channels, and meetings but only in the contexts where the previous version of the app was added. Users don't need to update the app separately in each context if they provide consent. Users must provide consent in other contexts once, if a team owner updates the app in team context.

* **Personal app** context - When a user is using an app in their private workspace.

    :::image type="content" source="media/update-app-personal.png" alt-text="Screenshot that shows personal app context." lightbox="media/update-app-personal2.png":::

* **Tab app** context - When a user opens an app from a tab within a team, meeting, or group chat.

    :::image type="content" source="media/update-app-tab.png" alt-text="Screenshot that shows tab app context." lightbox="media/update-app-tab2.png":::

* **Bot app** context - When a bot app initiates update in a chat with users.

    :::image type="content" source="media/update-app-bot.png" alt-text="Screenshot that shows bot app context." lightbox="media/update-app-bot2.png":::

## Admin upload of updated custom apps

Custom apps that are created and deployed within your organization are available to the users on your organization. To provide a newer version of a custom app in the org store, an admin must follow one of the following steps:

* If developers send the app package to you, then upload it from within the Teams admin center.
* If developers submit the app for your approval, then review and approve the request in the Teams admin center.

For more information, see [how admins manage custom apps](teams-custom-app-policies-and-settings.md).

For custom apps to update, after you upload the new version of the app to Teams, users must individually provide their consent if it's required.

## Considerations for app upgrades

* If an app is not updated for a user, then the user continues to use the older version of an app. If an app updates in one context but not in the other context for a user, then the user continues to use two different versions of the app.

* App policies, usage reporting, audit logs, and other governance apply to all versions of an app. Admins retain complete control irrespective of the app versions used in the tenant.

* For updated apps, Teams administrators can't consent on behalf of the users. Users must individually provide their consent if it's required. Azure AD admin must [allow users to consent](/azure/active-directory/manage-apps/configure-user-consent?pivots=portal).

* A team owner can add an app in a team and view the update option when there's an available app update. It can be done from the **Manage team** page in their Teams client.

   :::image type="content" source="media/manage-teams-owner.png" alt-text="Screenshot that shows the Apps option in the Manage team page that teams owners can view.":::

* When an app is updated in a team, all team members can access the updated app. However, team members must still give their consent to update the same app in their other contexts.

* After updating in a context, the app automatically updates only in the contexts that the user is a member of and in the context where the previous version of the app was added. The app isn't updated in teams and groups that the user isn't a part of. The new version of the app isn't added to teams or groups where the app wasn't originally added.

* Teams admin can't forcibly update an app for a user if the user doesn't provide consent to an app.

* If the app developer changes the ID of a bot in a newer version of an app, then a new bot instance engages with users. The previous bot is no longer part of the app (developer changes the `botId` property in the app manifest file) and the chat history is left as is to preserve it. The icon and name of the previous bot reverts to the values that the developer provided when registering their bot in [Microsoft Bot Framework](https://dev.botframework.com/). The previous bot doesn't display the icon or the name of the new version of the app. The previous bot doesn't belong to any app (as `botId` isn't mentioned in app manifest file) and hence app permission policies don't apply to it.

## Related articles

* [Understand manifest schema for updates done in apps](/microsoftteams/platform/resources/schema/manifest-schema).
* [How Azure AD admin allows users to consent](/azure/active-directory/manage-apps/configure-user-consent?pivots=portal)
* [Know about custom app management](teams-custom-app-policies-and-settings.md).
