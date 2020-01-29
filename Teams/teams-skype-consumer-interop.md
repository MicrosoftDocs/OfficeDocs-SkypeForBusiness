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

This article gives you an overview of the interoperability capabilities between Microsoft Teams and Skype (Consumer). Learn how Teams users and Skype users can communicate through chat and calling and the admin controls that apply.

Teams users can chat with and call Skype users and vice versa.

- Teams users can search for and start a one-on-one conversation or an audio/video call with a Skype user.
- Skype users can search for and start a one-on-one conversation or an audio/video call with a Teams user.

This is available in the desktop, web, and mobile (Android and iOS) clients for both Teams and Skype.

Conversations are text-only. This means that there's no rich formatting, @mentions, emojis, or other chat features that are available in a native Teams chat experience. Although Teams users and Skype users can search for, chat, and call each other, at this time, they can't see each other's presence.

### Chat and calling experience

Here's what chat and calling experience looks like between Teams users and Skype users.

#### Teams user starts a chat with a Skype user

Teams users can search for a Skype user by typing the email address of the Skype account in a new chat or in the search bar. Multiple Skype accounts can be returned in the search results. The Teams user can then select the Skype user to start a chat or call.

A Skype user may choose not to appear in search results. In this case, they won't show up in the search results in Teams.

#### Skype user starts a chat with a Teams user

When a Skype user searches for and start a chat with a Teams user by using their email address, the Teams user is notified that they have a new message from a Skype user. They have to first accept the message before they can view it.

Here's an example of the notification that Teams users get:

- If the Teams user selects **Accept**, the conversation is marked as allowed and both users can chat and call each other.
- If the Teams user selects **Block**, the conversation is marked as blocked, and subsequent messages and calls from that Skype user are blocked.
- If the Teams user selects **View messages**, the message is displayed in Teams, which helps the user decide whether to accept or block the conversation.

#### Teams user blocks a Skype user

Teams users can block contacts and PSTN numbers.

### Set whether Teams users can communicate with Skype users

As an admin, you can use the Microsoft Teams admin center or PowerShell to control whether Teams users in your organization can communicate with Skype users.

#### In the Microsoft Teams admin center

1. In the left navigation, go to **Org-wide settings** > **External access**.
2. Turn on or turn off 
3. Click **Save**.

#### Using PowerShell

Use the [Set-CsExternalAccessPolicy](https://docs.microsoft.com/powershell/module/skype/set-csexternalaccesspolicy?view=skype-ps) together with the parameter. By default, the parameter is set to false. Setting the parameter to true enables Teams and Skyper users to communicate with each other. 

## Related topics

- [Manage external access in Teams](manage-external-access.md)
- [Teams PowerShell overview](teams-powershell-overview.md)
