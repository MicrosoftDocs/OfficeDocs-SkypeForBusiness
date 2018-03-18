---
title: "Get-CsAddressBookConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 07757a19-f819-4d65-82da-50bf2f157a9b
description: "Returns information about Address Book configuration settings. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsAddressBookConfiguration
 
Returns information about Address Book configuration settings. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsAddressBookConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

Example 1 returns information about all the Address Book configuration settings in use in your organization. This is the default behavior if you call the **Get-CsAddressBookConfiguration** cmdlet without any additional parameters.
  
```
Get-CsAddressBookConfiguration
```

### EXAMPLE 2

Example 2 returns information for the Address Book configuration settings with the Identity site:Redmond.
  
```
Get-CsAddressBookConfiguration -Identity site:Redmond
```

### EXAMPLE 3

In this example, the Filter parameter and the filter value "site:\*" are used to return information about all the Address Book configuration settings that have been applied at the site scope. The supplied filter value returns information for all the Address Book settings that have an Identity that begins with the string value "site:".
  
```
Get-CsAddressBookConfiguration -Filter site:*
```

### EXAMPLE 4

In Example 4, information is returned for all the Address Book configuration settings where the settings uses normalization rules when parsing phone numbers. To do this, the command first uses the **Get-CsAddressBookConfiguration** cmdlet to return a collection of all the Address Book settings in the organization. That collection is then piped to the **Where-Object** cmdlet, which selects only those settings where the UseNormalizationRules property is equal to True.
  
```
Get-CsAddressBookConfiguration | Where-Object {$_.UseNormalizationRules -eq $True}
```

## Detailed Description

Address Book servers are intermediaries between Active Directory Domain Services and Skype for Business Server 2015. The Address Book server ensures that the user information stored in Skype for Business Server 2015 is in synch with the user information stored in Active Directory. This is done by periodically synching Address Book files with information stored in the User database.
  
In addition, Address Book servers periodically generate index files that are downloaded to computers running Skype for Business. When a user searches for contacts, he or she either search through these index files or search the Address Book index files stored in the Central Management store.
  
Address Book servers are governed using Address Book configuration settings; these settings determine such things as how often Address Book files are synchronized with the user database and how often these Address Book index files are generated. When you install Skype for Business Server 2015, a set of global Address Book settings is created for you. You can also create custom configuration settings that can be applied to individual sites. These settings, if they exist, apply to any Address Book servers operating in the site, and take precedence over the global settings. 
  
You can use the **Get-CsAddressBookConfiguration** cmdlet to return information about any (or all) of the Address Book settings currently in use in your organization.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcard characters in order to return a collection (or multiple collections) of Address Book settings. For example, to return a collection of all the settings configured at the site scope, use this syntax:  `-Filter site:*`. To return a collection of all the settings that have the string value "EMEA" somewhere in their Identity, use this syntax:  `-Filter *EMEA*`.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the collection of Address Book settings to be returned. To refer to the global settings, use this syntax:  `-Identity global`. To refer to a collection configured at the site scope, use syntax similar to this:  `-Identity site:Redmond.` <br/> Note that you cannot use wildcards when specifying an Identity. If you need to use wildcards, then include the Filter parameter instead.  <br/> If this parameter is not specified, then the **Get-CsAddressBookConfiguration** cmdlet returns a collection of all the Address Book settings in use in the organization. <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the Address Book configuration data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None. The **Get-CsAddressBookConfiguration** cmdlet does not accept pipelined input.
  
## Return Types

The **Get-CsAddressBookConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.AddressBook.AddressBookSettings object.
  
## See also

#### 

[New-CsAddressBookConfiguration](new-csaddressbookconfiguration.md)
  
[Remove-CsAddressBookConfiguration](remove-csaddressbookconfiguration.md)
  
[Set-CsAddressBookConfiguration](set-csaddressbookconfiguration.md)

