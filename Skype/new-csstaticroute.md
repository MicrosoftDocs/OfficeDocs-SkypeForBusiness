---
title: New-CsStaticRoute
ms.prod: SKYPEFORBUSINESS
ms.assetid: 1df0c537-f24f-4a63-be6d-70d016f985a5
---


# New-CsStaticRoute
[]
Creates a new static phone route. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

New-CsStaticRoute -Destination <String> -MatchUri <String> -Port <UInt16> -TLSRoute <SwitchParameter> [-Enabled <$true | $false>] [-MatchOnlyPhoneUri <$true | $false>] [-ReplaceHostInRequestUri <$true | $false>] [-TLSCertIssuer <String>] [-TLSCertSerialNumber <Byte[]>] [-UseDefaultCertificate <$true | $false>] <COMMON PARAMETERS>

```


## Examples


  
    
    

### EXAMPLE 1

The commands shown in Example 1 create a new static route and then add that route to the global static routing configuration collection. To carry out this task, the first command uses the **New-CsStaticRoute** cmdlet to create an in-memory-only route that uses TCP as its transport protocol. The route points to the next hop IP address 192.168.0.100, uses port 8025, and matches any URI from the domain litwareinc.com. The resulting route object is stored in a variable named $x.
  
    
    
The second command in the example then adds the new route to the global static routing configuration collection. This is done by calling the **Set-CsStaticRoutingConfiguration** cmdlet along with the Route parameter. The parameter value @{Add=$x} adds the route object stored in $x to the existing set of routes already in the global collection.
  
    
    



```

$x = New-CsStaticRoute -TCPRoute -Destination "192.168.0.100" -Port 8025 -MatchUri "litwareinc.com"

Set-CsStaticRoutingConfiguration -Identity global -Route @{Add=$x}

```


### EXAMPLE 2

Example 2 shows how you can create a new static route that uses TLS as its transport protocol, and then add that route to the global static routing configuration collection. To do this, the first command in the example uses the **New-CsStaticRoute** cmdlet to create an in-memory-only route that uses TLS as its transport protocol. The route points to the "atl-proxy-001.litwareinc.com" as its destination, uses port 8025, and matches any URI that uses the domain suffix "litwareinc.com". In addition, the new route object, which is stored in a variable named $x, uses the default certificate for authentication purposes (-UseDefaultCertificate $True).
  
    
    
After the route object has been created, the second command in the example then adds the new route to the global static routing configuration collection.
  
    
    



```

$x = New-CsStaticRoute -TLSRoute -Destination "atl-proxy-001.litwareinc.com" -Port 8025 -MatchUri "*.litwareinc.com" -UseDefaultCertificate $True

Set-CsStaticRoutingConfiguration -Identity global -Route @{Add=$x}

```


### EXAMPLE 3

Example 3 creates a new static route using TLS and a specific certificate; this is indicated by included the required TLS parameters.
  
    
    
After the route object has been created, the second command in the example then adds the new route to the global static routing configuration collection.
  
    
    



```

$x = New-CsStaticRoute -TLSRoute -Destination "atl-proxy.litwareinc.com" -Port 5061 -MatchUri "litwareinc.com" -UseDefaultCertificate $False -TLSCertIssuer "CN=CertificateAuthority, DC=litwareinc, DC=com" -TLSCertSerialNumber 0x8f,0x33,0x70,0x93,0x70,0x05,0x33,0x00,0x02,0x33

Set-CsStaticRoutingConfiguration -Identity global -Route @{Add=$x}

