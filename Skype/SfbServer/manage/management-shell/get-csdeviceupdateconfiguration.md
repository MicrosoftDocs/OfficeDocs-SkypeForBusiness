---
title: "Get-CsDeviceUpdateConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: e7adc8a7-616a-41b1-8f4b-5f8778e46f55
description: "Returns information about the device update configuration settings currently deployed in your organization. These settings help manage the Device Update Web service, a Skype for Business Server 2015 component that enables administrators to distribute firmware updates to telephones and other devices running Skype for Business. This cmdlet was introduced in Lync Server 2010."
---

# Get-CsDeviceUpdateConfiguration
[]
Returns information about the device update configuration settings currently deployed in your organization. These settings help manage the Device Update Web service, a Skype for Business Server 2015 component that enables administrators to distribute firmware updates to telephones and other devices running Skype for Business. This cmdlet was introduced in Lync Server 2010.
  
```
Get-CsDeviceUpdateConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

The command shown in Example 1 returns a collection of all the device update configuration settings currently in use in the organization. Calling the **Get-CsDeviceUpdateConfiguration** cmdlet without any additional parameters returns all the device update settings currently in use.
  
```
Get-CsDeviceUpdateConfiguration 
```

### EXAMPLE 2

In Example 2, information is returned for the global device update configuration settings.
  
```
Get-CsDeviceUpdateConfiguration -Identity Global
```

### EXAMPLE 3

Example 3 demonstrates the use of the Filter parameter. The filter value "site:\*" returns a collection of all the device update configuration settings applied at the site scope; that's because these settings all have an Identity that begins with the string value "site:".
  
```
Get-CsDeviceUpdateConfiguration -Filter site:*
```

### EXAMPLE 4

Example 4 returns all the device update configuration settings where the MaxLogFileSize property is greater than 2048000 bytes. To do this, the **Get-CsDeviceUpdateConfiguration** cmdlet is used to return a collection of all the device update configuration settings currently in use. That collection is then piped to the **Where-Object** cmdlet, which picks out only those settings where the MaxLogFileSize property is greater than 2048000.
  
```
Get-CsDeviceUpdateConfiguration | Where-Object {$_.MaxLogFileSize -gt 2048000}
```

### EXAMPLE 5

The command shown in Example 5 returns all the device update configuration settings that include "Watson" as a valid log file type. To accomplish this task, the **Get-CsDeviceUpdateConfiguration** cmdlet is used to return a collection of all the device update configuration settings. That collection is then piped to the **Where-Object** cmdlet, which picks out only the device settings that include "Watson" in their set of valid log file types.
  
```
Get-CsDeviceUpdateConfiguration | Where-Object {$_.ValidLogFileTypes -like "*Watson*"}
```

## Detailed Description

The Device Update Web service provides a way for administrators to distribute firmware updates to devices that run Skype for Business. Periodically, administrators upload a set of device update rules to Skype for Business Server 2015. After those rules have been tested and approved, they can then be applied to the appropriate devices as those devices connect to the system. Devices check for updates when they are first powered on, then check again when a user logs on. After that, devices check for updates every 24 hours. 
  
The Device Update Web service is managed by using device configuration settings; these settings can be applied at the global scope or at the site scope. You can use the **Get-CsDeviceUpdateConfiguration** cmdlet to return information about the device update configuration settings currently in use in your organization.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Provides a way for you to use wildcard characters when specifying device update configuration settings. For example, to return a collection of all the configuration settings that have been applied at the site scope, use this syntax:  `-Filter "site:*"`. To return all the settings that have the term "EMEA" in their Identity, use this syntax:  `-Filter "*EMEA*"`. Note that the Filter parameter acts only on the Identity of the settings; you cannot filter on other device update configuration properties.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Indicates the Identity of the device update configuration settings to be retrieved. To refer to the global settings, use this syntax:  `-Identity global`. To refer to site settings, use syntax similar to this:  `-Identity site:Redmond`. Note that you cannot use wildcards when specifying an Identity. If you need to use wildcards, use the Filter parameter instead.  <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the device update configuration data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None. The **Get-CsDeviceUpdateConfiguration** cmdlet does not accept pipelined input.
  
## Return Types

The **Get-CsDeviceUpdateConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.DeviceUpdate.DeviceUpdateConfiguration object.
  
## See also

#### 

[New-CsDeviceUpdateConfiguration](new-csdeviceupdateconfiguration.md)
  
[Remove-CsDeviceUpdateConfiguration](remove-csdeviceupdateconfiguration.md)
  
[Set-CsDeviceUpdateConfiguration](set-csdeviceupdateconfiguration.md)

