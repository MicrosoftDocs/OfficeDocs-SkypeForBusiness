---
title: Microsoft Teams chat experience when communicating with people outside the organization
ms.author: jtremper
author: jacktremper
manager: pamgreen
ms.topic: article
ms.service: msteams
audience: admin
ms.custom: chat-teams-channels-revamp
ms.collection: 
  - Teams_ITAdmin_GuestAccess
  - M365-collaboration
  - m365initiative-externalcollab
ms.reviewer: vinbel
ms.date: 10/24/2019
search.appverid: MET150
ms.localizationpriority: medium
f1.keywords:
- NOCSH
description: Learn about the native Teams chat experience for external access users in Microsoft Teams where both users are in the TeamsOnly upgrade mode.
---

# Microsoft Teams chat experience when communicating with people outside the organization

When a Microsoft Teams user is chatting with someone outside the organization, there are two possible chat experiences:

- Native chat - a chat experience that includes formatting, @mentions, emojis, etc.
- Text-only chat

Native chat is available when communicating with people in other Microsoft 365 organizations, provided both users are in [Teams only coexistence mode](setting-your-coexistence-and-upgrade-settings.md) and both are in the same cloud environment. It's also available when communicating with Teams users not managed by an organization (those using Microsoft accounts).

Text-only chat is available in all other chat experiences, including:

- Communicating with Skype for Business users
- Communicating with Skype users
- Communicating between cloud environments, such as GCC to GCC High or commercial cloud

The following table shows the chat experience users get when communicating between organizations, across clouds, and with unmanaged Teams accounts (people with personal accounts).

|Chat experience|Commercial|GCC|GCC High|DoD|
|:---|:---------|:--|:-------|:--|
|**Commercial**|Native|Text only|Text only|Text only|
|**GCC**|Text only|Native|Text only|Text only|
|**GCC High**|Text only|Text only|Native|Text only|
|**DoD**|Text only|Text only|Text only|Native|
|**Skype**|Text only|Not available|Not available|Not available|
|**Skype for Business Server**|Text only|Text only|Text only|Text only|
|**Unmanaged Teams accounts**|Native|Not available|Not available|Not available|

## Teams chat experience while migrating from Skype for Business Server

Teams periodically checks the upgrade mode for people in other organizations and, when it finds them running Teams in the TeamsOnly upgrade mode, it prompt you to switch to a native Teams chat and lock the original chat.

When you switch to a native Teams chat, Teams doesn't merge the two conversations. Instead, you'll see both of the chats in your chat feed. The new, native-Teams chat is active, but the old, text-only chat is locked.

If you were having a native Teams chat with people in other organizations and then one of you gets switched out of the TeamsOnly upgrade mode, Teams locks the native Teams chat and gives you a link for a limited, text-only chat. You won't be able to continue in the native Teams chat. You can still read the native Teams chat, but you can't continue the conversation there.

If Teams finds an old text-only chat with this person, it revives that chat. Otherwise, Teams creates a new text-only chat.

## Related topics

[Manage external access in Teams](manage-external-access.md)
