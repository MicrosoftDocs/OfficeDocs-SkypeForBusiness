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

This article describes what you need to know to configure private lines for users in Microsoft Teams. A private line is a second phone number assigned to a user to allow them to make and receive calls from a different number than their primary line. Private lines are also known as secondary lines or secondary numbers. Private lines are typically configured for executives who give out the number to only people they wish to receive direct communications from.

Private lines only support inbound calling. When a user makes an outbound call, the call will be made from the user's primary line.

## Requirements

Keep the following requirements for private lines in mind:

- Users can only be assigned one private line
- Internal or external reverse number lookup (RNL) should work with private lines
- Multiple phone numbers must resolve to the same user
- A unique ringtone or call notification must be provided for private line calls
- Private lines must be from the same country and the same number type as the user's primary line
- Enterprise Voice Enabled must still be honored

### Licensing requirements

The automated provisioning and deprovisioning of private line licenses must match the user's primary line. The following table provides a mapping of the user license combinations that are simultaneously supported for private line and primary lines.

|User license combinations|Simultaneous phone number types allowed|
|Phone System|Direct Routing, Operator Connect, Teams Phone Mobile|
|Phone System + Calling Plans|Direct Routing, Operator Connect, Calling Plans|

## Inbound call handling rules

With a private line, all inbound call handling rules are ignored, including call forwarding, simultaneous ringing, and call groups. For example, if a user has a private line and a primary line, and the user has a call forwarding rule set up to forward calls to a delegate, the call will still ring the user's phone. If the user has voicemail enabled, unanswered calls will go to voicemail with the default ring time of 20 seconds. If the user doesn't have voicemail enabled and the call is unanswered, the busy signal will be played after 20 seconds.

## Call history

## Private line vs primary line

| Feature | Private line | Primary line |

## Assign a private line to a user

To assign a private line to a user, run the following PowerShell script:

```powershell

```

## Unassign a private line from a user

To unassign a private line to a user, run the following PowerShell script:

```powershell

```

## Emergency calling with private lines

## Related links

[Route inbound calls in Microsoft Teams](inbound-call-routing.md)
