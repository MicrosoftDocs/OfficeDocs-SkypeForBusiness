---
title: Availability and behavior of Teams apps for different types of users
author: ashishguptaiitb
ms.author: guptaashish
ms.reviewer: joglocke
manager: serdars
ms.topic: article
audience: admin
ms.service: msteams
ms.subservice: teams-apps
search.appverid: MET150
description: Learn how apps in Microsoft Teams work differently for guests, federated users, and anonymous users.
ms.localizationpriority: high
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
appliesto: 
  - Microsoft Teams
---

# Use Teams apps as external or guest user

Teams apps behave when guest, external (federated), and anonymous users are present in a Teams context.

* A **guest user** is someone who isn't an employee, student, or member of your organization. They don't have a school or work account with your organization.

* An **external (federated) user** is from another domain and does not have access to your organization's Teams resources.

  > [!Note]
  > For a more detailed comparison between guest and external users, see [communicate with users from other organizations](./communicate-with-users-from-other-organizations.md).

* An **anonymous user** is a user who joins a meeting via a link. The user isn't logged in with their Microsoft account or their organization’s account.

## Guests

### Install, update, and delete for guests

Guests can't install, update, or delete apps into a shared context, such as a chat, channel, or meeting. Guests can do so in their personal scope using message extensions and direct links. Guests can't access the Teams app store from the Teams desktop app, but can access the store with a direct link.

### Usage behavior and policy for guests

Guests can use an app if the app was installed by a native user.

#### Bots installed to a channel

Guests can mention the bot and interact with adaptive cards.

#### Personal bots installed with policies

* For any app, guests adhere to global and org-wide permission policies set for the host organization. If an app is blocked for the whole host organization, then guests can't use the app either.
* Any bot included in the global default app setup policy will also be installed for guests.
* After a bot is installed, bots can proactively communicate with guests and guests can communicate back with bots.
* You can't remove a guest from the global default app setup policy.
* To avoid guest from accessing bots, you can create more app setup policies, assign them to internal users, and install bots with the custom policies.

## Federated users

### Install, update, and delete for federated users

Federated users can't install, update, or delete apps into any context, such as a personal, chat, channel, or meeting. They don't have access to the Teams app store of the hosting organization.

### Usage behavior and policy for federated users

* People from other organizations adhere to the hosting organization's global (org-wide default) policy
* Users in the hosting organization can add apps in meeting chats with people from other organizations. People from other organizations can't add apps in meeting chats but can interact with bots, tabs and message extensions once added to the chat.
* After a bot is installed in a meeting chat, it can proactively communicate with people from other organizations in that chat and those people can communicate with bot.
* The data policies of the hosting organization are applied.
* The data sharing practices of any third-party apps shared by that user's organization are applied.

## Anonymous users

### Install, update, and delete for anonymous users

Anonymous users can't install, update, or delete apps in meetings.

### Usage behavior and policy for anonymous users

Anonymous users can't directly use apps in meetings. If an app sends an adaptive card in the chat, anonymous users can interact with the card. Such users can interact with apps in Teams meetings if the user-level permission policy enables the app. Anonymous users inherit the user-level global default permission policy.

Anonymous users can interact only with the apps that are already available in a meeting but can't acquire and manage such apps. The native users can continue to use meetings apps even when the anonymous users are attending a meeting.

## See also

* [Allow anonymous users to join meetings](meeting-settings-in-teams.md#allow-anonymous-users-to-join-meetings).
* [Manage app setup policies in Microsoft Teams](teams-app-setup-policies.md).
