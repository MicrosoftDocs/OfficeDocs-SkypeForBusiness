---
title: 'Private lines in Microsoft Teams'
author: mkbond007
ms.author: mabond
manager: serdars
ms.topic: conceptual
ms.service: msteams
ms.reviewer: jenstr
ms.date: 10/24/2023
audience: admin
search.appverid: MET150
description: Learn how to configure private telephone lines for users in Microsoft Teams.
ms.localizationpriority: medium
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - Tier1
f1.keywords:
- CSH
ms.custom: 
appliesto: 
  - Microsoft Teams
---

# Private telephone lines with Microsoft Teams

This article describes what you need to know to configure private lines for users in Microsoft Teams. A private line is a second phone number assigned to a user to allow them to make and receive calls from a different number than their primary line. Private lines are typically configured for executives who give out the number to only people they wish to receive direct communications from.

Private lines only support inbound calling. When a user makes an outbound call, the call will be made from the user's primary line.

## Requirements

Keep the following requirements for private lines in mind:

- Users can only be assigned one private line
- Internal or external reverse number lookup (RNL) should work with private lines (should?)
- Multiple phone numbers must resolve to the same user
- A unique ringtone or call notification must be provided for private line calls
- Private lines must be from the same country and the same number type as the user's primary line
- Users must be voice enabled for private lines

### Licensing requirements

The automated provisioning and deprovisioning of private line licenses must match the user's primary line. The following table provides a mapping of the user license combinations that are simultaneously supported for private line and primary lines.

|User license combinations|Simultaneous phone number types allowed|
|-----|-----|
|Phone System|Direct Routing, Operator Connect, Teams Phone Mobile|
|Phone System + Calling Plans|Direct Routing, Operator Connect, Calling Plans|
|?|?|

## Inbound call handling rules

With a private line, all inbound call handling rules are ignored, including call forwarding, simultaneous ringing, and call groups. For example, if a user has a private line and a primary line, and the user has a call forwarding rule set up to forward calls to a delegate, the call will still ring the user's primary line and won't be forwarded to the delegate. If a user with a private line has voicemail enabled, unanswered calls will go to voicemail with the **default ring time of 20 seconds/after ringing for 1 minute**. If the user doesn't have voicemail enabled and the call is unanswered, the busy signal will be played after 20 seconds.

Inbound calls to users with a private line will display a message showing the call as private. The call history in Teams will also show a label that an incoming call was made to the private line.

## Configure a private line for a user

Currently, private lines can only be configured with PowerShell. You must have Teams PowerShell Module version 5.4.0 or higher to use the updated [CsPhoneNumberAssignment](/powershell/module/teams/set-csphonenumberassignment) cmdlets. You'll use these cmdlets to create and manage private line policies.

### Assign a private line to a user

The following PowerShell script assigns the Microsoft Calling Plan phone number +4532759474 as a private line for the user user1@contoso.com:

```powershell
Set-CsPhoneNumberAssignment -Identity main@contoso.com -PhoneNumber '+4532759474' -PhoneNumberType CallingPlan -AssignmentCategory Private
```

### Unassign a private line from a user

The following PowerShell script unassigns the Microsoft Calling Plan phone number +4532759474 as a private line for the user user1@contoso.com:

```powershell
Remove-CsPhoneNumberAssignment -Identity user1@contoso.com -PhoneNumber +4532759474 -PhoneNumberType CallingPlan -AssignmentCategory Private
```

The following PowerShell script removes a phone number from user1@contoso.com with the -RemoveAll parameter:

```powershell
Remove-CsPhoneNumberAssignment -Identity user1@contoso.com -RemoveAll 
```

If you remove a user's primary number but not their private number, the user will still be able to use their private line for calls.

## Related links

[Route inbound calls in Microsoft Teams](inbound-call-routing.md)
