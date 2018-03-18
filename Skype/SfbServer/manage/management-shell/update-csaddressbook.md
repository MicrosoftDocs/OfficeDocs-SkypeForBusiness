---
title: "Update-CsAddressBook"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 109c5fe7-0154-4161-b19f-01bab024bb3d
description: "Forces the specified Address Book servers to synchronize their contents with the User database. This cmdlet was introduced in Lync Server 2010."
---

# Update-CsAddressBook
 
Forces the specified Address Book servers to synchronize their contents with the User database. This cmdlet was introduced in Lync Server 2010.
  
```
Update-CsAddressBook [-Force <SwitchParameter>] [-Fqdn <Fqdn>]

```

## Examples

### EXAMPLE 1

In Example 1, the **Update-CsAddressBook** cmdlet is called without any parameters. This synchronizes all the Address Book servers in the organization.
  
```
Update-CsAddressBook
```

### EXAMPLE 2

In Example 2, only a single Address Book server is synchronized: the server with the FQDN atl-abs-001.litwareinc.com.
  
```
Update-CsAddressBook -Fqdn atl-abs-001.litwareinc.com
```

## Detailed Description

Address Book servers are intermediaries between Active Directory and Skype for Business Server 2015. The Address Book server ensures that the user information stored in Skype for Business Server 2015 is in synch with the user information stored in Active Directory. This is done by periodically synching Address Book files with the information stored in the User database. By default, this synchronization takes place every five minutes. (However, that time interval can be modified by using the **Set-CsAddressBookConfiguration** cmdlet.)
  
If you can't wait for synchronization to take place or if it appears that, for some reason, synchronization isn't taking place, you can use the **Update-CsAddressBook** cmdlet to force an Address Book server to immediately synch with the user information stored in the User database.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts or non-fatal error messages that might occur when you run the cmdlet.  <br/> |
| _Fqdn_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Enables you to specify an individual Address Book to be updated. If this parameter is not included then all of your Address Book servers will be synchronized with the User database. Individual Address Book servers should be referenced by their fully qualified domain name (FQDN); for example, atl-abs-001.litwareinc.com.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None. The **Update-CsAddressBook** cmdlet does not accept pipelined input.
  
## Return Types

None. Instead, the **Update-CsAddressBook** cmdlet updates existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.AddressBook.AddressBookSettings object.
  
## See also

#### 

[Get-CsAddressBookConfiguration](get-csaddressbookconfiguration.md)
  
[Test-CsAddressBookService](test-csaddressbookservice.md)
  
[Test-CsAddressBookWebQuery](test-csaddressbookwebquery.md)

