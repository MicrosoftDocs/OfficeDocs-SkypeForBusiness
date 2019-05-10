---
title: 'Lync Server 2013: Configure a static route for remote call control'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configure a static route for remote call control
ms:assetid: f7003023-443d-48ee-989b-71e8b0b0abbd
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg615051(v=OCS.15)
ms:contentKeyID: 48185855
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure a static route for remote call control in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-22_

Remote call control requires that every Lync Server pool is configured with a path from that pool to the SIP/CSTA gateway that connects to the private branch exchange (PBX). This path requires that each pool has one static route for each gateway to which the pool will proxy SIP call control messages associated with calls to the PBX. If you configure a global static route for remote call control, each pool that is not configured with a static route at the pool level will use the global static route.

<div>

## To configure a static route for remote call control

1.  Log on to a computer where Lync Server Management Shell is installed as a member of the RTCUniversalServerAdmins group or a role-based access control (RBAC) role to which you have assigned the **New-CsStaticRoute** cmdlet.

2.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

3.  To create a static route and put it in the variable $TLSRoute or $TCPRoute, do one of the following:
    
    <div class="">
    

    > [!TIP]  
    > To match child domains of a domain, you can specify a wildcard value in the MatchUri parameter. For example, <STRONG>*.contoso.net</STRONG>. That value matches any domain that ends with the suffix <STRONG>contoso.net</STRONG>.

    
    </div>
    
      - For a Transport Layer Security (TLS) connection, type the following at the command prompt:
        
            $TLSRoute = New-CsStaticRoute -TLSRoute -Destination <gateway FQDN> -Port <gateway SIP listening port> -UseDefaultCertificate $true -MatchUri <destination domain>
        
        For example:
        
            $TLSRoute = New-CsStaticRoute -TLSRoute -Destination rccgateway.contoso.net -Port 5065 -UseDefaultCertificate $true -MatchUri *.contoso.net
        
        If UseDefaultCertificate is set to False, you must specify TLSCertIssuer and TLSCertSerialNumber parameters. These parameters indicate the name of the certification authority (CA) that issued the certificate used in the static route, and the serial number of that TLS certificate, respectively. For details about these parameters, see Lync Server Management Shell Help by typing the following at the command prompt:
        
            Get-Help New-CsStaticRoute -Full
    
      - For a Transmission Control Protocol (TCP) connection, type the following at the command prompt:
        
        <div class="">
        

        > [!NOTE]  
        > If you specify a fully qualified domain name (FQDN), you must configure a Domain Name System (DNS) A record first.

        
        </div>
        
            $TCPRoute = New-CsStaticRoute -TCPRoute -Destination <gateway IP address or FQDN> -Port <gateway SIP listening port> -MatchUri <destination domain>
        
        For example:
        
            $TCPRoute = New-CsStaticRoute -TCPRoute -Destination 192.168.0.240 -Port 5065 -MatchUri *.contoso.net
        
        The following are default values for optional parameters for static routes:
        
          - Enabled = True
        
          - MatchOnlyPhoneUri = False
        
          - ReplaceHostInRequestUri = False
        
        We strongly recommend that you do not change these default values. However, if you must change any of these parameters, see Lync Server Management Shell Help by typing the following at the command prompt:
        
            Get-Help New-CsStaticRoute -Full

4.  To persist a newly created static route in the Central Management store, run one of the following, as appropriate:
    
       ```
        Set-CsStaticRoutingConfiguration -Route @{Add=$TLSRoute}
       ```
    
       ```
        Set-CsStaticRoutingConfiguration -Route @{Add=$TCPRoute}
       ```

</div>

<div>

## See Also


[Configure a trusted application entry for remote call control in Lync Server 2013](lync-server-2013-configure-a-trusted-application-entry-for-remote-call-control.md)  
[Define a SIP/CSTA gateway IP address in Lync Server 2013](lync-server-2013-define-a-sip-csta-gateway-ip-address.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

