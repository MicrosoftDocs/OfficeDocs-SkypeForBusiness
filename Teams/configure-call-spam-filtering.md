---
title: 'Configure spam filtering for calls in Microsoft Teams'
author: mkbond007
ms.author: mabond
manager: pamgreen
ms.topic: conceptual
ms.service: msteams
ms.reviewer: roykuntz
ms.date: 02/26/2024
audience: admin
search.appverid: MET150
description: Learn how to configure spam filtering for calls in Microsoft Teams.
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

# Configure spam filtering for calls in Microsoft Teams

In Microsoft Teams, admins can configure spam filtering for inbound calls from the Public Switched Telephone Network (PSTN). Teams can detect potential spam calls and notify users with a "Spam Likely" notification.

Spam filtering for calls isn't the same as blocking inbound calls. For more information, see [Block inbound calls](block-inbound-calls.md).

## Using the Teams admin center

This setting allows you to control the type of spam filtering available on incoming calls. This setting is on by default. This setting has three options:

- **On** Spam filtering is fully enabled. Both Basic and Captcha Interactive Voice Response (IVR) checks are performed. In case the call is considered as spam, the user gets a "Spam Likely" notification in Teams.
- **On without IVR** Spam Filtering is partially enabled. Captcha IVR checks are disabled. A "Spam Likely" notification appears. A call might get dropped if it gets a high score from Basic checks.
- **Off** Spam filtering is disabled. No checks are performed. A "Spam Likely" notification doesn't appear.

## Using PowerShell

To configure spam filtering for calls in Teams, use the `-SpamFilteringEnabledType` parameter with the following cmdlets:

- [Get-CsTeamsCallingPolicy](/powershell/module/skype/get-csteamscallingpolicy)
- [New-CsTeamsCallingPolicy](/powershell/module/skype/new-csteamscallingpolicy)
- [Set-CsTeamsCallingPolicy](/powershell/module/skype/set-csteamscallingpolicy)
- [Remove-CsTeamsCallingPolicy](/powershell/module/skype/remove-csteamscallingpolicy)
- [Grant-CsTeamsCallingPolicy](/powershell/module/skype/grant-csteamscallingpolicy)

For example, this script enables spam detection for the global policy:

```powershell
Set-CsTeamsCallingPolicy -Identity Global -SpamFilteringEnabledType Enabled
```

## Related articles

[Block inbound calls](block-inbound-calls.md)

[Routing inbound calls](inbound-call-routing.md)

[Configure calling policies in Microsoft Teams](teams-calling-policy.md)
