---
title: Allow users to block Microsoft Teams chat messages
author: MicrosoftHeidi
ms.author: heidip
manager: jtremper
ms.reviewer: degoh
ms.date: 07/29/2024
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.custom: 
ms.collection: 
f1.keywords: 
  - NOCSH
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn how to allow users to block chats from people inside your organization.
---

# Allow users to block Microsoft Teams chat messages

[!INCLUDE[Teams Premium ECM](includes/teams-premium-ecm.md)]

You can allow users to block new incoming chats from people in your organization. When someone initiates a chat, users who have this policy assigned to them have the option to block that person. That person then can't communicate with the user or see their status. Users can unblock people from their chat history.

This feature only affects 1:1 chats from other people inside your organization. (All users can [block chats from people outside your organization](https://support.microsoft.com/office/5b590992-c938-4ed9-933b-37ee1fb84d32).) This feature doesn't affect channel or meeting chats.

Users must be using the [new Teams desktop client](new-teams-desktop-admin.md) or the web client to use this feature.

This feature requires Teams Premium.

## Manage who can block new incoming chats

Configuring internal message blocking requires two admin controls:

- The **Priority account chat control** messaging setting determines if message blocking is available in your organization.
- The **Priority account chat control** messaging policy control determines if a user assigned to that policy has the option to block new incoming chats.

To manage internal message blocking for your organization:

1. In the Teams admin center, expand **Messaging** and select **Messaging settings**.
1. Under **Advanced collaboration management**, set **Priority account chat control** to **On** or **Off**.
1. Select **Save**.

To manage internal message blocking for specific users or groups:

1. In the Teams admin center, expand **Messaging** and select **Messaging policies**.
1. Select the policy that you want to update or create a new one.
1. Set **Priority account chat control** to **On** or **Off**.
1. Select **Save**.

The messaging setting and the messaging policy must both be enabled for a user to be able to block new incoming chats.

## Related topics

[Manage Teams with policies](manage-teams-with-policies.md)
