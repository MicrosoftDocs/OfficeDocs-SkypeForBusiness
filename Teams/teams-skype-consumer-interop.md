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

This article gives you an overview of the interoperability capabilities between Microsoft Teams and Skype (Consumer). Learn how Teams users and Skype users can communicate and the admin controls that apply.

## Chat

Teams users can chat with Skype users and vice versa. Teams users can search for and start a 1:1 conversation with a Skype user and Skype users can search for and start a 1:1 chat with a Teams user. This is available for Teams desktop, web, and mobile (Android and iOS) clients.

Conversations are text-only, with limited audio/video capabilities. This means that there's no rich formatting, @mentions, emojis, or other chat features that are available in a native Teams chat experience. Although Teams users and Skype users can search for each other, at this time, they can't see each other's presence states.

### Scenarios

Here's what chat experience looks like between Teams users and Skype users.

#### A Teams user starts a chat with a Skype user

A Teams user can search for a Skype user by typing the email address of the Skype account in a new chat or in the search bar. Multiple Skype accounts can be returned in the search results. The Teams user then selects the Skype user to start a conversation with them.

A Skype user may choose not to appear in search results. In this case, that user won't show up in the search results in Teams.

#### A Skype user starts a chat with a Teams user

When a Skype user searches for and starts a chat with a Teams user by using their email address, the Teams user is notified that they have a new message from a Skype user. They have to accept the message before they can view it.

Here's an example of a chat notification that Teams users get:

- If the user selects **Accept**, the conversation is marked as allowed and subsequent messages flow between Teams and Skype.
- If the user selects **Block**, the conversation is marked as blocked, and subsequent messages won’t flow to Teams.
- If the users selects **View messages**, the message is displayed. This helps the Teams user decide whether to accept or block the conversation.

#### A Teams user blocks a Skype user

### Set whether Teams users can chat with Skype users

As an admin, you can use the Microsoft Teams admin center or PowerShell to control whether Teams users in your organization can search for and chat with Skype users. 

#### In the Microsoft Teams admin center

1. In the left navigation, go to **Org-wide settings** > **External access**.
2. Turn on or turn off 
3. Click **Save**. 


#### Using PowerShell

To learn more, see [Set-CsExternalAccessPolicy](https://docs.microsoft.com/powershell/module/skype/set-csexternalaccesspolicy?view=skype-ps).

## Related topics

- [Manage external access in Teams](manage-external-access.md)
- [Teams PowerShell overview](teams-powershell-overview.md)
