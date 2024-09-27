---
title: 'Configure private lines in Microsoft Teams'
author: mkbond007
ms.author: mabond
manager: pamgreen
ms.topic: article
ms.service: msteams
ms.reviewer: roykuntz
ms.date: 09/27/2024
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

# Configure private lines in Microsoft Teams

This article describes how to configure private telephone lines for users with Teams Phone in Microsoft Teams.

A *private line* is a second phone number assigned to a user. Typically, the user is an executive who shares the second number with only a few people.

Private lines support inbound calling only. A private line can’t be used to make outgoing calls.

## Requirements

Keep the following requirements for private lines in mind:

- Users can be assigned one private line only.
- Internal or external reverse number lookup (RNL) works with private lines.
- Private lines must be the same number type as the user’s primary line.
- Private lines must have the same licensing requirements as the user’s primary phone number.
- Users must be "voice enabled" for private lines

### Licensing requirements

The automated provisioning and deprovisioning of private line licenses must match the user's primary line. The following user license combinations are simultaneously supported for both private line and primary lines:

|User license combinations|Phone number category available for assignment|
|-----|-----|
|Teams Phone|Direct Routing, Operator Connect, Teams Phone Mobile|
|Teams Phone with Calling Plan|Direct Routing, Operator Connect, Teams Phone Mobile, Calling Plan|

For more information about licensing, see [Microsoft Teams add-on licenses](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md).

## Call handling for private lines

The following information describes how inbound calls are handled using a private line:

- For calls to a user’s private line, all inbound call handling rules are ignored, including call forwarding, simultaneous ringing, and call groups. For example, if a user has a private line and a primary line, and the user has a call forwarding rule set up to forward calls to a delegate, the call still rings the user's primary line and isn't forwarded to the delegate.
- If a user with a private line has voicemail enabled, the call goes to voicemail per normal.
- If the user doesn't have voicemail enabled and the call is unanswered, the busy signal will be played after 1 minute.
- Calls to a user's private line still follow "do not disturb" rules. For example, if a user is in "do not disturb" mode, the user doesn't hear a ringtone and the call is routed to voicemail, just as calls to the user's primary line are routed during "do not disturb" mode.
- Incoming calls to a user's private line have a special ringtone to distinguish them from calls to the user's primary line.
- The Teams notification for the call tells the user that the incoming call is on their private line. The call history in Teams will also show a label that an incoming call was made to the private line.

## Configure a private line for a user

Private lines can be configured in the Teams admin center or with PowerShell. You must have Teams PowerShell Module version 5.4.0 or higher to use the updated [CsPhoneNumberAssignment](/powershell/module/teams/set-csphonenumberassignment) cmdlets.

### Using Teams admin center

#### Assign a private line to a user

1. From the Teams admin center, go to **Users** > **Manage users**.
1. Select a user.
1. From the user's Account tab, under Assigned phone number, select **Assign private phone number**.
1. From the Assign private phone number panel, select the **Private phone number type**.
1. From the Assign private phone number panel, select a phone number for **Assign private phone number**.
1. Assign an emergency location for the primary number.
1. Select **Apply**.

#### Unassign a private line from a user

1. From the Teams admin center, go to **Users** > **Manage users**.
1. Select a user.
1. From the user's Account tab, under Assigned phone number, select **View details**.
1. On the user's Private phone number, select **Edit**.
1. From the Assign private phone number panel, select **None** for **Assigned phone number**.
1. Select **Apply**.

### Using PowerShell

#### Assign a private line to a user

Accounts for new users who need private lines use the same [CsPhoneNumberAssignment](/powershell/module/teams/set-csphonenumberassignment) cmdlet as accounts for new users who don't need private lines. The only difference is that you need to specify the parameter `-AssignmentPlan` with the **Private** attribute.

The following PowerShell script assigns the Microsoft Calling Plan phone number +4532759474 as a private line for user1@contoso.com:

```powershell
Set-CsPhoneNumberAssignment -Identity user1@contoso.com -PhoneNumber '+14255551234' -PhoneNumberType CallingPlan -AssignmentCategory Private
```

When you assign a phone number to a user, the `-EnterpriseVoiceEnabled` parameter is automatically set to **True**.

#### Unassign a private line from a user

The following PowerShell script unassigns the Microsoft Calling Plan phone number +14255551234 as a private line for user1@contoso.com:

```powershell
Remove-CsPhoneNumberAssignment -Identity user1@contoso.com -PhoneNumber +14255551234 -PhoneNumberType CallingPlan
```

The following PowerShell script removes a phone number from user1@contoso.com with the `-RemoveAll` parameter:

```powershell
Remove-CsPhoneNumberAssignment -Identity user1@contoso.com -RemoveAll  
```

If you remove a user's primary number but not their private number, the user will still be able to use their private line for calls.

## Related links

[Set-CsPhoneNumberAssignment](/powershell/module/teams/set-csphonenumberassignment)

[Remove-CsPhoneNumberAssignment](/powershell/module/teams/remove-csphonenumberassignment)

[Route inbound calls in Microsoft Teams](inbound-call-routing.md)

[Block inbound calls](block-inbound-calls.md)
