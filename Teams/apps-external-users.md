---
title: Availability and use of Teams apps by different types of users from outside an organization
author: ashishguptaiitb
ms.author: guptaashish
ms.reviewer: shmundra
manager: prkosh
ms.topic: article
audience: admin
ms.service: msteams
ms.subservice: teams-apps
search.appverid: MET150
description: Learn how apps in Microsoft Teams work for guests, external access users, and anonymous users.
ms.localizationpriority: high
ms.date: 06/20/2024
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
  - highpri
appliesto: 
  - Microsoft Teams
---

# Teams apps for external attendees or guests from outside an organization

Teams apps allow collaboration with people outside your organization. As an admin, you control who can access Teams chats, meetings, and channel to collaborate with your organization's users. For detailed information, see [how to allow collaboration with external attendees](manage-external-access.md) and [what can guests do in Teams](guest-access.md). This article focuses on use of apps by people outside your organization.

Teams users can add apps when they host meetings or chats with people from other organizations. They can also use apps shared by people in other organizations when they join meetings or chats hosted by those organizations. The data policies of the hosting user's organization, as well as the data sharing practices of any third-party apps shared by that user's organization, are applied.

The following types of users can be present in a Teams chat or meeting and if you allow it, they can use apps in Teams.

* A **guest** is someone who has an [Microsoft Entra B2B collaboration](/azure/active-directory/external-identities/what-is-b2b) guest account your organization.

* An **external access user** is from another domain and doesn't have access to your organization's Teams resources.

* An **anonymous user** is a user who joins a meeting via a link. The user isn't logged in with their Microsoft account or their organization’s account.

For a more detailed comparison between guest and external access users, see [communicate with users from other organizations](communicate-with-users-from-other-organizations.md).

## Guests

### Add, update, and delete apps for guests

* Guest users can't search and add apps from Teams app store (AppSource or client store) and from the in-context stores in Teams.

* Guests can't add, update, or delete apps into a shared context, such as a chat, channel, or meeting.

* Guest users can add apps using [deep links](/microsoftteams/platform/concepts/build-and-test/deep-link-application) shared with them by others. However, guest users can use such apps in personal scope only and the app icon doesn't display in the app bar.

* Guest users can use apps added by other org users in personal chats, group chats, and teams and channels.

### Usage behavior and policy for guests

Guests can use an app if the app was added by an organization's user.

#### Bots added to a channel

Guests can mention the bot and interact with adaptive cards.

#### Personal bots added with policies

* For any app, guests adhere to global and org-wide permission policies set for the host organization. If an app is blocked for the whole host organization, then guests can't use the app either.
* Any bot included in the global default app setup policy is also added for guests.
* After a bot is added, bots and guests can communicate with each other.
* You can't remove a guest from the global default app setup policy.
* To avoid guest from accessing bots, you can create more app setup policies, assign them to internal users, and add bots with the custom policies.

## External access users

### Add, update, and delete apps for external access users

External access users can't add, update, or delete apps into any context, such as a personal, chat, channel, or meeting. They don't have access to the Teams app store of the hosting organization.

### Usage behavior and policy for external access users

* People from other organizations adhere to the hosting organization's global (org-wide default) policy
* Users in the hosting organization can add apps in meeting chats with people from other organizations. People from other organizations can't add apps in meeting chats but can interact with bots, tabs and message extensions once added to the chat.
* After a bot is added in a meeting chat, it can proactively communicate with people from other organizations in that chat, and those people can communicate with bot.
* The data policies of the hosting organization are applied.
* The data sharing practices of any third-party apps shared by that user's organization are applied.

## Anonymous users

### Add, update, and delete apps for anonymous users

Anonymous users can't add, update, or delete apps in meetings.

### Usage behavior and policy for anonymous users

Anonymous users can't directly use apps in meetings. If an app sends an adaptive card in the chat, anonymous users can interact with the card. Such users can interact with apps in Teams meetings if the user-level permission policy enables the app. Anonymous users inherit the user-level global default permission policy.

Anonymous users can interact only with the apps that are already available in a meeting but can't acquire and manage such apps. The native users can continue to use meetings apps even when the anonymous users are attending a meeting.

### Allow anonymous users to use apps in meetings

By default, anonymous users can interact with the existing apps in a meeting. Anonymous users can't add new apps to a meeting. You can disallow anonymous users for interacting with apps.

1. Sign in to the Teams admin center and access **Meetings** > **[Meeting settings](https://admin.teams.microsoft.com/meetings/settings)**.

1. Under **Participants**, change the toggle for **Anonymous users can interact with apps in meetings** to **Off**.

1. Select **Save**.

## Related articles

* [How anonymous users can join meetings](meeting-settings-in-teams.md#allow-anonymous-users-to-join-meetings).
* [How to manage app setup policies in Teams](teams-app-setup-policies.md).
* [How to allow collaboration with guests and external participants](manage-external-access.md).
* [Know what can guests do in Teams](guest-access.md)
