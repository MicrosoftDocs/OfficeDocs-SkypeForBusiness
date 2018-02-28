---
title: "Remove-CsAddressBookNormalizationConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 06e27877-f9aa-4523-be6b-2f8345d8468e
description: "Deletes one or more collections of Address Book normalization configuration settings. Address Book normalization settings are used to convert phone numbers to a format readily understood by Skype for Business Server 2015."
---

# Remove-CsAddressBookNormalizationConfiguration
[]
Deletes one or more collections of Address Book normalization configuration settings. Address Book normalization settings are used to convert phone numbers to a format readily understood by Skype for Business Server 2015.
  
This cmdlet was introduced in Skype for Business Server 2015.
  
```
Remove-CsAddressBookNormalizationConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 deletes the Address Book normalization configuration settings currently applied to the Redmond site. After this collection has been deleted, Address Book servers in the Redmond site will use the global configuration settings to handle phone number normalization.
  
```
Remove-CsAddressBookNormalizationConfiguration -Identity "site:Redmond"
```

### Example 2

In Example 2, all the Address Book normalization configuration settings applied to the site scope are deleted. To do this, the command first uses the Get-CsAddressBookNormalizationConfiguration cmdlet and the Filter parameter to return a collection of all the configuration settings applied to the site scope. This collection is then piped to the Remove-CsAddressBookNormalizationConfiguration cmdlet, which removes each item in the collection. When this command completes, the deployment will be limited to the global collection of Address Book normalization settings.
  
```
Get-CsAddressBookNormalizationConfiguration -Filter "site:*" | Remove-CsAddressBookNormalizationConfiguration
```

## Detailed Description
<a name="DetailedDescription"> </a>

Normalization rules define the requirements for converting (or translating) numbers from an internal Skype for Business Server 2015 format to a standard (E.164) format. (Note that an understanding of regular expressions is helpful in order to understand what normalization rules do and how they do it.) In Skype for Business Server 2015, the Address Book normalization configuration settings represent collections of normalization rules that carry out these conversions and translations for Address Book servers. (These settings can be defined at the global scope or at the site scope.) The Remove-CsAddressBookNormalizationConfiguration cmdlet provides a way delete normalization rule configuration settings that have been configured at the site scope. This cmdlet can also be run against the global collection of settings. In that case, however, the global settings will not be removed; that's because the global collection cannot be deleted. However, all the properties in the global collection will be reset to their default values. That means that any custom rules you have created for the global collection will be deleted.
  
Although Address Book normalization rules are very similar to voice normalization rules, the two are not interchangeable: you cannot add voice normalization rules to an Address Book collection, nor can you add Address Book normalization rules to a dial plan. That means, in some cases, you might need to create identical rules: one for assignment to Address Book servers, the other for assignment to dial plans.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the collection of Address Book configuration settings to be removed. For example:  `-Identity "site:Redmond"` <br/> Note that you cannot use wildcards when specifying the collection to be removed.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The Remove-CsAddressBookNormalizationConfiguration cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.AddressBook.AddressBookNormalizationSettings object.
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the Remove-CsAddressBookNormalizationConfiguration cmdlet deletes existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.AddressBook.AddressBookNormalizationSettings object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsAddressBookNormalizationConfiguration](get-csaddressbooknormalizationconfiguration.md)
  
[New-CsAddressBookNormalizationConfiguration](new-csaddressbooknormalizationconfiguration.md)
  
[Set-CsAddressBookNormalizationConfiguration](set-csaddressbooknormalizationconfiguration.md)
#### 

[Import-CsCompanyPhoneNormalizationRules](import-cscompanyphonenormalizationrules.md)

