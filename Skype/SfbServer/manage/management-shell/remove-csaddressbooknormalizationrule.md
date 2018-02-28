---
title: "Remove-CsAddressBookNormalizationRule"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 708ebae7-59b2-4f33-a706-18a7237eccb0
description: "Removes an Address Book normalization rule. Address Book normalization rules are used to convert phone numbers to a format readily understood by Skype for Business Server 2015."
---

# Remove-CsAddressBookNormalizationRule
[]
Removes an Address Book normalization rule. Address Book normalization rules are used to convert phone numbers to a format readily understood by Skype for Business Server 2015.
  
This cmdlet was introduced in Skype for Business Server 2015.
  
```
Remove-CsAddressBookNormalizationRule -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 removes the Generic_All normalization rule from the global collection of Address Book normalization rules.
  
```
Remove-CsAddressBookNormalizationRule -Identity "Global/Generic_All"
```

### Example 2

In Example 2, all the normalization rules are removed from the collection of Address Book normalization rules assigned to the Redmond site. To do this, the Get-CsAddressBookNormalizationRule cmdlet is first used to retrieve all the rules assigned to the Redmond site. Those rules are then piped to, and deleted by, the Remove-CsAddressBookNormalizationRule cmdlet. When the command finishes running the normalization rules collection for the Redmond site will still exist, but the collection will no longer contain any rules.
  
```
Get-CsAddressBookNormalizationRule -Identity "site:Redmond" | Remove-CsAddressBookNormalizationRule
```

### Example 3

Example 3 removes all Address Book normalization rules where the Pattern property is equal to E164. To carry out this task, the command first uses Get-CsAddressBookNormalizationRule to return a collection of all the available normalization rules. That collection is then piped to the Where-Object cmdlet, which picks out only those rules where the Pattern property is equal to E164. Any rules that meet that criterion are then piped to the Remove-CsAddressBookNormalizationRule cmdlet and are deleted.
  
```
Get-CsAddressBookNormalizationRule | Where-Object {$_.Pattern -eq "E164"} | Remove-CsAddressBookNormalizationRule
```

## Detailed Description
<a name="DetailedDescription"> </a>

Normalization rules define the requirements for converting (or translating) numbers from an internal Skype for Business Server 2015 format to a standard (E.164) format. (Note that an understanding of regular expressions is helpful in order to understand what normalization rules do and how they do it.) The Address Book normalization rules handle these conversions and translations for the Address Book server.
  
Although Address Book normalization rules are very similar to voice normalization rules, the two are not interchangeable: you cannot add voice normalization rules to an Address Book collection, nor can you add Address Book normalization rules to a dial plan. That means, in some cases, you might need to create identical rules: one for assignment to Address Book server, the other for assignment to dial plans.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the rule being removed. The Identity specified must include the scope followed by a slash followed by the name; for example: site:Redmond/Rule1, where site:Redmond is the scope and Rule1 is the name.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The Remove-CsAddressBookNormalizationRule cmdlet accepts pipelined input of the Microsoft.Rtc.Management.WritableConfig.Settings.AddressBook.AddressBookNormalizationRule#Decorated object.
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the Remove-CsAddressBookNormalizationRule cmdlet deletes existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.AddressBook.AddressBookNormalizationRule#Decorated object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsAddressBookNormalizationRule](get-csaddressbooknormalizationrule.md)
#### 

[New-CsAddressBookNormalizationRule](new-csaddressbooknormalizationrule.md)
  
[Set-CsAddressBookNormalizationRule](set-csaddressbooknormalizationrule.md)

