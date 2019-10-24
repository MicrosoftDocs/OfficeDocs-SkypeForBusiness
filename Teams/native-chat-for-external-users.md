---
title: Native chat experience for external access (federated) users in Microsoft Teams
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - Teams_ITAdmin_GuestAccess
  - M365-collaboration
ms.reviewer: vinbel
search.appverid: MET150
description: Learn about the native Teams chat experience for external access (federated) users in Microsoft Teams, available between external users where both users are in the TeamsOnly upgrade mode.

---

Native chat experience for external access (federated) users in Microsoft Teams
======================================

When a Microsoft Teams users is chatting with an external user, the chat experience is limited to text. However, if both your Teams tenant and that of the external user is in the TeamsOnly upgrade mode, you can have a "native-Teams chat experience," which includes rich formatting, @mentions, and other chat features. In other words, you can have the same rich 1:1 Teams chat experience with eligible external users as you'd have with users in your organization. Native Teams chats with external users are still limited to 1:1 chats only (external users can't do group chats).

The native chat experience for external users is turned on for all Teams tenants, but not all users are eligible. To be offered a native chat experience, both the sender and receiver need to be on a Teams tenant that's running the TeamsOnly upgrade mode. To learn more about upgrade policies, read [Setting your coexistence and upgrade settings](setting-your-coexistence-and-upgrade-settings.md).

To see a list of capabilities for external users in Teams, see [Compare external and guest access](communicate-with-users-from-other-organizations.md#compare-external-and-guest-access).

## How do I know if I'm in a native chat?

If you can only exchange text in your chat with an external user, then you're in a standard external-access (federated) chat. If you've got all of the other chat functionality, including formatting, @mentions, emojis, etc., then you're in a native Teams chat with your external user. 

When you chat with an external user for the first time, you'll be in a limited, text-only chat. Teams periodically checks the upgrade mode for external users and, when it finds an external user running Teams in the TeamsOnly upgrade mode, it'll ask if you want to switch to a native Teams chat.

When you switch to a native Teams chat, Teams doesn't merge the two conversations. Instead, you'll see both of the chats in your chat feed. The new, native-Teams chat is active, but the old, text-only chat is locked.

**LOLA: Add a screen cap of this message**



## What happens if a user isn't in Teams Only mode anymore?

If you were having a native Teams chat with an external user and then one of you gets switched out of the TeamsOnly upgrade mode, Teams locks the native Teams chat and gives you a link for a limited, text-only chat. You won't be able to continue in the native Teams chat. You can still read the native Teams chat, but you can't continue the conversation there.

If Teams finds an old text-only chat with this external user, it'll revive that chat. Otherwise, Teams creates a new text-only chat.

**LOLA: Add a screen cap of this message**



