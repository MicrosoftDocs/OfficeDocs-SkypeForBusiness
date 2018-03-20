---
title: "New-CsAddressBookNormalizationConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: f73862d8-7382-4502-a9fa-3cfdab5f7207
description: "Creates a new collection of Address Book normalization configuration settings. Address Book normalization settings are used to convert phone numbers to a format readily understood by Skype for Business Server 2015."
---

# New-CsAddressBookNormalizationConfiguration
 
Creates a new collection of Address Book normalization configuration settings. Address Book normalization settings are used to convert phone numbers to a format readily understood by Skype for Business Server 2015.
  
This cmdlet was introduced in Skype for Business Server 2015.
  
```
New-CsAddressBookNormalizationConfiguration -Identity <XdsIdentity> [-AddressBookNormalizationRules <PSListModifier>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Exercise 1 creates a new set of Address Book normalization configuration settings assigned to the Redmond site. Note that this collection will not contain any Address Book normalization rules. Those rules are most-easily created using the New-CsAddressBookNormalizationRule cmdlet after the new settings collection is in place.
  
```
New-CsAddressBookNormalizationConfiguration -Identity "site:Redmond"
```

## Detailed Description
<a name="DetailedDescription"> </a>

Normalization rules define the requirements for converting (or translating) numbers from an internal Skype for Business Server 2015 format to a standard (E.164) format. (Note that an understanding of regular expressions is helpful in order to understand what normalization rules do and how they do it.) In Skype for Business Server 2015, the Address Book normalization configuration settings represent collections of normalization rules that carry out these conversions and translations for Address Book servers. (These settings can be defined at the global scope or at the site scope.) The New-CsAddressBookNormalizationConfiguration cmdlet provides a way create new collections scoped to a specified site.
  
In general, you will typically find it easier to add rules to a new collection by using the New-CsAddressBookNormalizationRule cmdlet; that cmdlet enables you to add a rule by using one simple command. However, you cannot add a rule to a collection until you have first used the New-CsAddressBookNormalizationConfiguration cmdlet to create that collection.
  
Although Address Book normalization rules are very similar to voice normalization rules, the two are not interchangeable: you cannot add voice normalization rules to an Address Book collection, nor can you add Address Book normalization rules to a dial plan. That means that, in some cases, you might need to create identical rules: one for assignment to Address Book servers, the other for assignment to dial plans.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the new collection of Address Book normalization rules. Because new rule collections can only be created at the site scope, the Identity will always be similar to this:  `-Identity "site:Redmond"` <br/> |
| _AddressBookNormalizationRules_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |One or more normalization rules to be assigned to the collection. Although these rules can be created directly using the New-CsAddressBookNormalizationConfiguration cmdlet, it is recommended that you create the normalization rules using the New-CsAddressBookNormalizationRule cmdlet instead. That cmdlet creates the rule and assigns it to the specified collection using a single command, and using much simpler syntax.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching **Set-\<cmdlet\>**. <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The New-CsAddressBookNormalizationConfiguration cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The New-CsAddressBookNormalizationConfiguration cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.AddressBook.AddressBookNormalizationSettings object cmdlet.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsAddressBookNormalizationConfiguration](get-csaddressbooknormalizationconfiguration.md)
  
[Remove-CsAddressBookNormalizationConfiguration](remove-csaddressbooknormalizationconfiguration.md)
  
[Set-CsAddressBookNormalizationConfiguration](set-csaddressbooknormalizationconfiguration.md)
#### 

[Import-CsCompanyPhoneNormalizationRules](import-cscompanyphonenormalizationrules.md)

