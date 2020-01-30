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

---

# Teams and Skype interoperability

This article gives you an overview of the interoperability capabilities between Microsoft Teams and Skype (Consumer). Learn how Teams users and Skype users can communicate through chats and calls and the admin controls that apply.

Teams users in your organization can chat with and call Skype users who are inside or outside your organization and vice versa. Teams users can search for and start a one-on-one conversation or an audio/video call with a Skype user. Skype users can search for and start a one-on-one conversation or an audio/video call with a Teams user. This is available on the desktop, web, and mobile (Android and iOS) clients for both Teams and Skype.

Conversations are text-only. This means that there's no rich formatting, @mentions, emojis, or other any of the other chat features that are available in a native Teams chat experience. Although Teams users and Skype users can find, chat, and call each other, at this time, they can't see each other's presence.

## Chat and calling experience

Here's an overview of what the chat and calling experience looks like.

### Teams user starts a chat or call with a Skype user

Teams users can search for a Skype user by typing the email address of the Skype account in a new chat or in the search bar. (Searching by using a Skype Id or phone number won't work). The Teams user can then select the Skype user in the search results to start a chat or call with them.

A Skype user may choose not to appear in search results. In this case, they won't show up in the search results in Teams and Teams users won't be able to find them.

### Skype user starts a chat or call with a Teams user

Skype users can search for and start a chat with a Teams user by using their email address. The Teams user is notified that they have a new message from a Skype user and have to first accept the message before they can view it.

Here's an example of the notification that Teams users get:

PLACEHOLDER FOR IMAGE

- If the Teams user selects **Accept**, the Skype user is added to their contacts list, and both users can chat and call each other.
- If the Teams user selects **Block**, the conversation is blocked, and subsequent messages and calls from that Skype user are blocked.
- If the Teams user selects **View messages**, the message is displayed in Teams, which helps the user decide whether to accept or block the conversation.

### Teams user blocks or unblocks a Skype user

After a Teams user accepts the initial conversation request from a Skype user, they can choose to block and unblock that person at any time. Skype users won't know that they've been blocked.

Blocked Skype users, along with other people and PSTN phone numbers that a Teams user has blocked, are listed on the user's blocked contact list in Teams.

## Set whether Teams users can communicate with Skype users

As an admin, you set external access settings by using the Microsoft Teams admin center or PowerShell to control whether Teams users in your organization can communicate with Skype users. By default, the capability is turned off for new tenants.

> [!NOTE]
> If you upgraded from Skype for Business to Teams, the existing federation setting in the Skype for Business admin center is migrated to Teams. If your users are in Teams Only mode, chats and calls from Skype users to Teams users are delivered to Teams. If your users are in Islands mode, chats and calls from Skype users to Teams users are delivered to Skype for Business.

### In the Microsoft Teams admin center

In the Microsoft Teams admin center, go to**Teams** > **Org-wide settings** > **External access**, and then PLACEDHOLDER. For steps on how to do this, see [Manage external access in Teams](manage-external-access.md).

### Using PowerShell

Use the [Set-CsExternalAccessPolicy](https://docs.microsoft.com/powershell/module/skype/set-csexternalaccesspolicy?view=skype-ps) cmdlet together with the ```EnablePublicCloudAccess``` parameter to control whether Teams users can communicate with Skype users. Setting the parameter to ```true``` allows Teams users to communicate with Skype users.

## Related topics

- [Teams PowerShell overview](teams-powershell-overview.md)
