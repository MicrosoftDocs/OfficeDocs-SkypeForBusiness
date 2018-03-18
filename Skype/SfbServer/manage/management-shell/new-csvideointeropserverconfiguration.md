---
title: "New-CsVideoInteropServerConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 1f1124e2-9bba-4659-a48f-0c2c1e060482
description: "Use the New-CsVideoInteropServerConfiguration cmdlet to create a new collection of Video Interop Server (VIS) configuration settings. The configuration can then be scoped to the appropriate VIS instances, and will govern the behavior of those instances. The Video Interop Server (VIS) enables you to incorporate 3rd party video teleconferencing systems (VTCs) into your Skype for Business infrastructure. VIS is a Skype for Business service that runs on a standalone pool and cannot be co-located on an FE pool."
---

# New-CsVideoInteropServerConfiguration
 
Use the **New-CsVideoInteropServerConfiguration** cmdlet to create a new collection of Video Interop Server (VIS) configuration settings. The configuration can then be scoped to the appropriate VIS instances, and will govern the behavior of those instances. The Video Interop Server (VIS) enables you to incorporate 3rd party video teleconferencing systems (VTCs) into your Skype for Business infrastructure. VIS is a Skype for Business service that runs on a standalone pool and cannot be co-located on an FE pool.
  
This cmdlet was introduced in Skype for Business Server 2015.
  
```
New-CsVideoInteropServerConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-EnableEnhancedVideoExperience <$true | $false>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

This example creates a new collection of VIS configuration settings that are assigned to the Redmond site. The enhanced video experience is disabled by setting the  _EnableEnhancedVideoExperience_ parameter to False ($False).
  
```
New-CsVideoInteropServerConfiguration -Identity "site:Redmond" -EnableEnhancedVideoExperience $False
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Video Interop Server (VIS) enables you to incorporate 3rd party video teleconferencing systems (VTCs) into your Skype for Business infrastructure. VIS is a Skype for Business service that runs on a standalone pool and cannot be co-located on an FE pool. 
  
To enable the Video Interop Server (VIS) you must use Topology Builder to define at least one VIS instance. Each VIS instance will typically be associated with one or more Video Gateways. Video Gateways route traffic between internal and external video devices such as an internal Skype for Business endpoint receiving video from an external PBX supporting 3rd party video teleconferencing systems (VTCs). The Video Gateway and a VIS use a Session Initiation Protocol (SIP) trunk to connect video calls between external VTCs and internal endpoints. 
  
The Video Interop Server can be managed by using VIS configuration settings and the **CsVideoInteropServerConfiguration** cmdlets. These settings are used to enable or disable the enhanced video experience (in which a single video stream is converted to multiple streams in order to accommodate the needs of devices that use different frame rates or video resolutions).
  
By default, Skype for Business Server 2015 ships with a single, global collection of video interop configuration settings. However, administrators can use the **New-CsVideoInteropServerConfiguration** cmdlet to create additional settings at the site or the service scope (for the VIS service only.)
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the new collection of VIS configuration settings. New collections can be created at either the site scope or the service scope (for the video interop service only). For example, this syntax creates a new collection of settings assigned to the Redmond site:  <br/>  `-Identity "site:Redmond"` <br/> And this syntax creates a new collection assigned to the VIS for the pool atl-cs-001.litwareinc.com:  <br/>  `-Identity "service:VideoInteropServer:atl-edge-001.litwareinc.com"` <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _EnableEnhancedVideoExperience_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True ($True) the single video stream coming from a third party video teleconferencing system (VTC) will be converted to multiple streams in order to meet the needs of devices using different video resolutions or frame rates. The default value is True ($True).  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error messages and completes the cmdlet operation.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching **Set-\<cmdlet\>**. <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The **New-CsVideoInteropServerConfiguration** cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The **New-CsVideoInteropServerConfiguration cmdlet** creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.VideoInteropServer.VideoInteropServerConfiguration object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsVideoInteropServerConfiguration](get-csvideointeropserverconfiguration.md)
  
[Remove-CsVideoInteropServerConfiguration](remove-csvideointeropserverconfiguration.md)
  
[Set-CsVideoInteropServerConfiguration](set-csvideointeropserverconfiguration.md)

