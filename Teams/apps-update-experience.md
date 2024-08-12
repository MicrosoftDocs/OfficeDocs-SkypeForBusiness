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
ms.date: 06/05/2024
ms.reviewer: shmundra
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

When you install an app for the first time, it may require consent of an admin depending on the permissions that the app needs. When a new version of an app in use is made available, then the following app update scenarios can occur:

* If there are changes in app permissions or [some selected functionality](#conditions-when-an-app-update-requires-consent), then the app update requires consent from the app user.
* If the updated version of the app doesn't require new permissions and has only basic functionality changes, then it updates automatically.

As a Teams administrator, you can update Teams apps to help the users get the latest version of apps by performing one of the following tasks:

* When a new app version is available in Teams store, allow users to upgrade to the new version.
* When your developer submits a new version of a custom app, [update or approve the submission](#admin-upload-of-updated-custom-apps) and allow users to upgrade to the new version.

## Conditions when an app update requires consent

Apps update on their own if there's no change in functionality or request for organization's data. When one or more of the following changes are made to an app, it doesn't update on its own, unless an admin installed or pinned it. However, users may receive a notification to update an app if their consent is required and the app doesn't auto-update. Users can provide consent by selecting [`Update` option displayed in Teams](#update-to-new-version-by-users-and-admins).

* Add a bot or change the ID of the bot using the `botId` property.
* Change the `isNotificationOnly` property of an existing bot that changes the bot's notifications.
* Change `SupportsCalling`, `SupportsVideo`, and `SupportsFiles` properties of an existing bot to add capability to call, play video, and upload or download files.
* Change parameters in the `webApplicationInfo` in the manifest file.
* Add or remove permissions in authorization.
* Add a messaging extension.

When developers create a new version of an app, they can change the above values in the [app manifest file](/microsoftteams/platform/resources/schema/manifest-schema) or change the required permissions in their Microsoft Entra ID or both. Any of these changes lead to a change in app permissions. Hence, an update requires admin approval.

> [!TIP]
> Request your admin team to regularly monitor the [Message Center posts](/microsoft-365/admin/manage/message-center?view=o365-worldwide&preserve-view=true) in Microsoft 365 admin center, to stay informed of the upcoming changes to Teams apps governance methods or permissions. We recommend admin actions for smooth app updates in case of major changes. Know the [roles that can view Message Center posts](/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide#commonly-used-microsoft-365-admin-center-roles&preserve-view=true).

## Update to new version by users and admins

If an app update doesn't require consent, then it automatically updates. If consent is required, then Teams simplifies the app update experience by requesting user consent only once. When a user consents, Teams updates the app in the chats, channels, and meetings where the user is added. Users don't need to update the app separately in different contexts. If you pin or install an app, then it updates to a new version without requiring user consent. An update happens when a new version of the app is available in the Teams app store or when you upload a new version of a custom app.

To update their app, users must individually provide their consent. Admins can't consent on behalf of the users but can update an app manually.

| Who can consent to app update | How to update                                                                  | Conditions and scope of update                                                                                             |
|-------------------------------|--------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| User                          | Select [Update on the consent prompt](#contexts-in-which-apps-upgrade).        | [Microsoft Entra admin must allow user consent](/azure/active-directory/manage-apps/configure-user-consent?pivots=portal). |
| Admin                         | Open a team in Teams client and update an app from the team's settings page.   | Team and channel                                                                                                           |
| Team owner                    | Open a team in Teams client and update an app from their team's settings page. | In the teams that they own. For other contexts, users still need to provide their consent.                                 |

If none of above methods is used to update, then an app is never updated. Users can update their apps only in personal context, if a team owner doesn't allow app updates in team context. However, the user continues to use different versions of the app in personal and team contexts.

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

* If you pin or install an app, then it automatically updates when a new version is available.

* If an app isn't updated for a user, then the user continues to use the older version of an app. If an app updates in one context but not in the other context for a user, then the user continues to use two different versions of the app.

* App policies, usage reporting, audit logs, and other governance apply to all versions of an app. Admins retain complete control irrespective of the app versions used in their organization.

* For updated apps, Teams administrators can't consent on behalf of the users. Users must individually provide their consent if consent is required. Microsoft Entra admin must [allow users to consent](/azure/active-directory/manage-apps/configure-user-consent?pivots=portal).

* A team owner can add an app in a team and view the update option when there's an available app update. It can be done from the **Manage team** page in their Teams client.

   :::image type="content" source="media/manage-teams-owner.png" alt-text="Screenshot that shows the Apps option in the Manage team page that teams owners can view.":::

* When an app is updated in a team, all team members can access the updated app. However, team members must still give their consent to update the same app in their other contexts.

* After you update the app in a context, the app automatically updates only in the contexts that the user is a member of and in the context where the previous version of the app was added. The app isn't updated in teams and groups that the user isn't a part of. The new version of the app isn't added to teams or groups where the app wasn't originally added.

* Teams admin can't forcibly update an app for a user if the user doesn't provide consent to an app's update.

* If the app developer changes the ID of a bot in a newer version of an app, then a new bot instance engages with users. The previous bot is no longer part of the app (developer changes the `botId` property in the app manifest file) and the chat history is left as is to preserve it. The icon and name of the previous bot reverts to the values that the developer provided when registering their bot in [Microsoft Bot Framework](https://dev.botframework.com/). The previous bot doesn't display the icon or the name of the new version of the app. The previous bot doesn't belong to any app (as `botId` isn't mentioned in app manifest file) and hence app permission policies don't apply to it.

## Related articles

* [Understand manifest schema for updates done in apps](/microsoftteams/platform/resources/schema/manifest-schema).
* [How Microsoft Entra admin allows users to consent](/azure/active-directory/manage-apps/configure-user-consent?pivots=portal)
* [Know about custom app management](teams-custom-app-policies-and-settings.md).
