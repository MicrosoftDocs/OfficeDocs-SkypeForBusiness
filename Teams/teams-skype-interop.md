---
title: Teams and Skype interoperability
author: LanaChin
ms.author: v-lanac
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-collaboration
ms.reviewer: vinbel
search.appverid: MET150
description: Learn about the interoperability capabilities between Teams users in your organization and Skype (Consumer) users. 
localization_priority: Normal
---

# Teams and Skype interoperability

[!INCLUDE [preview-feature](includes/preview-feature.md)]

This article gives you an overview of the interoperability capabilities between Microsoft Teams and Skype (Consumer). Learn how Teams users and Skype users can communicate through chats and calls and the admin controls that apply.

Teams users in your organization can chat with and call Skype users by using their email address and vice versa.

- Teams users can search for and start a one-on-one text-only conversation or an audio/video call with a Skype user.
- Skype users can search for and start a one-on-one text-only conversation or an audio/video call with a Teams user.

This is available on the desktop, web, and mobile (Android and iOS) clients for both Teams and Skype. For an optimal experience, we recommend Skype version 8.58 and later.

## Chat and calling experience

Here's an overview of the chat and calling experience.

### Teams user starts a chat or call with a Skype user

Teams users can search for a Skype user by typing their email address in a new chat or in the search bar.  The Teams user can then select the Skype user in the search results to start a chat or call with them.

A Skype user may choose not to appear in search results. In this case, they won't show up in the search results in Teams and Teams users won't be able to find them.

### Skype user starts a chat or call with a Teams user

Skype users can search for and start a chat with a Teams user by using their email address. The Teams user is notified that they have a new message from a Skype user and have to first accept the message before they can reply to it.

- If the Teams user selects **Accept**, the conversation is accepted, and both users can chat and call each other.
- If the Teams user selects **Block**, the conversation is blocked, and subsequent messages and calls from that Skype user are blocked.
- If the Teams user selects **View messages**, the message is displayed in Teams, which helps the user decide whether to accept or block the conversation.

> [!NOTE]
> If you upgraded from Skype for Business to Teams and your users are in Teams Only mode, chats and calls from Skype users to Teams users are delivered to Teams. If your users are in Islands mode, chats and calls from Skype users to Teams users are delivered to Skype for Business.

### Teams user blocks or unblocks a Skype user

After a Teams user accepts or blocks the initial conversation request from a Skype user, they can choose to block or unblock that person at any time, either in the conversation or in their privacy settings in Teams. Skype users won't know that they've been blocked.

Blocked Skype users, along with other people and public switched telephone network (PSTN) phone numbers that a Teams user has blocked, are listed on the user's blocked contact list in Teams.

## Limitations

- Conversations are text-only. This means that there's no rich formatting, @mentions, emojis, or other any of the other chat features that are available in a [native Teams chat experience](native-chat-for-external-users.md).
- Conversations are one-on-one only. Group chats aren't supported.
- Teams users and Skype users can't see each other's presence.
- Searching for Skype users by using their Skype ID or phone number isn't supported.

## Set whether Teams users can communicate with Skype users

As an admin, you use the Microsoft Teams admin center or PowerShell to set external access settings to control whether Teams users in your organization can communicate with Skype users. By default, this capability is turned off for new tenants.

If you upgraded from Skype for Business to Teams, the external communications settings that you configured in the Skype for Business admin center are migrated to Teams.

### In the Microsoft Teams admin center

In the Microsoft Teams admin center, go to **Org-wide settings** > **External access**, and then turn on **Users can communicate with Skype users**. For step-by-step guidance on how to configure this and other external access settings, see [Manage external access in Teams](https://docs.microsoft.com/microsoftteams/manage-external-access#allow-or-block-domains).

### Using PowerShell

Use the [Set-CsExternalAccessPolicy](https://docs.microsoft.com/powershell/module/skype/set-csexternalaccesspolicy) cmdlet together with the ```EnablePublicCloudAccess``` parameter to control whether Teams users can communicate with Skype users. Setting the parameter to ```true``` allows Teams users to communicate with Skype users.

## Related topics

- [Manage external access in Teams](manage-external-access.md)
- [Teams PowerShell overview](teams-powershell-overview.md)
