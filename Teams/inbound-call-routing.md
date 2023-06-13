---
title: 'Routing inbound PSTN & VoIP federated calls in Microsoft Teams'
author: mkbond007
ms.author: mabond
manager: serdars
ms.topic: conceptual
ms.service: msteams
ms.reviewer: jenstr
ms.date: 06/12/2023
audience: admin
search.appverid: MET150
description: Learn how to route inbound PSTN & VoIP federated calls in Microsoft Teams.
ms.localizationpriority: medium
ms.collection: 
  - M365-voice
  - Tier1
f1.keywords:
- CSH
ms.custom: 
appliesto: 
  - Microsoft Teams
---

# Routing inbound PSTN & VoIP federated calls

As an admin, you can create policies that help prevent your users from getting unwanted calls from external parties. You can control whether external calls should always be sent to voicemail, sent to unanswered settings, use normal call routing, or allow your users within the policy to decide.

Calls from a Public Switched Telephone Network (PSTN) and federated Teams or Skype for Business users are considered external calls.

This article applies to Microsoft Calling Plans, Operator Connect, Teams Phone Mobile, Direct Routing, and federated VoIP calls. These policy settings are also available for GCCH & DoD use.

These inbound routing policies have precedence over other call forwarding settings such as **Call forwarding and simultaneous to people in your organization**, **Call forwarding and simultaneous ringing to external phone numbers**, **Delegation for inbound and outbound calls**, and **Inbound calls can be routed to call groups**.

## Inbound PSTN calls

### Using the Teams admin center

1. In the left navigation of the Microsoft Teams admin center, click **Voice** > **Calling policies**.

1. Select the policy you would like to update or click **Add** to create a new policy.

1. 

### Using PowerShell

```powershell

```

For more information, see [Set-CsTeamsCallingPolicy](/powershell/module/skype/set-csteamscallingpolicy).

## Inbound VoIP federated calls

### Using the Teams admin center

1. In the left navigation of the Microsoft Teams admin center, click **Voice** > **Calling policies**.

1. Select the policy you would like to update or click **Add** to create a new policy.

### Using PowerShell

```powershell

```

For more information, see [Set-CsTeamsCallingPolicy](/powershell/module/skype/set-csteamscallingpolicy).

## Related articles

[Set-CsTeamsCallingPolicy](/powershell/module/skype/set-csteamscallingpolicy)

[Configure calling policies in Microsoft Teams](teams-calling-policy.md)

[Block inbound calls in Microsoft Teams](block-inbound-calls.md)

[Configure call settings for your users](user-call-settings.md)

[Voice policies reference](settings-policies-reference.md#voice)
