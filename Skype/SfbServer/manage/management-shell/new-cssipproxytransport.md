---
title: "New-CsSipProxyTransport"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 68587257-d666-429a-bf2d-f8a2b46f1f09
description: "Specifies the transmission protocol to be used in a static route. Skype for Business Server 2015 enables you to choose either Transmission Control Protocol (TCP) or Transport Layer Security (TLS) as the transmission protocol for a route. This cmdlet was introduced in Lync Server 2010."
---

# New-CsSipProxyTransport
[]
Specifies the transmission protocol to be used in a static route. Skype for Business Server 2015 enables you to choose either Transmission Control Protocol (TCP) or Transport Layer Security (TLS) as the transmission protocol for a route. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsSipProxyTransport -Port <UInt16> -TransportChoice <ITransportChoice>

```

## Examples

### EXAMPLE 1

The commands shown in Example 1 create a new SIP proxy transport object that uses TLS as its transport. Because TLS requires a certificate (to be used for authentication purposes), the first command in the example uses the **New-CsSipProxyUseDefaultCert** cmdlet to configure a new SipProxy.UseDefaultCert object. This object, stored in a variable named $cert, instructs Skype for Business Server 2015 to use the default certificate for the TLS transport. After the UseDefaultCert object has been created, the **New-CsSipProxyTLS** cmdlet can be called to create a new SipProxy.TLS object, one that uses the default certificate and points to atl-proxy-001.litwareinc.com as the fully qualified domain name (FQDN) of the next hop server.
  
```
$cert = New-CsSipProxyUseDefaultCert

$tls = New-CsSipProxyTLS -Certificate $cert -Fqdn atl-proxy-001.litwareinc.com

$transport = New-CsSipProxyTransport -TransportChoice $tls -Port 7500

```

### EXAMPLE 2

The commands shown in Example 2 create a new SIP proxy transport object that uses TCP as its transport. To do this, the first command in the example uses the **New-CsSipProxyTCP** cmdlet to create a new SipProxy.TCP object that points to the next hop server with the IP address 192.168.1.100; this TCP object is stored in a variable named $tcp.
  
After the SipProxy.TCP object has been created, the **New-CsSipProxyTransport** cmdlet can then be called to create a TCP transport object.
  
```
$tcp = New-CsSipProxyTCP -IPAddress 192.168.1.100

$transport = New-CsSipProxyTransport -TransportChoice $tcp -Port 7500
```

## Detailed Description

When you send a SIP message to someone, that message might need to traverse multiple subnets and networks before it is delivered; the path traveled by the message is often referred to as a route. In networking, there are two types of routes: dynamic and static. With dynamic routing, servers use algorithms to determine the next location (the next hop) where a message should be forwarded. With static routing, message paths are predetermined by system administrators. When a message is received by a server, the server checks the message address and then forwards the message to the next hop server that has been preconfigured by an administrator. If configured correctly, static routes help ensure timely, and accurate, delivery of messages, and with minimal overheard placed on servers. The downside to static routes is that messages are not dynamically rerouted in the event of a network failure.
  
Skype for Business Server 2015 enables you to set up static routes for proxy servers. These routes are composed of two primary pieces: proxy configuration settings and SIP proxy routes. In turn, SIP proxy routes have a number of properties; for example, each route must have a Transport, a property that defines the network protocol used for transmitting messages along the route. The Transport property can be specified using the **New-CsSipProxyTransport** cmdlet.
  
The **New-CsSipProxyTransport** cmdlet has two required parameters: TransportChoice and Port. The TransportChoice parameter is configured using another cmdlet, either the **New-CsSipProxyTCP** cmdlet (to assign the Transmission Control Protocol as the route transport) or the **New-CsSipProxyTLS** cmdlet (to assign the TLS as the route transport). Any transport object created by using the **New-CsSipProxyTransport** cmdlet must be saved to a variable. That variable will then be used to configure the Transport property of a SIP proxy route.
  
You do not need to use the **New-CsSipProxyTransport** cmdlet if you are using the **New-CsStaticRoute** cmdlet to create your static route.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Port_ <br/> |Required  <br/> |System.UInt16  <br/> |Port number used for SIP routing. For example: -Port 7742.  <br/> |
| _TransportChoice_ <br/> |Required  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.ITransportChoice  <br/> |Indicates the transmission protocol (TCP or TLS) to be used on the static route. To use the TCP protocol, create a transport object by using the **New-CsSipProxyTCP** cmdlet. To use the TLS protocol, create a transport object by using the **New-CsSipProxyTLS** cmdlet. <br/> |
   
## Input Types

None. The **New-CsSipProxyTransport** cmdlet does not accept pipelined input.
  
## Return Types

The **New-CsSipProxyTransport** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.Transport object.
  
## See also

#### 

[New-CsSipProxyTCP](new-cssipproxytcp.md)
  
[New-CsSipProxyTLS](new-cssipproxytls.md)