```


## Detailed Description

When you send a SIP message to someone that message might need to traverse multiple subnets and networks before it is delivered; the path traveled by the message is often referred to as a route. In networking, there are two types of routes: dynamic and static. With dynamic routing, servers use algorithms to determine the next location (the next hop) where the message should be forwarded. With static routing, message paths are predetermined by system administrators. When a message is received by a server, the server checks the message address and then forwards the message to the next hop server that has been preconfigured by an administrator. If configured correctly, static routes help ensure timely, and accurate, delivery of messages, and with minimal overheard placed on servers. The downside to static routes is that messages are not dynamically rerouted in the event of a network failure.
  
    
    
New static routes are created by using the **New-CsStaticRoute** cmdlet. After a route has been created by using the **New-CsStaticRoute** cmdlet, you must then add the route to a collection of routing configuration settings by using the **Set-CsStaticRoutingConfiguration** cmdlet.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Destination_ <br/> |Required  <br/> |System.String  <br/> |If the route uses Transport Layer Security (TLS) as the transport protocol, then the Destination is the fully qualified domain name (FQDN) of the next hop server. For example:  `-Destination "atl-proxy-001.litwareinc.com"` <br/> If the route uses Transmission Control Protocol (TCP) as the transport protocol, then the Destination is the IP address of the next hop router. For example: -Destination "192.168.0.240".  <br/> |
| _MatchUri_ <br/> |Required  <br/> |System.String  <br/> |FQDN or domain suffix used to determine if the message is being sent to a user handled by this route. For example, you might use the FQDN "litwareinc.com". This pattern matches any user who has a SIP address that ends with the domain name "litwareinc.com".  <br/> To match child domains of a domain, you can use a wildcard value like "*.litwareinc.com". That value matches any domain that ends with the suffix "litwareinc.com". For example: northamerica.litwareinc.com; asia.litwareinc.com; and europe.litwareinc.com.  <br/> |
| _Port_ <br/> |Required  <br/> |System.UInt16  <br/> |Port number used for SIP routing. For example:  `-Port 7742` <br/> |
| _TCPRoute_ <br/> |Required  <br/> |System.Management.Automation.SwitchParameter  <br/> |Configures TCP as the transport protocol for the new route.  <br/> |
| _TLSRoute_ <br/> |Required  <br/> |System.Management.Automation.SwitchParameter  <br/> |Configures TLS as the transport protocol for the new route.  <br/> |
| _Enabled_ <br/> |Optional  <br/> |System.Boolean  <br/> |If set to True, then the route is enabled, and any messages matching the MatchURI pattern will be routed to the next hop server. If set to False, the route is disabled and will not be used in routing messages. The default value is True.  <br/> |
| _MatchOnlyPhoneUri_ <br/> |Optional  <br/> |System.Boolean  <br/> |If set to True, only messages addressed to phone Uniform Resource identifiers (URIs) (for example, sip:kenmmyer@litwareinc.com;user=phone) will be matched and, potentially, routed. If set to False (the default value) then all messages will be matched.  <br/> |
| _ReplaceHostInRequestUri_ <br/> |Optional  <br/> |System.Boolean  <br/> |If set to True ($True) then the host portion of a Request-URI will be replaced by the address of the next hop server. If set the False then the Request-URI will be used as-is. The Request-URI represents the URI of the user or service that the request (message) is addressed to. The default value is False.  <br/> |
| _TLSCertIssuer_ <br/> |Optional  <br/> |System.String  <br/> |Name of the certification authority (CA) that issued the certificate to be used in the static route. This parameter is not used if you have configured TCP as the transport protocol.  <br/> If you include the TLSCertIssuer parameter then you must also use the TLSCertSerialNumber parameter.  <br/> |
| _TLSCertSerialNumber_ <br/> |Optional  <br/> |System.Byte[]  <br/> |Serial number of the TLS certificate to be used in the static route. Serial numbers must be passed as a byte array; this means you must pass the serial number as an array of two-character values. For example:  `-TLSCertSerialNumber 0x01, 0xA4, 0xD5, 0x67, 0x89` <br/> This parameter is not used if you have configured TCP as the transport protocol.  <br/> If you include the TLSCertSerialNumber parameter then you must also use the TLSCertIssuer parameter.  <br/> |
| _UseDefaultCertificate_ <br/> |Optional  <br/> |System.Boolean  <br/> |Configures the route to use your default Skype for Business Server 2015 certificate as its authentication certificate. If you do not want to use the default certificate then you must specify a different certificate by using the TLSCertIssuer and TLSCertSerialNumber parameters.  <br/> To view the default certificate, use the following command:  <br/>  `Get-CsCertificate | Where-Object {$_.Use -eq "urn:certref:Default"}` <br/> |
   

## Input Types

None. The **New-CsStaticRoute** cmdlet does not accept pipelined input.
  
    
    

## Return Types

The **New-CsStaticRoute** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.Route object.
  
    
    

## See also


#### 


  
    
    
 [New-CsStaticRoutingConfiguration](new-csstaticroutingconfiguration.md)
  
    
    
 [Set-CsStaticRoutingConfiguration](set-csstaticroutingconfiguration.md)
