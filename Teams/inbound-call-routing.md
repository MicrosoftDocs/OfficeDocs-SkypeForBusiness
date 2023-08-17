---
title: 'Routing inbound calls in Microsoft Teams'
author: mkbond007
ms.author: mabond
manager: serdars
ms.topic: conceptual
ms.service: msteams
ms.reviewer: jenstr
ms.date: 06/28/2023
audience: admin
search.appverid: MET150
description: Learn how to route inbound PSTN & federated calls in Microsoft Teams.
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

# Routing inbound calls

This article describes how to route incoming calls that come from the Public Switched Telephone Network (PSTN) or calls that are federated.

Federated calls are calls that don't originate from the PSTN and that are outside your tenant. For example, a call from Teams or Skype for Business that is from another tenant would be considered federated. However, a Teams or Skype for Business (Online or on premises) call made within the same tenant wouldn't be considered a federated call.

As an admin, you can create policies that help prevent your users from getting unwanted calls from external parties. You can control whether these external calls should always be sent to voicemail, sent to unanswered settings, or use normal call routing. For PSTN calls, you can also allow your users within the policy to decide.

This article applies to Microsoft Calling Plans, Operator Connect, Teams Phone Mobile, and Direct Routing. These policy settings are also available for GCCH & DoD use.

## Routing for PSTN calls

This policy setting controls how inbound PSTN calls should be routed.

You can configure this setting by using the Teams admin center or PowerShell.

If **Use unanswered settings** or **Send to voicemail** is used, either of these settings will have precedence over other call forwarding settings like call forwarding with simultaneous ringing to delegate, call groups, or call forwarding.

### Using the Teams admin center

1. In the left navigation of the Microsoft Teams admin center, click **Voice** > **Calling policies**.

1. Select the policy you would like to update or click **Add** to create a new policy.

1. For **Routing for PSTN calls**, you have the following options:

    - **Use default settings** The call is routed using your default inbound call routing settings. This is the default setting.
    - **Use unanswered settings** The call is routed according to the unanswered call forwarding settings set for that user.
    - **Send to voicemail** The call is routed directly to voicemail and isn't shown to the user. If the called user doesn't have voicemail enabled, the call will be disconnected.
    - **Let users decide** The call is routed as **Use default settings**.

1. Click **Save**.

### Using PowerShell

For example, this script sets InboundPstnCallRoutingTreatment to route inbound PSTN calls according to the unanswered call forwarding settings for users in the Global (default) Teams Calling Policy instance.

```powershell
Set-CsTeamsCallingPolicy -Identity Global -InboundPstnCallRoutingTreatment Unanswered
```

For more information, see [Set-CsTeamsCallingPolicy](/powershell/module/skype/set-csteamscallingpolicy).

## Routing for federated calls

This policy setting controls how inbound federated calls should be routed.

You can configure this setting by using the Teams admin center or PowerShell.

If **Unanswered** or **Send to voicemail** is used, either of these settings will have precedence over other call forwarding settings like call forwarding with simultaneous ringing to delegate, call groups, or call forwarding.

### Using the Teams admin center

1. In the left navigation of the Microsoft Teams admin center, click **Voice** > **Calling policies**.

1. Select the policy you would like to update or click **Add** to create a new policy.

1. For **Routing for federated calls**, you have the following options:

    - **Use default settings** The call is routed using your default inbound call routing settings. This is the default setting.
    - **Use unanswered settings** The call is routed according to the unanswered call forwarding settings set for that user.
    - **Send to voicemail** The call is routed directly to voicemail and isn't shown to the user. If the called user doesn't have voicemail enabled, the call will be disconnected.

1. Click **Save**.

### Using PowerShell

For example, this script sets InboundFederatedCallRoutingTreatment to route inbound federated calls directly to voicemail for users in the Global (default) Teams Calling Policy instance.

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
