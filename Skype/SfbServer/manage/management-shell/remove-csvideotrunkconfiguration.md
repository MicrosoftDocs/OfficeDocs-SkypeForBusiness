---
title: "Remove-CsVideoTrunkConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 6ab45bb0-b843-4b4a-88d4-436b82f5aacc
description: "Use the Remove-CsVideoTrunkConfiguration to remove one or more Video Trunk configurations. Video Trunk configuration settings are scoped to Video Gateway instances, and govern the behavior of the Session Initiation Protocol (SIP) trunk between each Video Gateway instance and the paired Video Interop Server instance that together define the Video Trunk."
---

# Remove-CsVideoTrunkConfiguration
 
Use the **Remove-CsVideoTrunkConfiguration** to remove one or more Video Trunk configurations. Video Trunk configuration settings are scoped to Video Gateway instances, and govern the behavior of the Session Initiation Protocol (SIP) trunk between each Video Gateway instance and the paired Video Interop Server instance that together define the Video Trunk.
  
This cmdlet was introduced in Skype for Business Server 2015.
  
```
Remove-CsVideoTrunkConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

This example removes the Video Trunk configuration settings scoped to the Seattle site.
  
```
Remove-CsVideoTrunkConfiguration -Identity "site:Seattle"
```

### Example 2

This example removes all the configuration settings that have been scoped at the site level. The command first calls the **Get-CsVideoTrunkConfiguration** cmdlet along with the _Filter_ parameter that limits the returns to configurations scoped at the site level. Those configuration objects are then piped to, and removed by, the **Remove-CsVideoTrunkConfiguration** cmdlet.
  
```
Get-CsVideoTrunkConfiguration -Filter "site:*" | Remove-CsVideoTrunkConfiguration
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Video Interop Server (VIS) in Skype for Business Server 2015 incorporates 3rd party video teleconferencing systems (VTCs) into your Skype for Business Server 2015 infrastructure. The VIS is a service that runs on a standalone pool and cannot be co-located on an FE pool.
  
To enable the Video Interop Server, you must use Topology Builder to define at least one VIS instance. Each VIS instance will typically be associated with one or more Video Gateways. Video Gateways route traffic between internal and third party video devices such as an internal Skype endpoint receiving video from an third party PBX supporting 3rd party video teleconferencing systems (VTCs). The Video Gateway and a Video Interop Server (VIS) use a Session Initiation Protocol (SIP) trunk to connect video calls between third party VTCs and internal endpoints.
  
Video Trunks settings can be managed by using the **CsVideoTrunkConfiguration** cmdlets. These settings are used to manage the following Video Trunk characteristics.
  
- RTCP for active calls
    
- RTCP for calls on hold
    
- Secure Real-time Transport Protocol (SRTP) use when Transport Layer Security (TLS) is used for the SIP signaling
    
- Session timers usage on the Video Interop Server (VIS) for dialogs associated with a Video Trunk
    
By default, Skype for Business Server 2015 ships with a single, global collection of Video Trunk configuration settings. However, administrators can use the **New-CsVideoTrunkConfiguration** cmdlet to create additional settings at the site or the service scope (for the Video Gateway service only).
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The  _Identity_ parameter specifies the Video Trunk configuration to remove. Video Trunk configuration settings can be configured at the global, site, or service scope (for the VideoGateway service only). To refer to the global instance, use this syntax: `-Identity "global"`To refer to a collection at the site scope: `-Identity "site:Redmond"` <br/> Wildcard characters such as the asterisk (*) cannot be used with the  _Identity_ parameter. <br/> The **Remove-CsVideoTrunkConfiguration** cmdlet can be run against the single global collection of settings. However, that single global collection will not be deleted. Instead, all the properties within the collection will be reset to their default values. <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error messages and completes the cmdlet operation.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Remove-CsVideoTrunkConfiguration** cmdlet accepts pipelined input of the Microsoft.Rtc.Management.WritableConfig.Settings.VideoTrunkConfiguration object.
  
## Return Types
<a name="ReturnTypes"> </a>

None. The **Remove-CsVideoTrunkConfiguration** cmdlet removes specified Microsoft.Rtc.Management.WritableConfig.Settings.VideoTrunkConfiguration objects.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsVideoTrunkConfiguration](get-csvideotrunkconfiguration.md)
  
[New-CsVideoTrunkConfiguration](new-csvideotrunkconfiguration.md)
  
[Set-CsVideoTrunkConfiguration](set-csvideotrunkconfiguration.md)

