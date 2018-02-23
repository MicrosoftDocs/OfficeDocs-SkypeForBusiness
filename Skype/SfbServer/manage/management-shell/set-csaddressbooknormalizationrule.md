---
title: "Set-CsAddressBookNormalizationRule"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f06f3a1c-b1ce-4bc7-809a-a1b25c46e308
description: "Modifies an existing Address Book normalization rule. Address Book normalization settings are used to convert phone numbers to a format readily understood by Skype for Business Server 2015."
---

# Set-CsAddressBookNormalizationRule
[]
Modifies an existing Address Book normalization rule. Address Book normalization settings are used to convert phone numbers to a format readily understood by Skype for Business Server 2015.
  
This cmdlet was introduced in Skype for Business Server 2015.
  
```
Set-CsAddressBookNormalizationRule [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 changes the priority of the RedmondAddresses normalization rule found in the global collection of Address Book normalization rules.
  
```
Set-CsAddressBookNormalizationRule -Identity "Global/RedmondAddresses" -Priority 1
```

### Example 2

In Example 2, all the normalization rules that use the Translation +12065556$1 are updated to use the Translation +14255556$1; this might be required if an area code changes from 206 to 425. To carry out this task, the Get-CsAddressBookNormalizationRule cmdlet is called in order to return a collection of all the available normalization rules. This collection is then piped to the Where-Object cmdlet, which picks out only those rules that have a Translation equal to +12065556$1. Those rules are then piped to the Set-CsAddressBookTranslationRule, which changes the Translation for each of these rules to +14255556$1.
  
```
Get-CsAddressBookNormalizationRule | Where-Object {$_.Translation -eq '+1206556$1'} Set-CsAddressBookNormalizationRule -Translation '+1425556$1'
```

## Detailed Description
<a name="DetailedDescription"> </a>

Normalization rules define the requirements for converting (or translating) numbers from an internal Skype for Business Server 2015 format to a standard (E.164) format. (Note that an understanding of regular expressions is helpful in order to understand what normalization rules do and how they do it.) Address Book normalization rules carry out these conversions and translations for Address Book servers.
  
Although Address Book normalization rules are very similar to voice normalization rules, the two are not interchangeable: you cannot add voice normalization rules to an Address Book collection, nor can you add Address Book normalization rules to a dial plan. That means, in some cases, you might need to create identical rules: one for assignment to Address Book servers, the other for assignment to dial plans.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Description_ <br/> |Optional  <br/> |System.String  <br/> |Enables administrators to provide explanatory text that accompanies a normalization rule. For example, the Description might explain how the rule converts phone numbers.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |A unique identifier for the rule. The Identity specified must include the scope followed by a slash followed by the name; for example: site:Redmond/Rule1, where site:Redmond is the scope and Rule1 is the name.  <br/> |
| _Instance_ <br/> |Optional  <br/> |System.Management.Automation.PSObject  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _Pattern_ <br/> |Optional  <br/> |System.String  <br/> |A regular expression that the phone number must match in order for this rule to be applied.  <br/> The default value is ^(\d{11})$. This represents any set of numbers up to 11 digits.  <br/> |
| _Priority_ <br/> |Optional  <br/> |System.Int32  <br/> |The order in which rules are applied; this is required because a given phone number might match more than one rule. The Priority parameter sets the order in which the rules are tested against a number. If a phone number matches multiple rules, the rule with the highest priority will be selected to do the conversion.  <br/> Note that, when you set a priority, any existing rules will renumber themselves accordingly.  <br/> |
| _Translation_ <br/> |Optional  <br/> |System.String  <br/> |The regular expression pattern that will be applied to the number to convert it to E.164 format.  <br/> The default value is +$. This prefixes the number with a plus sign (+).  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The Set-CsAddressBookNormalizationRule cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.AddressBook.AddressBookNormalizationRule#Decorated object.
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the Set-CsAddressBookNormalizationRule cmdlet modifies existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.AddressBook.AddressBookNormalizationRule#Decorated object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsAddressBookNormalizationRule](get-csaddressbooknormalizationrule.md)
#### 

[New-CsAddressBookNormalizationRule](new-csaddressbooknormalizationrule.md)
  
[Remove-CsAddressBookNormalizationRule](remove-csaddressbooknormalizationrule.md)

