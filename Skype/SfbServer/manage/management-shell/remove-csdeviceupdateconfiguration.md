---
title: "Remove-CsDeviceUpdateConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 4335eb24-61a6-4e76-8242-edfd861d7d0b
description: "Removes the specified device update configuration settings. These settings help manage the Device Update Web service, a Skype for Business Server 2015 component that enables administrators to distribute firmware updates to telephones and other devices running Skype for Business Phone Edition. This cmdlet was introduced in Lync Server 2010."
---

# Remove-CsDeviceUpdateConfiguration
 
Removes the specified device update configuration settings. These settings help manage the Device Update Web service, a Skype for Business Server 2015 component that enables administrators to distribute firmware updates to telephones and other devices running Skype for Business Phone Edition. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsDeviceUpdateConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

In Example 1, the **Remove-CsDeviceUpdateConfiguration** cmdlet is used to "remove" the global device update configuration settings. Because the global settings cannot actually be removed, the command will not delete anything; however, all the properties in the global device update configuration settings will be reset to their default values.
  
```
Remove-CsDeviceUpdateConfiguration -Identity global
```

### EXAMPLE 2

The command shown in Example 2 removes the device update configuration settings with the Identity site:Redmond. Because these settings were configured at the site scope, they will be deleted, and the Redmond site will no longer have its own set of device update configuration settings. 
  
```
Remove-CsDeviceUpdateConfiguration -Identity site:Redmond
```

### EXAMPLE 3

In Example 3, all the device update configuration settings that have been configured at the site scope are removed. To do this, the **Get-CsDeviceUpdateConfiguration** cmdlet and the Filter parameter are used to return all the settings that have an Identity that begins with the string value "site:"; by definition, these will all be settings that were configured at the site scope. That collection is then piped to the **Remove-CsDeviceUpdateConfiguration** cmdlet, which removes each of the items in the collection.
  
```
Get-CsDeviceUpdateConfiguration -Filter "site:*" | Remove-CsDeviceUpdateConfiguration 
```

### EXAMPLE 4

In Example 4, all the device update configuration settings that have a MaxLogFileSize property greater than 1024000 bytes are deleted. To accomplish this task, the **Get-CsDeviceUpdateConfiguration** cmdlet is first called in order to return a collection of all the device update configuration settings. This collection is piped to the **Where-Object** cmdlet, which selects only those configuration settings where the MaxLogFileSize property is greater than 1024000 bytes. That filtered collection is then piped to the **Remove-CsDeviceUpdateConfiguration** cmdlet, which deletes each item in the collection.
  
```
Get-CsDeviceUpdateConfiguration | Where-Object {$_.MaxLogFileSize -lt 1024000} | Remove-CsDeviceUpdateConfiguration
```

## Detailed Description

The Device Update Web service provides a way for administrators to distribute firmware updates to devices that run Skype for Business Phone Edition. Periodically, administrators upload a set of device update rules to Skype for Business Server 2015. After those rules have been tested and approved, they can then be applied to the appropriate devices as those devices connect to the system. Devices check for updates when they are first powered on, then check again when a user logs on. After that, devices check for updates every 24 hours.
  
Skype for Business Server 2015 uses device update configuration settings to manage the Device Update Web service; these configuration settings can be applied at the global scope or at the site scope. By default, settings are found only at the global scope; however, you can use the **New-CsDeviceUpdateConfiguration** cmdlet to assign customized settings at the site scope as well.
  
In addition, you can use the **Remove-CsDeviceUpdateConfiguration** cmdlet to delete settings that have been assigned at the site scope. When you run this cmdlet against a site, the device update configuration settings assigned to that site are removed. You can also run the **Remove-CsDeviceUpdateConfiguration** cmdlet against the global settings. In that case, however, the global settings will not be removed; that's because you cannot remove the global device update configuration settings. Instead, the global properties will be reset to their default values. For example, suppose you have changed the global property MaxLogCacheLimit to 1,024,000 bytes. If you run the **Remove-CsDeviceUpdateConfiguration** cmdlet against the global settings, the global settings will not be removed; however, any properties that have been modified will be reset to their default values. That means that MaxLogCacheLimit will be reset to 512,000 bytes.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Indicates the Identity of the device update configuration settings to be removed. To refer to the global settings, use this syntax:  `-Identity global`. To refer to site settings, use syntax similar to this:  `-Identity site:Redmond`. Note that you cannot use wildcards when specifying an Identity.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.DeviceUpdate.DeviceUpdateConfiguration object. The **Remove-CsDeviceUpdateConfiguration** cmdlet accepts pipelined instances of the device update configuration object.
  
## Return Types

None. Instead, the **Remove-CsDeviceUpdateConfiguration** cmdlet deletes instances of the Microsoft.Rtc.Management.WritableConfig.Settings.DeviceUpdate.DeviceUpdateConfiguration object.
  
## See also

#### 

[Get-CsDeviceUpdateConfiguration](get-csdeviceupdateconfiguration.md)
  
[New-CsDeviceUpdateConfiguration](new-csdeviceupdateconfiguration.md)
  
[Set-CsDeviceUpdateConfiguration](set-csdeviceupdateconfiguration.md)

