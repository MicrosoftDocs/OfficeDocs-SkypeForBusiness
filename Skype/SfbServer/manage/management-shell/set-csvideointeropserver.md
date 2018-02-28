---
title: "Set-CsVideoInteropServer"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: a07791d3-61fc-4b47-9dce-d3a50c9151b0
description: "Use the Set-CsVideoInteropServer to modify the property values of one or more Video Interop Servers (VIS). The Video Interop Server is a Skype service that is used to communicate with a Video Gateway via a Session Initiation Protocol (SIP) trunk. Video Gateways route traffic between internal and 3rd party video devices such as an internal Skype endpoint exchanging video with a 3rd party PBX supporting 3rd party video teleconferencing systems (VTCs). The Video Gateway and a Video Interop Server (VIS) use a Session Initiation Protocol (SIP) trunk to connect video calls between 3rd party VTCs and internal endpoints."
---

# Set-CsVideoInteropServer
[]
Use the **Set-CsVideoInteropServer** to modify the property values of one or more Video Interop Servers (VIS). The Video Interop Server is a Skype service that is used to communicate with a Video Gateway via a Session Initiation Protocol (SIP) trunk. Video Gateways route traffic between internal and 3rd party video devices such as an internal Skype endpoint exchanging video with a 3rd party PBX supporting 3rd party video teleconferencing systems (VTCs). The Video Gateway and a Video Interop Server (VIS) use a Session Initiation Protocol (SIP) trunk to connect video calls between 3rd party VTCs and internal endpoints.
  
```
Set-CsVideoInteropServer [-Identity <XdsGlobalRelativeIdentity>] [-AudioPortCount <UInt16>] [-AudioPortStart <UInt16>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Registrar <String>] [-RegistrationTcpPort <UInt16>] [-RegistrationTlsPort <UInt16>] [-SipTrunkTcpPort <UInt16>] [-SipTrunkTlsPort <UInt16>] [-VideoPortCount <UInt16>] [-VideoPortStart <UInt16>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

This example sets the SIP trunk TLS port for the Video Interop server VideoInteropServer:atl-cs-001.litwareinc.com to port 444.
  
```
Set-CsVideoInteropServer -Identity "VideoInteropServer:atl-cs-001.litwareinc.com" -SipTrunkTlsPort 444
```

### Example 2

This example sets the SIP trunk TLS port for all the organization's Video Interop servers is set to port 444. This the command first calls the Get-CsService cmdlet, along with the VideoInteropServer parameter, to return a collection of all the Video Interop servers configured for use in the organization. That collection is then piped to the Set-CsVideoInteropServer cmdlet, which changes the TLS port for each server in the collection.
  
```
Get-CsService -VideoInteropServer | Set-CsVideoInteropServer -SipTrunkTlsPort 444
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Video Interop Server (VIS) in Skype for Business Server 2015 incorporates 3rd party video teleconferencing systems (VTCs) into your Skype for Business Server 2015 infrastructure. The VIS is a service that runs on a standalone pool and cannot be co-located on an FE pool.
  
To enable the Video Interop Server, you must use Topology Builder to define at least one VIS instance. Each VIS instance will typically be associated with one or more Video Gateways. Video Gateways route traffic between internal and 3rd party video devices such as an internal Skype endpoint receiving video from a 3rd party PBX supporting 3rd party video teleconferencing systems (VTCs). The Video Gateway and a VIS use a Session Initiation Protocol (SIP) trunk to connect video calls between 3rd party VTCs and internal endpoints. 
  
After the Video Interop Server has been defined by using the Topology Builder, you can then modify the properties of that server by using the **Set-CsVideoInteropServer** cmdlet.
  
To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt.
  
```
Get-CsAdminRole | Where-Object {$_.Cmdlets -Match "Set-CsVideoInteropServer"}
```

## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _AudioPortCount_ <br/> |Optional  <br/> |System.UInt16  <br/> |Total number of ports allocated for sending and receiving audio traffic. The actual ports to be opened will start with the value configured for AudioPortStart and continue through the number of ports specified for AudioPortCount. For example, if the AudioPortStart is set to 60000 and the AudioPortCount is set to 100, then ports 60000 through 60099 will be used for audio traffic.  <br/> |
| _AudioPortStart_ <br/> |Optional  <br/> |System.UInt16  <br/> |First port in the range of ports allocated for sending and receiving audio traffic. For example:  `-AudioPortStart 60000`.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Service location of the Video Interop Server to be modified. For example:  `-Identity "VideoInteropServer:atl-cs-001.litwareinc.com"`.  <br/> |
| _Registrar_ <br/> |Optional  <br/> |System.String  <br/> |Service identity of the Registrar associated with the Video Interop Server. For example:  `-Registrar "Registrar:atl-cs-001.litwareinc.com"`.  <br/> |
| _RegistrationTcpPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |This parameter is reserved for internal Microsoft use.  <br/> |
| _RegistrationTlsPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |This parameter is reserved for internal Microsoft use.  <br/> |
| _SipTrunkTcpPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |TCP (Transmission Control Protocol) listening port on the Video Interop Server used for SIP trunk communication with a Video Gateway.  <br/> |
| _SipTrunkTlsPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |TLS (Transport Layer Security) listening port on the Video Interop Server used for SIP trunk communication with a Video Gateway.  <br/> |
| _VideoPortCount_ <br/> |Optional  <br/> |System.UInt16  <br/> |Total number of ports allocated for sending and receiving video traffic. The actual ports to be opened will start with the value configured for VideoPortStart and continue through the number of ports specified for VideoPortCount. For example, if the VideoPortStart is set to 60000 and the VideoPortCount is set to 100, then ports 60000 through 60099 will be used for video traffic.  <br/> |
| _VideoPortStart_ <br/> |Optional  <br/> |System.UInt16  <br/> |First port in the range of ports allocated for sending and receiving video traffic. For example:  `-AudioPortStart 60000`.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The Set-CsVideoInteropServer accepts pipelined instances of the Microsoft.Rtc.Management.Xds.DisplayVideoInteropServer object.
  
## Return Types
<a name="ReturnTypes"> </a>

None. The Set-CsVideoInteropServer cmdlet does not return any objects or values.
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Set-CsVideoGateway](set-csvideogateway.md)
  
[Get-CsVideoTrunk](get-csvideotrunk.md)

