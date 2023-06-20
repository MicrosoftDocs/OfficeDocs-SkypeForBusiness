---
title: 'Routing inbound external calls in Microsoft Teams'
author: mkbond007
ms.author: mabond
manager: serdars
ms.topic: conceptual
ms.service: msteams
ms.reviewer: jenstr
ms.date: 06/20/2023
audience: admin
search.appverid: MET150
description: Learn how to route inbound PSTN & external Teams VoIP calls in Microsoft Teams.
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

# Routing inbound external calls

This article describes how to route incoming calls from the Public Switched Telephone Network (PSTN) and calls from external Teams VoIP users.

*External calls* are considered calls made from Teams VoIP users or Skype for Business users who are outside of your organization. Teams or Skype for Business (Online or On-Premises) VoIP calls made within the same organization are considered *internal calls*.

As an admin, you can create policies that help prevent your users from getting unwanted calls from external parties. You can control whether external calls should always be sent to voicemail, sent to unanswered settings, use normal call routing, or allow your users within the policy to decide.

This article applies to Microsoft Calling Plans, Operator Connect, Teams Phone Mobile, Direct Routing, and federated VoIP calls. These policy settings are also available for GCCH & DoD use.

If **Unanswered** or **Voicemail** is used, either of these settings will have precedence over other call forwarding settings like call forwarding with simultaneous ringing to delegate, call groups, or call forwarding.

## Inbound PSTN calls

This policy setting controls how inbound PSTN calls should be routed.

You can configure this setting with the Teams admin center or by using PowerShell.

### Using the Teams admin center

1. In the left navigation of the Microsoft Teams admin center, click **Voice** > **Calling policies**.

1. Select the policy you would like to update or click **Add** to create a new policy.

1. For **Inbound PSTN call routing**, you have the following options:

    - **Regular Incoming** The call will be routed per normal. This is the default setting.
    - **Unanswered** The call will be routed according to the unanswered call forwarding settings set for that user.
    - **Voicemail** The call will be routed directly to voicemail and will not be shown to the user. If the called user doesn't have voicemail enabled, the call will be disconnected.
    - **User Override** The call will currently be routed as **Regular Incoming**.

1. Click **Save**.

### Using PowerShell

For example, this script sets InboundPstnCallRoutingTreatment to route external calls according to the unanswered call forwarding settings for users in the Global (default) Teams Calling Policy instance.

```powershell
Set-CsTeamsCallingPolicy -Identity Global -InboundPstnCallRoutingTreatment Unanswered
```

For more information, see [Set-CsTeamsCallingPolicy](/powershell/module/skype/set-csteamscallingpolicy).

## Inbound VoIP calls

This policy setting controls how inbound external TeamsVoIP calls should be routed.

You can configure this setting with the Teams admin center or by using PowerShell.

### Using the Teams admin center

1. In the left navigation of the Microsoft Teams admin center, click **Voice** > **Calling policies**.

1. Select the policy you would like to update or click **Add** to create a new policy.

1. For **Inbound external call routing**, you have the following options:

    - **Regular Incoming** The call will be routed per normal. No changes will be made to the default inbound routing. This is the default setting.
    - **Unanswered** The call will be routed according to the unanswered call forwarding settings set for that user.
    - **Voicemail** The call will be routed directly to voicemail and will not be shown to the user. If the called user doesn't have voicemail enabled, the call will be disconnected.

1. Click **Save**.

### Using PowerShell

For example, this script sets InboundFederatedCallRoutingTreatment to route external VoIP calls directly to voicemail for users in the Global (default) Teams Calling Policy instance.

```powershell
Set-CsTeamsCallingPolicy -Identity Global -InboundFederatedCallRoutingTreatment Voicemail
```

For more information, see [Set-CsTeamsCallingPolicy](/powershell/module/skype/set-csteamscallingpolicy).

## Related articles

[Set-CsTeamsCallingPolicy](/powershell/module/skype/set-csteamscallingpolicy)

[Configure calling policies in Microsoft Teams](teams-calling-policy.md)

[Block inbound calls in Microsoft Teams](block-inbound-calls.md)

[Configure call settings for your users](user-call-settings.md)

[Voice policies reference](settings-policies-reference.md#voice)
