---
title: "Remove-CsAddressBookConfiguration"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d634abc2-988a-48f9-ad11-903759516082
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Remove-CsAddressBookConfiguration
[]
 **In this article**
  
[Examples](#sectionSection0)
  
[Detailed Description](#sectionSection1)
  
[Input Types](#sectionSection2)
  
[Return Types](#sectionSection3)
  
Removes the specified collection of Address Book configuration settings. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsAddressBookConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]
```

## Examples
<a name="sectionSection0"> </a>

### EXAMPLE 1

In this example, the **Remove-CsAddressBookConfiguration** cmdlet is used to delete the Address Book configuration settings with the identity site:Redmond. Using the Identity parameter ensures that only the specified Address Book settings will be removed. 
  
```
Remove-CsAddressBookConfiguration -Identity site:Redmond
```

### EXAMPLE 2

In Example 2, all the Address Book setting collections configured at the site scope are removed. To do this, the **Get-CsAddressBookConfiguration** cmdlet is used to retrieve a collection of all the Address Book settings that have been configured at the site scope; this is done by using the Filter parameter and the filter value "site:*". The retrieved collection is then piped to the **Remove-CsAddressBookConfiguration** cmdlet, which removes all the items in that collection. 
  
```
Get-CsAddressBookConfiguration -Filter site:* | Remove-CsAddressBookConfiguration
```

### EXAMPLE 3

Example 3 removes all the Address Book settings in which change files are kept for less than 30 days. To carry out this task, the **Get-CsAddressBookConfiguration** cmdlet is used to return a collection of all the Address Book settings currently in use in the organization. This collection is then piped to the **Where-Object** cmdlet, which selects only those settings where the KeepDuration property is less than 30 days. (Note the syntax: 30., with a period following the number of days.) Finally, the filtered collection is piped to the **Remove-CsAddressBookConfiguration** cmdlet, which deletes each item in that collection. 
  
```
Get-CsAddressBookConfiguration | Where-Object {$_.KeepDuration -lt 30.} | Remove-CsAddressBookConfiguration
```

## Detailed Description
<a name="sectionSection1"> </a>

Address Book servers are intermediaries between AD DS and Lync Server. The Address Book server ensures that the user information stored in Lync Server is in synch with the user information stored in AD DS. This is done by periodically synching Address Book files with information stored in the User database.
  
In addition, Address Book servers periodically generate index files that are downloaded to computers running Lync Server. When a user searches for contacts, he or she either search through these index files or search the Address Book index files stored in the Central Management store.
  
Address Book servers are governed using Address Book configuration settings; these settings determine such things as how often Address Book files are synchronized with the user database and how often these Address Book index files are generated. When you install Lync Server, a set of global Address Book settings is created for you. You can also create custom configuration settings that can be applied to individual sites. These settings, if they exist, apply to any Address Book servers operating in the site, and take precedence over the global settings. 
  
The **New-CsAddressBookConfiguration** cmdlet enables you to create site-level Address Book configuration settings. To later remove Address Book settings configured at the site scope, use the **Remove-CsAddressBookConfiguration** cmdlet. Note that you can also run the **Remove-CsAddressBookConfiguration** cmdlet against the global settings; however, the global settings cannot actually be removed. Instead, running the **Remove-CsAddressBookConfiguration** cmdlet against the global settings will reset all of the global properties to their default values. 
  
Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsAddressBookConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt: 
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsAddressBookConfiguration"}
  
## Parameters
<a name="sectionSection1"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the collection of Address Book configuration settings to be removed. To remove the global collection, use the following syntax: -Identity global. (When you "remove" the global settings you simply reset all the properties to their default values.) To remove a site collection, use syntax similar to this: -Identity site:Redmond. Note that you cannot use wildcards when specifying a policy Identity.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="sectionSection2"> </a>

Microsoft.Rtc.Management.WritableConfig.Settings.AddressBook.AddressBookSettings object. The **Remove-CsAddressBookConfiguration** cmdlet accepts pipelined input of Address Book configuration objects. 
  
## Return Types
<a name="sectionSection3"> </a>

The **Remove-CsAddressBookConfiguration** cmdlet does not return a value or object. Instead, the cmdlet removes instances of the Microsoft.Rtc.Management.WritableConfig.Settings.AddressBook.AddressBookSettings object. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Get-CsAddressBookConfiguration](get-csaddressbookconfiguration.md)
  
[New-CsAddressBookConfiguration](new-csaddressbookconfiguration.md)
  
[Set-CsAddressBookConfiguration](set-csaddressbookconfiguration.md)

