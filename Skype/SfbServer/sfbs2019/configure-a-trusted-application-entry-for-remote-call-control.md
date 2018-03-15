---
title: "Configure a trusted application entry for remote call control in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/2/2015
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 37777f93-8b24-40cf-808e-7c6230eb2132
description: "The SIP/CSTA gateway must be configured as a trusted application in order for Lync Server to apply a static route to route calls to the gateway."
---

# Configure a trusted application entry for remote call control in Lync Server 2013
[]
The SIP/CSTA gateway must be configured as a trusted application in order for Lync Server to apply a static route to route calls to the gateway.
  
> [!IMPORTANT]
> If you're migrating users from a previous version of Lync Server deployment, be sure that you removed all existing trusted application entries (previously known as authorized host entries) you created for the SIP/CSTA gateway before following the procedures in this topic. For details, see [Remove a legacy authorized host in Lync Server 2013 (optional)](remove-a-legacy-authorized-host-optional.md). > If you plan to deploy new remote call control by using a Transmission Control Protocol (TCP) connection, you need to verify that **Limit service usage to selected IP addresses** should be set on existing trusted applications and pools, if you want to use the same TCP port for the new trusted application. 
  
### To configure a trusted application entry for the SIP/CSTA gateway

1. Log on to the computer where Lync Server Management Shell is installed as a member of the RTCUniversalServerAdmins group or a role-based access control (RBAC) role to which you have assigned the **New-CsTrustedApplicationPool** cmdlet. 
    
2. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
3. To create a trusted application entry, do one of the following:
    
  - For a Transport Layer Security (TLS) connection, type the following at the command prompt:
    
  ```
  New-CsTrustedApplicationPool -Identity <FQDN of the SIP/CSTA gateway> [-Registrar <Service ID or FQDN of the Registrar service>] -Site <Site ID for the site where you want to create the trusted application pool>
  ```

    For example:
    
  ```
  New-CsTrustedApplicationPool -Identity rccgateway.contoso.net -Registrar registrar1.contoso.net -Site co1 -TreatAsAuthenticated $true -ThrottleAsServer $true
  ```

  - For a Transmission Control Protocol (TCP) connection, type the following at the command prompt:
    
  ```
  New-CsTrustedApplicationPool -Identity <IP address or FQDN of the SIP/CSTA gateway> [-Registrar <Service ID or FQDN of the Registrar service>] -Site <Site ID for the site where you want to create the trusted application pool>
  ```

    For example:
    
  ```
  New-CsTrustedApplicationPool -Identity 192.168.0.240 -Registrar registrar1.contoso.net -Site co1 -TreatAsAuthenticated $true -ThrottleAsServer $true
  ```

4. To add the trusted application to the pool, do one of the following:
    
  - For a TLS connection, type the following at the command prompt:
    
  ```
  New-CsTrustedApplication -ApplicationID <application name> -TrustedApplicationPoolFqdn <FQDN of the SIP/CSTA gateway> -Port <SIP listening port on the gateway>
  ```

    For example:
    
  ```
  New-CsTrustedApplication -ApplicationID RccGateway-1 -TrustedApplicationPoolFqdn rccgateway.contoso.net -Port 5065
  ```

  - For a TCP connection, type the following at the command prompt:
    
  ```
  New-CsTrustedApplication -ApplicationID <application name> -TrustedApplicationPoolFqdn <IP address or FQDN of the SIP/CSTA gateway> -Port <SIP listening port on the gateway> -EnableTcp
  ```

    For example:
    
  ```
  New-CsTrustedApplication -ApplicationID RccGateway-1 -TrustedApplicationPoolFqdn 192.169.0.240 -Port 5065 -EnableTcp
  ```

5. To implement the published changes you have made to the topology, type the following at the command prompt:
    
  ```
  Enable-CsTopology
  ```

## See also

#### 

[Configure a static route for remote call control in Lync Server 2013](configure-a-static-route-for-remote-call-control.md)
  
[Define a SIP/CSTA gateway IP address in Lync Server 2013](define-a-sip-csta-gateway-ip-address.md)

