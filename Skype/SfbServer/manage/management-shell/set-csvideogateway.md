---
title: "Set-CsVideoGateway"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 66d2593b-574a-4b0f-a7d7-dab2eba1a19d
description: "Use the Set-CsVideoGateway cmdlet to modify the property values of one or more Video Gateways. Video Gateways route traffic between internal and 3rd party video devices such as an internal Skype endpoint exchanging video with a 3rd party PBX supporting 3rd party video teleconferencing systems (VTCs). The Video Gateway and a Video Interop Server (VIS) use a Session Initiation Protocol (SIP) trunk to connect video calls between 3rd party VTCs and internal endpoints."
---

# Set-CsVideoGateway
[]
Use the **Set-CsVideoGateway** cmdlet to modify the property values of one or more Video Gateways. Video Gateways route traffic between internal and 3rd party video devices such as an internal Skype endpoint exchanging video with a 3rd party PBX supporting 3rd party video teleconferencing systems (VTCs). The Video Gateway and a Video Interop Server (VIS) use a Session Initiation Protocol (SIP) trunk to connect video calls between 3rd party VTCs and internal endpoints.
  
This cmdlet was introduced in Skype for Business Server 2015.
  
```
Set-CsVideoGateway [-Identity <XdsGlobalRelativeIdentity>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-VideoGatewaySipClientTcpPort <UInt16>] [-VideoGatewaySipClientTlsPort <UInt16>] [-VideoInteropServer <String>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 changes the TCP client port for the video gateway located on the pool atl-cs-001.litwareinc.com. In this example, the port is set to 444.
  
```
Set-CsVideoGateway -Identity "VideoGateway:atl-cs-001.litwareinc.com" -VideoGatewaySipClientTcpPort 444
```

### Example 2

In Example 2, the TCP client ports for all the video gateways deployed in the organization are set to 444. To do this, the command first uses the Get-CsService cmdlet and the -VideoGateway parameter to return a collection of all the video gateways, That collection is then piped to the Set-CsVideoGateway cmdlet, which sets the TCP client port for all the gateways in the collection to 444.
  
```
Get-CsService -VideoGateway | Set-CsVideoGateway -VideoGatewaySipClientTcpPort 444
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Video Interop Server (VIS) in Skype for Business Server 2015 incorporates 3rd party video teleconferencing systems (VTCs) into your Skype for Business Server 2015 infrastructure. The VIS is a service that runs on a standalone pool and cannot be co-located on an FE pool.
  
To enable the Video Interop Server, you must use Topology Builder to define at least one VIS instance. Each VIS instance will typically be associated with one or more Video Gateways. Video Gateways route traffic between internal and 3rd party video devices such as an internal Skype endpoint receiving video from a 3rd party PBX supporting 3rd party video teleconferencing systems (VTCs). The Video Gateway and a Video Interop Server (VIS) use a Session Initiation Protocol (SIP) trunk to connect video calls between 3rd party VTCs and internal endpoints. After a Video Gateway has been defined, you can then manage the properties of that gateway by using the **Set-CsVideoGateway** cmdlet.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Service location of the video gateway being modified. For example:  <br/>  `-Identity "VideoGateway:atl-cs-001.litwareinc.com"` <br/> |
| _VideoGatewaySipClientTcpPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |TCP (Transmission Control Protocol) listening port on the Video Gateway used for SIP trunk communication with a Video Interop Server pool.  <br/> |
| _VideoGatewaySipClientTlsPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |TLS (Transport Layer Security) listening port on the Video Gateway used for SIP trunk communication with a Video Interop Server pool.  <br/> |
| _VideoInteropServer_ <br/> |Optional  <br/> |System.String  <br/> |Service location for the Video Interop Server associated with this Video Gateway.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The Set-CsVideoGateway cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.Xds.DisplayVideoGateway object.
  
## Return Types
<a name="ReturnTypes"> </a>

None. The Set-CsVideoGateway cmdlet does not return any objects or values.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Get-CsVideoTrunk](get-csvideotrunk.md)

