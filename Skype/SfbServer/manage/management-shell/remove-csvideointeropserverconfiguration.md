---
title: "Remove-CsVideoInteropServerConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 62a93c97-f8bc-4420-a611-7f6c1e1d7200
description: "Use the Remove-CsVideoInteropServerConfiguration cmdlet to remove an existing collection of Video Interop Server (VIS) configuration settings. Video Interop Server configuration settings are scoped to appropriate Video Interop Server (VIS) instances, and will govern the behavior of those instances."
---

# Remove-CsVideoInteropServerConfiguration
 
Use the **Remove-CsVideoInteropServerConfiguration** cmdlet to remove an existing collection of Video Interop Server (VIS) configuration settings. Video Interop Server configuration settings are scoped to appropriate Video Interop Server (VIS) instances, and will govern the behavior of those instances.
  
This cmdlet was introduced in Skype for Business Server 2015.
  
```
Remove-CsVideoInteropServerConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

This example deletes the VIS configuration settings assigned to the Redmond site.
  
```
Remove-CsVideoInteropServerConfiguration -Identity "site:Redmond"
```

### Example 2

This example deletes all the VIS settings that have been assigned to the site scope are deleted. The command calls the **Get-CsVideoInteropServerConfiguration** and filters the configuration by using the _Filter_ parameter value "site:*". Those configuration objects are then piped to, and deleted by, the **Remove-CsVideoInteropServerConfiguration** cmdlet.
  
```
Get-CsVideoInteropServerConfiguration -Filter "site:*" | Remove-CsVideoInteropServerConfiguration
```

### Example 3

This example deletes all the VIS settings where the enhanced video experience has been enabled. The command first calls **Get-CsVideoInteropServerConfiguration** to return a collection of all the VIS settings in use in the organization. Those configuration objects then piped to the **Where-Object** cmdlet, which filters for VIS configuration objects in which EnableEnhancedVideoExperience property has been set to True ($True). Those configuration objects are then piped to and deleted by the **Remove-CsVideoInteropServerConfiguration**.
  
```
Get-CsVideoInteropServerConfiguration | Where-Object {$_.EnableEnhancedVideoExperience -eq $True} | Remove-CsVideoInteropServerConfiguration
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Video Interop Server (VIS) enables you to incorporate 3rd party video teleconferencing systems (VTCs) into your Skype for Business infrastructure. VIS is a Skype for Business service that runs on a standalone pool and cannot be co-located on an FE pool. 
  
To enable the Video Interop Server (VIS) you must use Topology Builder to define at least one VIS instance. Each VIS instance will typically be associated with one or more Video Gateways. Video Gateways route traffic between internal and external video devices such as an internal Skype for Business endpoint receiving video from an external PBX supporting 3rd party video teleconferencing systems (VTCs). The Video Gateway and a VIS use a Session Initiation Protocol (SIP) trunk to connect video calls between external VTCs and internal endpoints. 
  
You can manage the Video Interop Server (VIS) by using VIS configuration settings and the **CsVideoInteropServerConfiguration** cmdlets. These settings are used to enable or disable the enhanced video experience (in which a single video stream is converted to multiple streams in order to accommodate the needs of devices that use different frame rates or video resolutions).
  
By default, Skype for Business Server ships with a single, global collection of Video Interop Server configuration settings. You can use the **New-CsVideoInteropServerConfiguration** cmdlet to create additional settings at the site or the service scope (for the VIS service only.) These custom settings can later be removed by using the **Remove-CsVideoInteropServerConfiguration** cmdlet. This cmdlet can also be run against the global collection of VIS settings. The global collection will not be removed, but all the properties in the global collection will be reset to their default values. Skype for Business Server 2015 does not allow you to delete the global settings.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identity assigned to the video interop service configuration settings when they were created. Video interop settings can be assigned at the global, site, or service scope (for the VideoInteropServer service only). For example, to remove settings configured at the site scope use the following syntax:  <br/>  `-Identity "site:Redmond"` <br/> Wildcard characters such as the asterisk (*) cannot be used with the  _Identity_ parameter. The **Remove-CsVideoInteropServerConfiguration** cmdlet can be run against the global settings collection. However, the global collection will not be deleted. Instead, all the properties within the collection will be reset to their default values. <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error messages and completes the cmdlet operation.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Remove-CsVideoInteropServerConfiguration** cmdlet accepts pipelined input of the Microsoft.Rtc.Management.WritableConfig.Settings.VideoInteropServer.VideoInteropServerConfiguration object.
  
## Return Types
<a name="ReturnTypes"> </a>

None. The **Remove-CsVideoInteropServerConfiguration** cmdlet deletes instances of the Microsoft.Rtc.Management.WritableConfig.Settings.VideoInteropServer.VideoInteropServerConfiguration object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsVideoInteropServerConfiguration](get-csvideointeropserverconfiguration.md)
  
[New-CsVideoInteropServerConfiguration](new-csvideointeropserverconfiguration.md)
  
[Set-CsVideoInteropServerConfiguration](set-csvideointeropserverconfiguration.md)

