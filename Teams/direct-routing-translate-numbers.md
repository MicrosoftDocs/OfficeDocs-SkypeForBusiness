---
title: "Translate phone numbers for Direct Routing"
ms.reviewer: filippse
ms.author: crowe
author: CarolynRowe
manager: serdars
audience: ITPro
ms.topic: article
ms.service: msteams
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-voice
appliesto: 
  - Microsoft Teams
f1.keywords:
- NOCSH
description: "Learn how to configure Microsoft Phone System Direct Routing."
---

# Translate phone numbers to an alternate format

This article describes how to translate numbers for outbound and inbound calls to an alternate format. This is step 4 of the following steps for configuring Direct Routing:

- Step 1. [Connect the SBC with Microsoft Phone System and validate the connection](direct-routing-connect-the-sbc.md) 
- Step 2. [Enable users for Direct Routing, voice, and voicemail](direct-routing-enable-users.md)   
- Step 3. [Configure voice routing](direct-routing-voice-routing.md)
- **Step 4. Translate numbers to an alternate format**   (This article)

For information on all the steps required for setting up Direct Routing, see [Configure Direct Routing](direct-routing-configure.md).

Sometimes tenant administrators may want to change the number for outbound and/or inbound calls based on the patterns they created to ensure interoperability with Session Border Controllers (SBCs). This article describes how you can specify a Number Translation Rules policy to translate numbers to an alternate format. 

You can use the Number Translation Rules policy to translate numbers for the following:

- Inbound calls: Calls from a PSTN endpoint (caller) to a Teams client (callee)
- Outbound calls: Calls from a Teams client (caller) to a PSTN endpoint (callee)

The policy is applied at the SBC level. You can assign multiple translation rules to an SBC, which are applied in the order that they appear when you list them in PowerShell. You can also change the order of the rules in the policy.

To create, modify, view, and delete number manipulation rules, use the [New-CsTeamsTranslationRule](/powershell/module/skype/new-csteamstranslationrule), [Set-CsTeamsTranslationRule](/powershell/module/skype/set-csteamstranslationrule), [Get-CsTeamsTranslationRule](/powershell/module/skype/get-csteamstranslationrule), and [Remove-CsTeamsTranslationRule](/powershell/module/skype/remove-csteamstranslationrule) cmdlets.

To assign, configure, and list number manipulation rules on SBCs, use the [New-CSOnlinePSTNGateway](/powershell/module/skype/new-csonlinepstngateway) and [Set-CSOnlinePSTNGateway](/powershell/module/skype/set-csonlinepstngateway) cmdlets together with the InboundTeamsNumberTranslationRules, InboundPSTNNumberTranslationRules, OutboundTeamsNumberTranslationRules, and OutboundPSTNNumberTranslationRules parameters.

> [!NOTE]
> The maximum total number of translation rules is 400, maximum translation parameter name length is 100 symbols, maximum translation parameter pattern length is 1024 symbols, and maximum translation parameter translation length is 256 symbols.


## Example SBC configuration

For this scenario, the New-CsOnlinePSTNGateway cmdlet is run to create the following SBC configuration:

```PowerShell
New-CSOnlinePSTNGateway -Identity sbc1.contoso.com -SipSignalingPort 5061 –InboundTeamsNumberTranslationRules ‘AddPlus1’, ‘AddE164SeattleAreaCode’ -InboundPSTNNumberTranslationRules ‘AddPlus1’ -OutboundPSTNNumberTranslationRules ‘AddSeattleAreaCode’,‘StripPlus1’  -OutboundTeamsNumberTranslationRules ‘StripPlus1’
```

The translation rules assigned to the SBC are summarized in the following table:

|Name  |Pattern |Translation  |
|---------|---------|---------|
|AddPlus1     |^(\d{10})$          |+1$1          |
|AddE164SeattleAreaCode      |^(\d{4})$          | +1206555$1         |
|AddSeattleAreaCode    |^(\d{4})$          | 425555$1         |
|StripPlus1    |^+1(\d{10})$          | $1         |

In the following examples, there are two users, Alice and Bob. Alice is a Teams user whose number is +1 206 555 0100. Bob is a PSTN user whose number is +1 425 555 0100.

## Example 1: Inbound call to a ten-digit number

