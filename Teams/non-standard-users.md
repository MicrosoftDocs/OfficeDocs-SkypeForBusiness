---
title: Teams apps behavior for non-standard users 
author: cichur
ms.author: v-cichur
ms.reviewer: joglocke
manager: serdars
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn how apps in Microsoft Teams behave for non-standard users.
localization_priority: Normal
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
appliesto: 
  - Microsoft Teams
---

# Microsoft Teams apps behavior for non-standard users

This article describes how apps in Teams behave when guest, external (federated), and anonymous users are present in a Teams context.

- A **guest user** is someone who isn't an employee, student, or member of your organization. They don't have a school or work account with your organization.

- An **external (federated) user** belongs to another domain and has no access to your organization's teams or team resources.

  > [!Note]
  > For a more detailed comparison of guest versus external users, [see communicate with users from other organizations](./communicate-with-users-from-other-organizations.md).

- An **anonymous user** is a concept in Teams meetings where the user has joined the meeting via a link. The user hasn't logged in with their Microsoft or organization’s account.

## Guest user access

### Install, update, and delete for guest users

Guests can't install, update, or delete apps into a shared context, such as a chat, channel, or meeting. They can install, update, or delete apps to their personal scope using message extensions and direct links. Guests don't have access to the Teams app store from the Teams desktop application, but they can access it with a direct link.

### Usage behavior and policy for guest users

Guests can use an app if the app was installed by a native user.

### Bots installed to a channel

Bots can proactively message guest users, but guests can't interact with the bot. Guests can't message the bot one-to-one, mention the bot, or interact with adaptive cards that communicate with the bot.

### Personal bots installed with policies

- Guests will adhere to global and org-wide permission policies set for the host tenant for any app. If an app is blocked for the whole host organization, then guests can't use the app either.
- Any bot included in the global default app setup policy will also be installed for guests.
- Bots can proactively communicate with guests, and guests can communicate back with bots after being added to a global default app setup policy that has contains bots.
- You cannot remove a guest from the global default app setup policy.
- To avoid a guest accessing a bot, you should create additional app setup policies, assign those to internal users, and install the bot with the custom policy.

## External (Federated) user access

### Install, update, and delete for external users

External users can't install, update, or delete apps into any context, such as a personal, chat, channel, or meeting. They don't have access to the Teams app store.

### Usage behavior and policy for external users

External users can't use any Teams apps, and when an external user is added to a context with native users, all users – native and external – can no longer use apps.

External users aren't impacted by app policies, because they can't use Teams apps.

## Anonymous user in meetings access

### Install, update, and delete for anonymous users

Anonymous users can't install, update, or delete apps in meetings.

### Usage behavior and policy for anonymous users

Anonymous users can't directly use apps in meetings. Native users can continue to use meetings apps if anonymous users are present. If an app sends an adaptive card in the chat, anonymous users can interact with the card For more information, see [Allow anonymous users to join meetings](https://docs.microsoft.com/microsoftteams/meeting-settings-in-teams#allow-anonymous-users-to-join-meetings).

Anonymous users will inherit the user-level global default permission policy. They can interact with apps in Teams meetings if the user-level permission policy has enabled the app. Anonymous users can only interact with apps that are already available in a meeting and can't acquire and/or manage these apps.
