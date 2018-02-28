---
title: "New-CsOutboundTranslationRule"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: aa6011e5-c48d-4fcc-ba65-bdec341234ed
description: "Creates a new outbound translation rule. An outbound translation rule converts phone numbers to the local dialing format for interaction with private branch exchange (PBX) systems. This cmdlet was introduced in Lync Server 2010."
---

# New-CsOutboundTranslationRule
[]
Creates a new outbound translation rule. An outbound translation rule converts phone numbers to the local dialing format for interaction with private branch exchange (PBX) systems. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsOutboundTranslationRule -Identity <XdsIdentity> <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

This example creates a new outbound translation rule for site Redmond named Prefix Redmond. Because no other parameters are specified, the rule is created with the default values. Notice that the value passed to the Identity parameter is in double-quotes; this is because the name of the rule (Prefix Redmond) contains a space. If the rule name does not contain a space you don't need to enclose the Identity in double quotes.
  
```
New-CsOutboundTranslationRule -Identity "site:Redmond/Prefix Redmond"
```

### EXAMPLE 2

This example creates a new global outbound translation rule named SeattleSevenDigit. (Note: Rather than specifying a Parent and a Name, we could have instead created this same rule by specifying -Identity global/SeattleSevenDigit.) We've included a Description explaining that this rule is for translating numbers in E.164 format to a seven-digit format. In addition, Pattern and Translation values have been specified. These values translate an E.164 number (in this case 12 digits beginning with +1425), specified by the regular expression in the Pattern, to a seven-digit number by removing the first five digits. For example, the number +14255551212 would be translated to the number 5551212.
  
```
New-CsOutboundTranslationRule -Parent global -Name SeattleSevenDigit -Description "Convert to seven digits" -Pattern '^\+1425(\d{7})$' -Translation '$1'
```

## Detailed Description

Call this cmdlet to create a new outbound translation rule. Skype for Business Server 2015 normalizes phone numbers to E.164 format. However, many private branch exchange (PBX) systems aren't able to work with this format. Outbound translations rules translate the number to the local dialing format prior to sending the number to the Mediation Server or gateway.
  
Each outbound translation rule is associated with a trunk configuration. More than one outbound translation rule can be associated with each configuration. Therefore, the Identity for each rule consists of a scope along with a name that is unique within the scope (in the format scope/name, for example site:Redmond/OBR1). The rule is automatically associated with the trunk configuration with the same scope. If you call the **New-CsOutboundTranslationRule** cmdlet and specify a scope at which a trunk configuration has not yet been defined, the trunk configuration will be created with the given scope, the outbound translation rule, and default values.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |A unique identifier for the outbound translation rule. The Identity includes the scope at which the rule is applied and the name of the rule, and must be at the global, site, or service (PSTNGateway only) scope. For example, site:Redmond/OutboundRule1 and PstnGateway:Redmond.litwareinc.com/OutboundRule2.  <br/> If the Identity parameter is specified, you cannot specify values for the Name or Parent parameters.  <br/> |
| _Name_ <br/> |Required  <br/> |System.String  <br/> |The name of the outbound translation rule. If no Name is supplied, an Identity consisting of a scope and name must be specified. If a Name is supplied, the Parent parameter is also required, but an Identity cannot be specified.  <br/> |
| _Parent_ <br/> |Required  <br/> |System.String  <br/> |The scope of the outbound translation rule. If a value is specified for this parameter, a value must also be specified for the Name parameter. However, the Identity parameter cannot be specified. If the Parent and Name parameters aren't specified, the Identity must be.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Description_ <br/> |Optional  <br/> |System.String  <br/> |A description of the outbound translation rule. This description will help identify the purpose of the rule.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching **Set-\<cmdlet\>**. <br/> |
| _Pattern_ <br/> |Optional  <br/> |System.String  <br/> |A regular expression representing the number pattern to which the Translation will be applied.  <br/> Default: ^\+(\d\*)$  <br/> |
| _Priority_ <br/> |Optional  <br/> |System.Int32  <br/> |If a number matches the Pattern of more than one outbound translation rule, rules are applied in priority order. Use this parameter to assign a priority to the rule.  <br/> |
| _Translation_ <br/> |Optional  <br/> |System.String  <br/> |A regular expression that will be applied to the number matching the Pattern to prepare that number for outbound routing.  <br/> Default: $1  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None.
  
## Return Types

This cmdlet creates an object of type Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.TranslationRule.
  
## See also

#### 

[Remove-CsOutboundTranslationRule](remove-csoutboundtranslationrule.md)
  
[Set-CsOutboundTranslationRule](set-csoutboundtranslationrule.md)
  
[Get-CsOutboundTranslationRule](get-csoutboundtranslationrule.md)

