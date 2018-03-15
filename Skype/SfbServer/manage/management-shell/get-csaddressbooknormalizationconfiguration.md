---
title: "Get-CsAddressBookNormalizationConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 617d5113-b396-4e4b-96e4-e73fcfde8d57
description: "Returns the Address Book normalization configuration settings currently in use in the organization. Address Book normalization settings are used to convert phone numbers to a format readily understood by Skype for Business Server 2015."
---

# Get-CsAddressBookNormalizationConfiguration
 
Returns the Address Book normalization configuration settings currently in use in the organization. Address Book normalization settings are used to convert phone numbers to a format readily understood by Skype for Business Server 2015.
  
This cmdlet was introduced in Skype for Business Server 2015.
  
```
Get-CsAddressBookNormalizationConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 returns a collection of all the Address Book normalization configuration settings currently in use in the organization. This is done by calling the Get-CsAddressBookNormalizationConfiguration cmdlet without any additional parameters.
  
```
Get-CsAddressBookNormalizationConfiguration
```

### Example 2

In Example 2, information is returned for a single collection of normalization rules: the collection with the Identity site:Redmond:
  
```
Get-CsAddressBookNormalizationConfiguration -Identity "site:Redmond"
```

### Example 3

Example 3 returns information about all the normalization configuration settings applied to the site scope. To do this, the command uses the Filter parameter and the parameter value "site:\*". That syntax limits the returned data to all the collections that have an Identity that begins with the string value "site:".
  
```
Get-CsAddressBookNormalizationConfiguration -Filter "site:*"
```

## Detailed Description
<a name="DetailedDescription"> </a>

Normalization rules define the requirements for converting (or translating) numbers from an internal Skype for Business Server 2015 format to the standard (E.164) format. (Note that an understanding of regular expressions is helpful in order to understood what normalization rules do and how they work.) In Skype for Business Server 2015, the Address Book normalization configuration settings represent collections of normalization created for use by the Address Book server. (These collections can be defined at the global scope or at the site scope.) The Get-CsAddressBookNormalizationConfiguration cmdlet provides a way to return information about the Address Book normalization rules currently in use in your organization.
  
Although Address Book normalization rules are very similar to voice normalization rules, the two are not interchangeable: you cannot add voice normalization rules to an Address Book collection, nor can you add Address Book normalization rules to a dial plan. That means that, in some cases, you might need to create identical rules: one for assignment to Address Book servers, the other for assignment to dial plans.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcard characters in order to return a collection (or multiple collections) of Address Book normalization configuration settings. For example, to return a collection of all the settings configured at the site scope, use this syntax:  `-Filter "site:*"` <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the collection of Address Book normalization configuration settings to be returned. To refer to the global settings, use this syntax:  `-Identity global` <br/> To refer to a collection configured at the site scope, use syntax similar to this:  `-Identity "site:Redmond"` <br/> Note that you cannot use wildcards when specifying an Identity. If you need to use wildcards, use the Filter parameter instead.  <br/> If this parameter is not specified, then the Get-CsAddressBookNormalizationConfiguration cmdlet returns a collection of all the Address Book normalization configuration settings in use in the organization.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the Address Book normalization configuration data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The Get-CsAddressBookNormalizationConfiguration cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The Get-CsAddressBookNormalizationConfiguration cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.AddressBook.AddressBookNormalizationSettings object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[New-CsAddressBookNormalizationConfiguration](new-csaddressbooknormalizationconfiguration.md)
  
[Remove-CsAddressBookNormalizationConfiguration](remove-csaddressbooknormalizationconfiguration.md)
  
[Set-CsAddressBookNormalizationConfiguration](set-csaddressbooknormalizationconfiguration.md)
#### 

[Import-CsCompanyPhoneNormalizationRules](import-cscompanyphonenormalizationrules.md)

