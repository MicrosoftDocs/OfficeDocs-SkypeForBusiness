---
title: "Set-CsVoiceNormalizationRule"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 68850abb-4ac7-4ae1-bb6e-d991385f92a4
description: "Modifies a voice normalization rule. Voice normalization rules are used to convert a telephone dialing requirement (for example, dialing 9 to access an outside line) to the E.164 phone number format used by Skype for Business Server 2015. This cmdlet was introduced in Lync Server 2010."
---

# Set-CsVoiceNormalizationRule
 
Modifies a voice normalization rule. Voice normalization rules are used to convert a telephone dialing requirement (for example, dialing 9 to access an outside line) to the E.164 phone number format used by Skype for Business Server 2015. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsVoiceNormalizationRule [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

This example sets the description of the rule Prefix Redmond on site Redmond to "Add a prefix to all numbers on site Redmond".
  
```
Set-CsVoiceNormalizationRule -Identity "site:Redmond/Prefix Redmond" -Description "Add a prefix to all numbers on site Redmond"
```

### EXAMPLE 2

This example modifies the voice normalization rule with the Identity global/SeattleFourDigit. A new Description has been specified to reflect the modifications to the rule. In addition, a Translation value has been specified that modifies the rule to translate any number matching the existing pattern of this rule to the same number but with the prefix +1206556. For example, if the existing pattern matched any four-digit number and the number 1234 were entered, this rule would translate that extension to the number +12065561234.
  
```
Set-CsVoiceNormalizationRule -Identity global/SeattleFourDigit -Description "Translate an internal four-digit extension" -Translation '+1206556$1'
```

### EXAMPLE 3

Example 3 changes the name of the normalization rule. Keep in mind that changing the name also changes the name portion of the Identity. The **Set-CsVoiceNormalizationRule** cmdlet doesn't have a Name parameter, so in order to change the name we first call the **Get-CsVoiceNormalizationRule** cmdlet to retrieve the rule with the Identity global/RedmondFourDigit and assign the returned object to the variable $a. We then assign the string RedmondRule to the Name property of the object. Next, we pass the variable to the Instance parameter of the **Set-CsVoiceNormalizationRule** cmdlet to make the change permanent.
  
```
$a = Get-CsVoiceNormalizationRule -Identity global/RedmondFourDigit
$a.name = "RedmondRule"
Set-CsVoiceNormalizationRule -Instance $a
```

## Detailed Description

This cmdlet modifies a named voice normalization rule. These rules are a required part of phone authorization and call routing. They define the requirements for converting (or translating) numbers from an internal Skype for Business Server 2015 format to a standard (E.164) format. An understanding of regular expressions is helpful in order to define number patterns that will be translated.
  
Rules that are modified by using this cmdlet are part of the dial plan and, in addition to being accessible through the **Get-CsVoiceNormalizationRule** cmdlet, can also be accessed through the NormalizationRules property returned by a call to the **Get-CsDialPlan** cmdlet.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Description_ <br/> |Optional  <br/> |System.String  <br/> |A friendly description of the normalization rule.  <br/> Maximum string length: 512 characters.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |A unique identifier for the rule. The Identity specified must include the scope followed by a slash followed by the name; for example: site:Redmond/Rule1, where site:Redmond is the scope and Rule1 is the name.  <br/> |
| _Instance_ <br/> |Optional  <br/> |NormalizationRule  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values. This object must be of type NormalizationRule and can be retrieved by calling the **Get-CsVoiceNormalizationRule** cmdlet. <br/> |
| _IsInternalExtension_ <br/> |Optional  <br/> |System.Boolean  <br/> |If True, the result of applying this rule will be a number internal to the enterprise. If False, applying the rule results in an external number. This value is ignored if the value of the OptimizeDeviceDialing property of the associated dial plan is set to False.  <br/> |
| _Pattern_ <br/> |Optional  <br/> |System.String  <br/> |A regular expression that the dialed number must match in order for this rule to be applied.  <br/> |
| _Priority_ <br/> |Optional  <br/> |System.Int32  <br/> |The order in which rules are applied. A number might match more than one rule. This parameter sets the order in which the rules are tested against the number.  <br/> |
| _Translation_ <br/> |Optional  <br/> |System.String  <br/> |The regular expression pattern that will be applied to the number to convert it to E.164 format.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _Tenant_ <br/> |Optional  <br/> |System.Guid  <br/> |PARAMVALUE: Guid  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.NormalizationRule object. The **Set-CsVoiceNormalizationRule** cmdlet accepts pipelined input of voice normalization rule objects.
  
## Return Types

The **Set-CsVoiceNormalizationRule** cmdlet does not return a value or object. Instead, the cmdlet configures instances of the Microsoft.Rtc.Management.WritableConfig.Policy.Voice.NormalizationRule object.
  
## See also

#### 

[New-CsVoiceNormalizationRule](new-csvoicenormalizationrule.md)
  
[Remove-CsVoiceNormalizationRule](remove-csvoicenormalizationrule.md)
  
[Get-CsVoiceNormalizationRule](get-csvoicenormalizationrule.md)
  
[Test-CsVoiceNormalizationRule](test-csvoicenormalizationrule.md)
  
[Set-CsDialPlan](set-csdialplan.md)
  
[Get-CsDialPlan](get-csdialplan.md)

