---
title: Teams and Skype Consumer interoperability  (Work in progress)
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
description: Learn how Teams users and Skype (Consumer) users can communicate. 

---

# Teams and Skype Consumer interoperability

This article gives you an overview of the interoperability capabilities between Microsoft Teams and Skype (Consumer) and the admin controls that apply.

## Chat

Teams users can chat with Skype users and vice versa. Teams users can search for and start a 1:1 conversation with a Skype user and Skype users can search for and start a 1:1 chat with a Teams user. This is available for Teams desktop, web, and mobile (Android and iOS) clients.

Conversations are text-only, with limited audio/video capabilities. There's no rich formatting, @ mentions, emojis, or other chat features that Teams users have in a native Teams chat experience. Although Teams users and Skype users can search for each other, at this time, they can't see each other's presence states.

### Scenarios

#### Teams user starts a chat with a Skype user

A Teams user can search for a Skype user by starting a new chat or from the search bar using the email address of the Skype account. Multiple Skype accounts can be returned in the search results. When the Teams user selects the Skype user, they can start chatting with them.

A Skype user may choose to not appear in search results. In this case, that user won't show up in the search results in Teams. 

#### Skype user starts a chat with a Teams user

When a Skype user starts a chat with a Teams user using their email address, the Teams user is notified that they have a new message from a Skype user. The Teams user has to accept the message before they can view it.  When clicking on the chat or message notification, the user is presented with the following screen:
 
If the user clicks on accept, the conversation is marked as allowed and subsequent messages/calls will flow as expected. If the user clicks on block, the conversation is marked as blocked, subsequent messages and calls won’t flow to the Teams client. 
If the user clicks on view messages, we will display the message(s) as it can help the Teams user to make a decision on whether she knows the Skype for consumer user, the email address might not be always top of mind. In order to engage in the conversation, the Teams user will have to accept/block the conversation.

When a Microsoft Teams users is chatting with an external (federated) user, the chat experience is limited to text. However, if both your Teams tenant and that of the external user is in the TeamsOnly upgrade mode, you can have a "native-Teams chat experience," which includes rich formatting, @mentions, and other chat features. In other words, you can have the same rich 1:1 Teams chat experience with eligible external users as you'd have with users in your organization. Native Teams chats with external users are still limited to 1:1 chats only (external users can't do group chats).

The native chat experience for external users is turned on for all Teams tenants, but not all users are eligible. To be offered a native chat experience, both the sender and receiver need to be on a Teams tenant that's running the TeamsOnly upgrade mode. To learn more about upgrade policies, read [Setting your coexistence and upgrade settings](setting-your-coexistence-and-upgrade-settings.md).

To see a list of capabilities for external access users in Teams, see [Compare external and guest access](communicate-with-users-from-other-organizations.md#compare-external-and-guest-access).

## How do I know if I'm in a native chat?

If you can only exchange text in your chat with an external user, then you're in a standard external-access (federated) chat. If you've got all of the other chat functionality, including formatting, @mentions, emojis, etc., then you're in a native Teams chat with your external user. 

Teams periodically checks the upgrade mode for external users and, when it finds an external user running Teams in the TeamsOnly upgrade mode, it'll prompt you to switch to a native Teams chat and lock the original chat.

When you switch to a native Teams chat, Teams doesn't merge the two conversations. Instead, you'll see both of the chats in your chat feed. The new, native-Teams chat is active, but the old, text-only chat is locked.

## What happens if a user isn't in Teams Only mode anymore?

If you were having a native Teams chat with an external user and then one of you gets switched out of the TeamsOnly upgrade mode, Teams locks the native Teams chat and gives you a link for a limited, text-only chat. You won't be able to continue in the native Teams chat. You can still read the native Teams chat, but you can't continue the conversation there.

If Teams finds an old text-only chat with this external user, it'll revive that chat. Otherwise, Teams creates a new text-only chat.


## Related topics

[Manage external access in Teams](manage-external-access.md)