Bob calls Alice using a non-E.164 ten-digit number. Bob dials 2065550100 to reach Alice.
SBC uses 2065550100 in the RequestURI and To headers and 4255550100 in the From header.


|Header  |Original |Translated header |Parameter and rule applied  |
|---------|---------|---------|---------|
|RequestURI  |INVITE sip:2065550100@sbc.contoso.com|INVITE sip:+12065550100@sbc.contoso.com|InboundTeamsNumberTranslationRules ‘AddPlus1’|
|TO    |TO: \<sip:2065550100@sbc.contoso.com>|TO: \<sip:+12065550100@sbc.contoso.com>|InboundTeamsNumberTranlationRules ‘AddPlus1’|
|FROM   |FROM: \<sip:4255550100@sbc.contoso.com>|FROM: \<sip:+14255550100@sbc.contoso.com>|InboundPSTNNumberTranslationRules ‘AddPlus1’|

## Example 2: Inbound call to a four-digit number

Bob calls Alice using a four-digit number. Bob dials 0100 to reach Alice.
SBC uses 0100 in the RequestURI and To headers and 4255550100 in the From header.


|Header  |Original |Translated header |Parameter and rule applied  |
|---------|---------|---------|---------|
|RequestURI  |INVITE sip:0100@sbc.contoso.com          |INVITE sip:+12065550100@sbc.contoso.com           |InboundTeamsNumberTranlationRules ‘AddE164SeattleAreaCode’        |
|TO    |TO: \<sip:0100@sbc.contoso.com>|TO: \<sip:+12065550100@sbc.contoso.com>|InboundTeamsNumberTranlationRules ‘AddE164SeattleAreaCode’         |
|FROM   |FROM: \<sip:4255550100@sbc.contoso.com>|FROM: \<sip:+14255550100@sbc.contoso.com>|InboundPSTNNumberTranlationRules ‘AddPlus1’        |

## Example 3: Outbound call using a ten-digit non-E.164 number

Alice calls Bob using a ten-digit number. Alice dials 425 555 0100 to reach Bob.
SBC is configured to use non-E.164 ten-digit numbers for both Teams and PSTN users.

In this scenario, a dial plan translates the number before sending it to the Direct Routing interface. When Alice enters 425 555 0100 in the Teams client, the number is translated to +14255550100 by the country dial plan. The resulting numbers are a cumulative normalization of the dial plan rules and Teams translation rules. The Teams translation rules remove the "+1" that was added by the dial plan.


|Header  |Original |Translated header |Parameter and rule applied  |
|---------|---------|---------|---------|
|RequestURI  |INVITE sip:+14255550100@sbc.contoso.com          |INVITE sip:4255550100@sbc.contoso.com       |OutboundPSTNNumberTranlationRules ‘StripPlus1’         |
|TO    |TO: \<sip:+14255550100@sbc.contoso.com>|TO: \<sip:4255555555@sbc.contoso.com>|OutboundPSTNNumberTranlationRules ‘StripPlus1’       |
|FROM   |FROM: \<sip:+12065550100@sbc.contoso.com>|FROM: \<sip:2065550100@sbc.contoso.com>|OutboundTeamsNumberTranlationRules ‘StripPlus1’         |

## Example 4: Outbound call using a four-digit non-E.164 number

Alice calls Bob using a four-digit number. Alice uses 0100 to reach Bob from Calls or by using a contact.
SBC is configured to use non-E.164 four-digit numbers for Teams users and ten-digit numbers for PSTN users. The dial plan isn't applied in this scenario.


|Header  |Original |Translated header |Parameter and rule applied  |
|---------|---------|---------|---------|
|RequestURI  |INVITE sip:0100@sbc.contoso.com           |INVITE sip:4255550100@sbc.contoso.com       |InboundTeamsNumberTranlationRules ‘AddSeattleAreaCode’         |
|TO    |TO: \<sip:0100@sbc.contoso.com>|TO: \<sip:4255555555@sbc.contoso.com>|InboundTeamsNumberTranlationRulesList ‘AddSeattleAreaCode’       |
|FROM   |FROM: \<sip:+12065550100@sbc.contoso.com>|FROM: \<sip:2065550100@sbc.contoso.com>| InboundPSTNNumberTranlationRules ‘StripPlus1’ |

## See also

[Plan Direct Routing](direct-routing-plan.md)

[Configure Direct Routing](direct-routing-configure.md)
