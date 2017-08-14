---
title: Set-CsMediationServer
ms.prod: SKYPEFORBUSINESS
ms.assetid: 13efdd9d-ba26-4c93-b0b9-b6e4739bb630
---


# Set-CsMediationServer
[]
Enables you to modify the properties of one or more Mediation Servers. Mediation Servers are used to route traffic between your internal Enterprise Voice infrastructure and a public switched telephone network (PSTN) gateway or a SIP trunk. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Set-CsMediationServer [-Identity <XdsGlobalRelativeIdentity>] [-AudioPortCount <UInt16>] [-AudioPortStart <UInt16>] [-Confirm [<SwitchParameter>]] [-EdgeServer <String>] [-Force <SwitchParameter>] [-Registrar <String>] [-SipClientTcpPort <UInt16>] [-SipClientTlsPort <UInt16>] [-SipServerPort <UInt16>] [-WhatIf [<SwitchParameter>]]

```


## Examples


  
    
    

### EXAMPLE 1

The command shown in Example 1 sets the SIP gateway TCP listening port to 5072 for the Mediation Server MediationServer:atl-cs-001.litwareinc.com. After changing the port you will need to restart the Skype for Business Server 2015 Mediation service.
  
    
    

```

Set-CsMediationServer -Identity "MediationServer:atl-cs-001.litwareinc.com" -SipClientTcpPort 5072
```


### EXAMPLE 2

Example 2 configures audio port settings for the Mediation Server MediationServer:atl-cs-001.litwareinc.com. In this example the starting audio port is set to 60000 and the total number of ports allocated for audio is 1000.
  
    
    

```
Set-CsMediationServer -Identity "MediationServer:atl-cs-001.litwareinc.com" -AudioPortStart 60000 -AudioPortCount 1000
```


## Detailed Description

Mediation Servers act as a bridge between your internal Enterprise Voice configuration and either a PSTN gateway, IP-PBX, or a SIP trunk; in turn, this provides a way for your Enterprise Voice users (who are using Voice over Internet Protocol (VoIP) devices) to communicate with people using standard land-line telephones or mobile phones. The **Set-CsMediationServer** cmdlet provides a way for you to make changes to an existing Mediation Server. In particular, you can modify the ports used for communicating with client devices, Front End Servers, and gateways peers. If necessary, the **Set-CsMediationServer** cmdlet can also be used to associate a Mediation Server with a new Registrar or a new Edge Server.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _AudioPortCount_ <br/> |Optional  <br/> |System.UInt16  <br/> |Total number of ports allocated for sending and receiving audio traffic. The actual ports to be opened will start with the value configured for AudioPortStart and continue through the number of ports specified for AudioPortCount. For example, if the AudioPortStart is set to 60000 and the AudioPortCount is set to 100, then ports 60000 through 60099 inclusive will be used for audio traffic.  <br/> A minimum of seven media ports are needed for relaying a single audio call:  <br/> Two gateway ports. One port is needed for real-time transport protocol (RTP) traffic and one for real-time transport control protocol (RTCP) traffic.  <br/> Two User Datagram Protocol (UDP) relay ports, one for RTP traffic and one for RTCP traffic.  <br/> One Transmission Control Protocol (TCP) relay port. A single TCP relay port can handle both RTP and RTCP traffic.  <br/> Two local ports per network interface, one for RTP traffic and one for RTCP traffic  <br/> |
| _AudioPortStart_ <br/> |Optional  <br/> |System.UInt16  <br/> |First port in the range of ports allocated for sending and receiving audio traffic. For example: -AudioPortStart 60000.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _EdgeServer_ <br/> |Optional  <br/> |System.String  <br/> |Service identity of the Edge Server to be associated with the Mediation Server. For example: - `EdgeServer "EdgeServer:atl-edge-001.litwareinc.com"`.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity  <br/> |Service location of the Mediation Server to be modified. For example:  `-Identity "MediationServer:atl-cs-001.litwareinc.com"`.  <br/> Note that you can leave off the prefix "MediationServer:" when specifying a Mediation Server. For example:  `-Identity "atl-cs-001.litwareinc.com"`.  <br/> |
| _Registrar_ <br/> |Optional  <br/> |System.String  <br/> |Service identity of the Registrar to be associated with the Mediation Server. For example:  `-Registrar "Registrar:atl-cs-001.litwareinc.com"`.  <br/> |
| _SipClientTcpPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Listening port used for communicating with gateway peers using TCP. By default, no TCP port is defined; however, a TCP port with the port number 5068 will automatically be created when a PSTN gateway is created. If you change the SipClientTcpPort you will need to restart the Mediation Server service before the new port will actually be used.  <br/> |
| _SipClientTlsPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Listening port used for communicating with gateway peers using the Transport Layer Security (TLS) protocol. By default, SipClientTlsPort is configured to use port 5067. If you change the SipClientTlsPort you will need to restart the Mediation Server service before the new port will actually be used.  <br/> |
| _SipServerPort_ <br/> |Optional  <br/> |System.UInt16  <br/> |Listening port used for communicating with Front End Servers. By default, SipServerPort is configured to use port 5070. If you change the SipServerPort, you will need to restart the Mediation Server service before the new port will actually be used.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types

None. The **Set-CsMediationServer** cmdlet does not accept pipelined input.
  
    
    

## Return Types

The **Set-CsMediationServer** cmdlet does not return any objects or values. Instead, the cmdlet modifies existing instances of the Microsoft.Rtc.Management.Xds.DisplayMediationServer object.
  
    
    

## See also


#### 


  
    
    
 [Get-CsService](get-csservice.md)
