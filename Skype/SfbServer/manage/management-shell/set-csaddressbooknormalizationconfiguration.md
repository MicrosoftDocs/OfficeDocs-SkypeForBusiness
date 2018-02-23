---
title: "Set-CsAddressBookNormalizationConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b7d38f99-311d-4e86-b8a4-a8301bb547e0
description: "Modifies one or more collections of Address Book normalization configuration settings. Address Book normalization settings are used to convert phone numbers to a format readily understood by Skype for Business Server 2015."
---

# Set-CsAddressBookNormalizationConfiguration
[]
Modifies one or more collections of Address Book normalization configuration settings. Address Book normalization settings are used to convert phone numbers to a format readily understood by Skype for Business Server 2015.
  
This cmdlet was introduced in Skype for Business Server 2015.
  
```
Set-CsAddressBookNormalizationConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

The commands shown in Example 1 remove the Address Book normalization rule LongDistanceRule from the global collection of Address Book normalization configuration settings. In order to carry out this task, the first command in the example uses the Get-CsAddressBookNormalizationRule cmdlet to create an object reference to the normalization rule with the Identity global/LongDistanceRule. The resulting object reference is stored in a variable named $x.
  
The second command in the example then uses the Set-CsAddressBookNormalizationConfiguraton cmdlet to remove the rule global/LongDistanceRule from the global collection. This is done by including the AddressBookNormalizationRules parameter and the syntax  `@{Remove=$x}.`
  
```
$x = Get-CsAddressBookNormalizationRule -Identity "global/LongDistanceRule"
Set-CsAddressBookNormalizationConfiguration -Identity "global" -AddressBookNormalizationRules @{Remove=$x}

```

Alternatively, you could remove the rule by using the Remove-CsAddressBookNormalizationRule cmdlet
  
```
Remove-CsAddressBookNormalizationRule -Identity "global/LongDistanceRule"
```

### Example 2

The commands shown in Example 2 demonstrate how you can use the Set-CsAddressBookNormalizationConfiguration cmdlet to copy an Address Book normalization rule from one collection to another. To do this, the first command in the example uses the Get-CsAddressBookNormalizationRule cmdlet to create an object reference to the normalization rule with the Identity global/LongDistanceRule. The resulting object reference is stored in a variable named $x.
  
The second command in the example then uses the Set-CsAddressBookNormalizationConfiguration cmdlet to add this same rule to the configuration settings applied to the Redmond site. This is done by first connecting to the configuration settings for the Redmond site, then using the AddressBookNormalizationRules parameter and the syntax  `@{Add=$x}`. When this command finishes running, both the global collection and the Redmond site collection will have a normalization rule named LongDistanceRule.
  
```
$x = Get-CsAddressBookNormalizationRule -Identity "global/LongDistanceRule"
Set-CsAddressBookNormalizationConfiguration -Identity "site:Redmond" -AddressBookNormalizationRules @{Add=$x}

```

### Example 3

In Example 3, all the Address Book normalization rules assigned to the Redmond site are deleted; this is done by setting the AddressBookNormalizationRules parameter to a null value ($Null). Note that the Redmond site collection will still exist. However, no normalization rules will be assigned to that collection.
  
```
Set-CsAddressBookNormalizationConfiguration -Identity "site:Redmond" -AddressBookNormalizationRules $Null

```

## Detailed Description
<a name="DetailedDescription"> </a>

Normalization rules define the requirements for converting (or translating) numbers from an internal Skype for Business Server 2015 format to a standard (E.164) format. (Note that an understanding of regular expressions is helpful in order to understand what normalization rules do and how they do it.) In Skype for Business Server 2015, the Address Book normalization configuration settings represent collections of normalization rules designed to carry out these conversions and translations for Address Book server. (These collections can be defined at the global scope or at the site scope.) The Set-CsAddressBookNormalizationConfiguration cmdlet provides a way add or remove a normalization rule from any of these collections.
  
In general, you will probably find it easier to add or remove rules by using the CsAddressBookNormalizationRule cmdlets; these cmdlets enable you to add or remove rules using one command rather than two. However, as Example 2 shows, the Set-CsAddressBookNormalizationConfiguration cmdlet does enable you to copy rules from one collection to another.
  
Although Address Book normalization rules are very similar to voice normalization rules, the two are not interchangeable: you cannot add voice normalization rules to an Address Book collection, nor can you add Address Book normalization rules to a dial plan. That means that, in some cases, you might need to create identical rules: one for assignment to Address Book servers, the other for assignment to dial plans.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _AddressBookNormalizationRules_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |A set of normalization rules that have been applied to this collection of Address Book normalization configuration settings.  <br/> While this set of rules can be modified directly using this cmdlet, it is recommended that you create normalization rules with the New-CsAddressBookNormalizationRule cmdlet; this cmdlet creates the rule and assigns it to the specified collection. You can then modify those rules by using the Set-CsAddressBookNormalizationRule cmdlet, or delete a rule from a collection by using the Remove-CsAddressBookNormalizationRule cmdlet. In general, this is easier and less error-prone than trying to modify a rules collection by using the Set-CsAddressBookNormalizationConfiguration cmdlet and the AddressBookNormalizationRules parameter.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts before making changes.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the collection of Address Book normalization configuration settings to be modified. To refer to the global settings, use this syntax:  `-Identity "global"` <br/> To refer to a collection configured at the site scope, use syntax similar to this:  `-Identity "site:Redmond"` <br/> Note that you cannot use wildcards when specifying an Identity.  <br/> |
| _Instance_ <br/> |Optional  <br/> |System.Management.Automation.PSObject  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The Set-CsAddressBookNormalizationConfiguration cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.AddressBook.AddressBookNormalizationSettings object.
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the Set-CsAddressBookNormalizationConfiguration cmdlet modifies existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.AddressBook.AddressBookNormalizationSettings object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsAddressBookNormalizationConfiguration](get-csaddressbooknormalizationconfiguration.md)
  
[New-CsAddressBookNormalizationConfiguration](new-csaddressbooknormalizationconfiguration.md)
  
[Remove-CsAddressBookNormalizationConfiguration](remove-csaddressbooknormalizationconfiguration.md)
#### 

[Import-CsCompanyPhoneNormalizationRules](import-cscompanyphonenormalizationrules.md)

