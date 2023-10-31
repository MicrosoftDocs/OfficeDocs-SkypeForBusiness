---
title: 'Private lines in Microsoft Teams'
author: mkbond007
ms.author: mabond
manager: serdars
ms.topic: conceptual
ms.service: msteams
ms.reviewer: jenstr
ms.date: 10/31/2023
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

Private lines only support inbound calling and can't be used to make outgoing calls. When a user with a private line makes an outbound call, the call comes from the user's primary line and the user's caller ID and primary telephone number are displayed.

## Requirements

Keep the following requirements for private lines in mind:

- Users can only be assigned one private line
- Internal or external reverse number lookup (RNL) **should** work with private lines (should?)
- Private lines must be from the same country and the same number type as the user's primary line
- Users must be "voice enabled" for private lines

### Licensing requirements

The automated provisioning and deprovisioning of private line licenses must match the user's primary line. The following table provides a mapping of the user license combinations that are simultaneously supported for private line and primary lines.

|User license combinations|Simultaneous phone number types allowed|
|-----|-----|
|Phone System|Direct Routing, Operator Connect, Teams Phone Mobile|
|Phone System + Calling Plans|Direct Routing, Operator Connect, Calling Plans|
|?|?|

## Call handling for private lines

[add intro sentence here]

- With a private line, all inbound call handling rules are ignored, including call forwarding, simultaneous ringing, and call groups (any more to list here?). For example, if a user has a private line and a primary line, and the user has a call forwarding rule set up to forward calls to a delegate, the call will still ring the user's primary line and won't be forwarded to the delegate.
- If a user with a private line has voicemail enabled, unanswered calls will go to voicemail with the **default ring time of 20 seconds/after ringing for 1 minute**(?).
- If the user doesn't have voicemail enabled and the call is unanswered, the busy signal will be played after 20 seconds. Calls to a user's private line don't follow "do not disturb" rules.
- Incoming calls to a user's private line have a special ringtone to distinguish them from calls to the user's primary line.
- The Teams notification for the call tells the user that the incoming call is on his or her private line. The call history in Teams will also show a label that an incoming call was made to the private line.

## Configure a private line for a user

Currently, private lines can only be configured with PowerShell. You must have Teams PowerShell Module version 5.4.0 or higher to use the updated [CsPhoneNumberAssignment](/powershell/module/teams/set-csphonenumberassignment) cmdlets. You'll use these cmdlets to create and manage private line policies.

### Assign a private line to a user

Accounts for new users who need private lines use the same [CsPhoneNumberAssignment](/powershell/module/teams/set-csphonenumberassignment) cmdlet as accounts for new users who don't need private lines. The only difference is that you need to specify the parameter -AssignmentPlan with the **Private** attribute.

The following PowerShell script assigns the Microsoft Calling Plan phone number +4532759474 as a private line for the user user1@contoso.com:

```powershell
Set-CsPhoneNumberAssignment -Identity main@contoso.com -PhoneNumber '+4532759474' -PhoneNumberType CallingPlan -AssignmentCategory Private
```

When you assign a phone number to a user, the -EnterpriseVoiceEnabled parameter is automatically set to True.

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

[Set-CsPhoneNumberAssignment](/powershell/module/teams/set-csphonenumberassignment)
[Remove-CsPhoneNumberAssignment](/powershell/module/teams/remove-csphonenumberassignment)
[Route inbound calls in Microsoft Teams](inbound-call-routing.md)
[Block inbound calls](block-inbound-calls.md)
