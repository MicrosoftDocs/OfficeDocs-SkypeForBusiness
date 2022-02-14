---
title: Native chat experience for external (federated) users in Microsoft Teams
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - Teams_ITAdmin_GuestAccess
  - M365-collaboration
  - m365initiative-externalcollab
ms.reviewer: vinbel
search.appverid: MET150
f1.keywords:
- NOCSH
description: Learn about the native Teams chat experience for external access (federated) users in Microsoft Teams where both users are in the TeamsOnly upgrade mode.

---

# Native chat experience for external (federated) users in Microsoft Teams

When a Microsoft Teams user is chatting with an external (federated) user, the chat experience is limited to text. However, if both your Teams user and the person in another organization are in the TeamsOnly upgrade mode, you can have a "native-Teams chat experience," which includes rich formatting, @mentions, and other chat features.

The native chat experience for people in other organizations is turned on for all Teams tenants, but not all people are eligible. To be offered a native chat experience, both the sender and receiver need to be configured for TeamsOnly upgrade mode. To learn more about upgrade policies, read [Setting your coexistence and upgrade settings](setting-your-coexistence-and-upgrade-settings.md).

To see a list of capabilities for external access users in Teams, see [Compare external and guest access](communicate-with-users-from-other-organizations.md#compare-external-and-guest-access).

## How do I know if I'm in a native chat?

If you can only exchange text in your chat with people in other organizations, then you're in a standard external-access (federated) chat. If you've got other chat functionality, including formatting, @mentions, emojis, etc., then you're in a native Teams chat. 

Teams periodically checks the upgrade mode for people in other organizations and, when it finds an them running Teams in the TeamsOnly upgrade mode, it'll prompt you to switch to a native Teams chat and lock the original chat.

When you switch to a native Teams chat, Teams doesn't merge the two conversations. Instead, you'll see both of the chats in your chat feed. The new, native-Teams chat is active, but the old, text-only chat is locked.



## What happens if a user isn't in Teams Only mode anymore?

If you were having a native Teams chat with people in other organizations and then one of you gets switched out of the TeamsOnly upgrade mode, Teams locks the native Teams chat and gives you a link for a limited, text-only chat. You won't be able to continue in the native Teams chat. You can still read the native Teams chat, but you can't continue the conversation there.

If Teams finds an old text-only chat with this person, it'll revive that chat. Otherwise, Teams creates a new text-only chat.


## Related topics

[Manage external access in Teams](manage-external-access.md)
