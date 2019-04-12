---
title: Message delegation  
author: jambirk
ms.author: jambirk 
manager: serdars
audience: ITPro
ms.topic: article 
ms.service: msteams 
search.appverid: MET150
localization_priority: Normal
MS.collection: Teams_ITAdmin_PracticalGuidance
appliesto:
- Microsoft Teams
ms.reviewer: acolonna
description: (may 2019) A user can explicitly set another user as a delegate in their status message. 
---

# Set a delegate status

A user can already explicitly set their status to Away or Do not Disturb. The delegation feature allows them to @username mention another user in part of a text status message, and suggest that while they are unavailable people who want to contact them contact the @username mentioned user instead. The person who has been assigned as a delegate is notified that they have been nominated to be a delegate. When a chat conversation or compose mode is initiated with the target user who has a delegate assigned, their status banner shows the sender clearly that messages should be sent to the assigned delegate instead.

This is a user-initiated process in the client, and no Admin involvement is required.

## Delegation overview

*Usage example without setting delegates:*  Dr. Franco Piccio is on-call at the radiology department. He receives an urgent personal call and has to step away for the next couple of hours. He asks one of his peers in the radiology department, Dr. Lena Ehrle, to cover for him while he is gone. He informally hands over his pager to Dr. Ehrle, who is listening for urgent messages and pings on the pager and responds to them on behalf of Dr. Piccio in addition to her current responsibilities. Others on the team may not realize the informal delegation happened, and confusion ensues with a patient's care.

*Usage example with setting delegates:* Dr. Franco Piccio is on-call at the radiology department. He receives an urgent personal call and has to step away for the next couple of hours. He asks one of his peers in the radiology department, Dr. Lena Ehrle to cover for him while he is gone. He changes his status in Teams to do not disturb and sets Dr. Ehrle as a delegate, enabling auto-forward of messages. Others on the team realize the delegation happened as they're attempting to contact Dr. Piccio, and little to no confusion ensues with a patient's care.

## Impact of co-existence modes on Status in the Teams client

Admins should be aware that status notes and delegation will depend partly on a user’s co-existence mode. This matrix shows the possibilities:

|Co-Existence Mode | Expected Behavior|
|---|---|
|TeamsOnly |Users can set a note only from Teams. <br> User’s Teams note is visible in Teams & SfB. |
|Islands | User’s note set in Teams visible only in Teams. <br> User’s note set in SfB visible only in SfB |
|SfB* modes | Users can set a note only from SfB. <br> User’s SfB note is visible in SfB & Teams.  |
|||

A user can only set a note in Teams if their mode is TeamsOnly or Islands.  

### Displaying notes set in Skype for Business
  
There is no visual indication that a note was set from Skype for Business.

Skype for Business doesn’t enforce a character limit on status notes. Microsoft Teams will only display the first 280 characters of a note set from Skype for Business. An ellipse (…) at the end indicates truncation.
  
Skype for Business doesn’t support expiry times for notes.

Migration of notes from Skype for Business to Teams is not supported when a user is upgraded to TeamsOnly mode.

## Configure feature

This feature does not require configuration in Microsoft Teams admin center, or using PowerShell.

## Related topics

[Coexistence with Skype for Business](../coexistence-chat-calls-presence.md)
