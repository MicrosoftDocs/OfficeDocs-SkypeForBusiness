---
title: "Remove-CsUserServicesConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8eed6091-ab96-49d4-a0c0-d1f9180a0b90
description: "Removes an existing collection of User Services configuration settings. The User Services service is used to help maintain presence information and manage conferencing. This cmdlet was introduced in Lync Server 2010."
---

# Remove-CsUserServicesConfiguration
 
Removes an existing collection of User Services configuration settings. The User Services service is used to help maintain presence information and manage conferencing. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsUserServicesConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 removes the User Services configuration settings from the Redmond site (-Identity site:Redmond). 
  
```
Remove-CsUserServicesConfiguration -Identity site:Redmond
```

### EXAMPLE 2

In Example 2, all the User Services configuration settings that have been applied at the service scope are deleted. To do this, the command calls the **Get-CsUserServicesConfiguration** cmdlet along with the Filter parameter. The filter value "service:*" limits returned data to settings configured at the service scope (that is, settings that have an Identity that begins with the characters "service:"). This filtered collection is then piped to the **Remove-CsUserServicesConfiguration** cmdlet, which deletes each item in the collection.
  
```
Get-CsUserServicesConfiguration -Filter "service:*:" | Remove-CsUserServicesConfiguration
```

### EXAMPLE 3

Example 3 removes all the User Services configuration settings that allow users to have more than 250 contacts. To carry out this task, the command first calls the **Get-CsUserServicesConfiguration** cmdlet without any parameters in order to return a collection of all the User Services configuration settings currently in use. This collection is the piped to the **Where-Object** cmdlet, which selects only those settings where the value of the MaxContacts property is greater than 250. Those settings are then piped to, and removed by, the **Remove-CsUserServicesConfiguration** cmdlet.
  
```
Get-CsUserServicesConfiguration | Where-Object {$_.MaxContacts -gt 250} | Remove-CsUserServicesConfiguration

```

## Detailed Description

Skype for Business Server 2015 relies on the User Services service to help maintain presence information for users and to manage meetings and conferences. In turn, the **CsUserServicesConfiguration** cmdlets are used to administer User Services configuration settings at the global, site, and service scope. (Note that the only service that can host User Services configuration settings is the User Services service itself.) These settings help determine such things as the number of contacts a user can have, the number of meetings a user can have scheduled at any one time, and the length of time that a given meeting can remain active.
  
The **Remove-CsUserServicesConfiguration** cmdlet enables you to delete User Services configuration settings that have been applied at the site or service scope. This cmdlet can also be run against the global collection. In that case, however, the global settings will not be deleted; that's because the global settings cannot be deleted. Instead, all of the properties within the global collection will be reset to their default values. For example, if you have changed the MaxContacts value in the global settings to 500 and then run the **Remove-CsUserServicesConfiguration** cmdlet, MaxContacts will be reset to the default value of 250.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the User Services configuration settings to be removed. To delete settings configured at the site scope, use syntax similar to this:  <br/>  `-Identity site:Redmond` <br/> To delete settings at the service level, use syntax like this:  <br/>  `-Identity service:UserServer:atl-cs-001.litwareinc.com` <br/> The **Remove-CsUserServicesConfiguration** cmdlet can also be run against the global collection. In that case, however, the global collection will not be deleted. Instead, all the properties in that collection will be reset to their default values. <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might arise when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.UserServicesSettings object. The **Remove-CsUserServicesConfiguration** cmdlet accepts pipelined instances of the User Services settings object.
  
## Return Types

None. Instead, the **Remove-CsUserServicesConfiguration** cmdlet deletes existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.UserServicesSettings object.
  
## See also

#### 

[Get-CsUserServicesConfiguration](get-csuserservicesconfiguration.md)
  
[New-CsUserServicesConfiguration](new-csuserservicesconfiguration.md)
  
[Set-CsUserServicesConfiguration](set-csuserservicesconfiguration.md)

