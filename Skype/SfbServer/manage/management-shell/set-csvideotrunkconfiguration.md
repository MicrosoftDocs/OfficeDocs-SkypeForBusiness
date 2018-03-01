---
title: "Set-CsVideoTrunkConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f90d8b4d-6d3b-49c1-9390-c0e57eff219a
description: "Use the Set-CsVideoTrunkConfiguration to modify one or more Video Trunk configurations containing settings applicable to a video SIP trunk between the Video Interoperability Server (VIS) and a Video Gateway."
---

# Set-CsVideoTrunkConfiguration
 
Use the **Set-CsVideoTrunkConfiguration** to modify one or more Video Trunk configurations containing settings applicable to a video SIP trunk between the Video Interoperability Server (VIS) and a Video Gateway.
  
Video Trunk configuration settings are scoped to appropriate Video Gateway instances, and will govern the behavior of the SIP Trunk between each Video Gateway instance and the paired Video Interop Server instance that together define the Video Trunk. The Video Interop Server in Skype for Business Server 2015 enables you to incorporate 3rd party video teleconferencing systems (VTCs) into your Skype for Business Server 2015 infrastructure. The Video Interop Server is a Skype service that runs on a standalone pool and cannot be co-located on an FE pool.
  
This cmdlet was introduced in Skype for Business Server 2015.
  
```
Set-CsVideoTrunkConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

### Example 1

This example disables session timers for the collection of Video Trunk configuration settings assigned to the Seattle site.
  
```
Set-CsVideoTrunkConfiguration -Identity "site:Seattle" -EnableSessionTimer $False
```

### Example 2

In this example the session timers are disabled for all the Video Trunk configuration settings in use in the organization. The command first uses the **Get-CsVideoTrunkConfiguration** cmdlet to return a collection of all the available Video Trunk configuration settings. That collection is then piped to the **Set-CsVideoTrunkConfiguration** cmdlet, which disables the session timer for each item in the collection.
  
```
Get-CsVideoTrunkConfiguration | Set-CsVideoTrunkConfiguration -EnableSessionTimer $False
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Video Interop Server in Skype for Business Server 2015 enables you to incorporate 3rd party video teleconferencing systems (VTCs) into your Skype for Business Server 2015 infrastructure. The Video Interop Server is a Skype service that runs on a standalone pool and cannot be co-located on an FE pool.
  
To enable the Video Interop Server, you must use Topology Builder to define at least one VIS instance. Each VIS instance will typically be associated with one or more Video Gateways. Video Gateways route traffic between internal and third party video devices such as an internal Skype endpoint receiving video from an third party PBX supporting 3rd party video teleconferencing systems (VTCs). The Video Gateway and a Video Interop Server (VIS) use a Session Initiation Protocol (SIP) trunk to connect video calls between third party VTCs and internal endpoints.
  
Video Trunks settings can be managed by using the **CsVideoTrunkConfiguration** cmdlets. These settings are used to manage the following Video Trunk characteristics.
  
- RTCP for active calls
    
- RTCP for calls on hold
    
- Secure Real-time Transport Protocol (SRTP) use when Transport Layer Security (TLS) is used for the SIP signaling
    
- Session timers usage on the Video Interop Server (VIS) for dialogs associated with a Video Trunk
    
By default, Skype for Business Server 2015 ships with a single, global collection of Video Trunk configuration settings. However, administrators can use the **New-CsVideoTrunkConfiguration** cmdlet to create additional settings at the site or the service scope (for the Video Gateway service only). Both the single global collection of settings and any custom settings that you create can be modified by using the **Set-CsVideoTrunkConfiguration** cmdlet.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _EnableMediaEncryptionForSipOverTls_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True ($True) it is expected that the Video Gateway or third party video teleconferencing system (VTC) uses TLS to protect SIP signaling and uses SRTP to protect the media traffic. The default value is True ($True).  <br/> |
| _EnableSessionTimer_ <br/> |Optional  <br/> |System.Boolean  <br/> |Specifies whether the session timer is enabled. Session timers are used to determine whether a particular session is still active. The default is false ($False).  <br/> Note that even if this parameter is set to False, session timers can be applicable if the remote connection has session timer enabled. In such a case, the Video Interop Server will reply to session timer probes from the remote entity.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error messages and completes the cmdlet operation.  <br/> |
| _ForwardErrorCorrectionType_ <br/> |Optional  <br/> |System.String  <br/> | Specifies the type of Forward Error Correction (FEC) to be used between the Video Interop Server (VIS) and a Video Gateway. The valid settings are: <br/>  None: Turns off FEC between the VIS and the Video Gateway. <br/>  Cisco: Enables FEC compatible with Cisco Video Gateways, such as Cisco Unified Communications Manager (CUCM). <br/> |
| _GatewaySendsRtcpForActiveCalls_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True ($True) it is expected that the Video Gateway or third party video teleconferencing system (VTC) sends RTCP for calls that are enabled for media sending from the Video Gateway or VTC. The default value is True ($True).  <br/> |
| _GatewaySendsRtcpForCallsOnHold_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True ($True) it is expected that the Video Gateway or third party video teleconferencing system (VTC) sends RTCP for calls that are disabled for media sending from the Video Gateway or VTC. The default value is False ($False).  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The  _Identity_ parameter specifies the unique identifier for the video trunk configuration to be modified. <br/> For example, this syntax creates a new collection of settings assigned to the Redmond site: `-Identity "site:Redmond"`. And this syntax creates a new collection assigned to the Video Gateway "video-pbx-001.litwareinc.com": `-Identity "service:VideoGateway:video-pbx-001.litwareinc.com"` <br/> If this parameter is not specified, the **Set-CsVideoTrunkConfiguration** cmdlet will automatically modify the global settings. <br/> |
| _Instance_ <br/> |Optional  <br/> |System.Management.Automation.PSObject  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Set-CsVideoTrunkConfiguration** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.VideoTrunkConfiguration object.
  
## Return Types
<a name="ReturnTypes"> </a>

None. The **Set-CsVideoTrunkConfiguration** cmdlet modifies existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.VideoTrunkConfiguration object.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsVideoTrunkConfiguration](get-csvideotrunkconfiguration.md)
  
[New-CsVideoTrunkConfiguration](new-csvideotrunkconfiguration.md)
  
[Remove-CsVideoTrunkConfiguration](remove-csvideotrunkconfiguration.md)

