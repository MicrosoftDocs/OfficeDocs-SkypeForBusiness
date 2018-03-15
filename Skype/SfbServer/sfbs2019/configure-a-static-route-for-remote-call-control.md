---
title: "Configure a static route for remote call control in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f7003023-443d-48ee-989b-71e8b0b0abbd
description: "Remote call control requires that every Lync Server pool is configured with a path from that pool to the SIP/CSTA gateway that connects to the private branch exchange (PBX). This path requires that each pool has one static route for each gateway to which the pool will proxy SIP call control messages associated with calls to the PBX. If you configure a global static route for remote call control, each pool that is not configured with a static route at the pool level will use the global static route."
---

# Configure a static route for remote call control in Lync Server 2013
[]
Remote call control requires that every Lync Server pool is configured with a path from that pool to the SIP/CSTA gateway that connects to the private branch exchange (PBX). This path requires that each pool has one static route for each gateway to which the pool will proxy SIP call control messages associated with calls to the PBX. If you configure a global static route for remote call control, each pool that is not configured with a static route at the pool level will use the global static route.
  
### To configure a static route for remote call control

1. Log on to a computer where Lync Server Management Shell is installed as a member of the RTCUniversalServerAdmins group or a role-based access control (RBAC) role to which you have assigned the **New-CsStaticRoute** cmdlet. 
    
2. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
3. To create a static route and put it in the variable $TLSRoute or $TCPRoute, do one of the following:
    
    > [!TIP]
    > To match child domains of a domain, you can specify a wildcard value in the MatchUri parameter. For example, **\*.contoso.net**. That value matches any domain that ends with the suffix **contoso.net**. 
  
  - For a Transport Layer Security (TLS) connection, type the following at the command prompt:
    
  ```
  $TLSRoute = New-CsStaticRoute -TLSRoute -Destination <gateway FQDN> -Port <gateway SIP listening port> -UseDefaultCertificate $true -MatchUri <destination domain>
  ```

    For example:
    
  ```
  $TLSRoute = New-CsStaticRoute -TLSRoute -Destination rccgateway.contoso.net -Port 5065 -UseDefaultCertificate $true -MatchUri *.contoso.net
  ```

    If UseDefaultCertificate is set to False, you must specify TLSCertIssuer and TLSCertSerialNumber parameters. These parameters indicate the name of the certification authority (CA) that issued the certificate used in the static route, and the serial number of that TLS certificate, respectively. For details about these parameters, see Lync Server Management Shell Help by typing the following at the command prompt:
    
  ```
  Get-Help New-CsStaticRoute -Full
  ```

  - For a Transmission Control Protocol (TCP) connection, type the following at the command prompt:
    
    > [!NOTE]
    > If you specify a fully qualified domain name (FQDN), you must configure a Domain Name System (DNS) A record first. 
  
  ```
  $TCPRoute = New-CsStaticRoute -TCPRoute -Destination <gateway IP address or FQDN> -Port <gateway SIP listening port> -MatchUri <destination domain>
  ```

    For example:
    
  ```
  $TCPRoute = New-CsStaticRoute -TCPRoute -Destination 192.168.0.240 -Port 5065 -MatchUri *.contoso.net
  ```

    The following are default values for optional parameters for static routes:
    
  - Enabled = True
    
  - MatchOnlyPhoneUri = False
    
  - ReplaceHostInRequestUri = False
    
    We strongly recommend that you do not change these default values. However, if you must change any of these parameters, see Lync Server Management Shell Help by typing the following at the command prompt:
    
  ```
  Get-Help New-CsStaticRoute -Full
  ```

4. To persist a newly created static route in the Central Management store, run one of the following, as appropriate:
    
  ```
  Set-CsStaticRoutingConfiguration -Route @{Add=$TLSRoute}
  ```

  ```
  Set-CsStaticRoutingConfiguration -Route @{Add=$TCPRoute}
  ```

## See also

#### 

[Configure a trusted application entry for remote call control in Lync Server 2013](configure-a-trusted-application-entry-for-remote-call-control.md)
  
[Define a SIP/CSTA gateway IP address in Lync Server 2013](define-a-sip-csta-gateway-ip-address.md)

