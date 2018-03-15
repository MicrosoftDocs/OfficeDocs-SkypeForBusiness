---
title: "Static routing cmdlets in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 71d5e0cd-8412-4383-818a-95b851a4da4b
description: "With static routes, administrators can predetermine the network routes taken by SIP messages. When a message is received by a server, the server checks the message address and then forwards the message to the next hop server preconfigured by an administrator. If configured correctly, static routes help ensure timely, and accurate, delivery of messages, and with minimal overheard placed on servers."
---

# Static routing cmdlets in Lync Server 2013
[]
With static routes, administrators can predetermine the network routes taken by SIP messages. When a message is received by a server, the server checks the message address and then forwards the message to the next hop server preconfigured by an administrator. If configured correctly, static routes help ensure timely, and accurate, delivery of messages, and with minimal overheard placed on servers.
  
## Static Routing Cmdlets

Unless otherwise instructed by Microsoft support personnel, static routes configured for Microsoft Lync Server 2013 should be created using the [New-CsStaticRoute](new-csstaticroute.md) cmdlet. After a route has been created, you can then use the CsStaticRoutingConfiguration cmdlets to add that route to a static routing collection. 
  
 **Static Routing**
  
> [Get-CsSipResponseCodeTranslationRule](get-cssipresponsecodetranslationrule.md)
    
> [New-CsSipResponseCodeTranslationRule](new-cssipresponsecodetranslationrule.md)
    
> [Remove-CsSipResponseCodeTranslationRule](remove-cssipresponsecodetranslationrule.md)
    
> [Set-CsSipResponseCodeTranslationRule](set-cssipresponsecodetranslationrule.md)
    
> [New-CsStaticRoute](new-csstaticroute.md)
    
> [Get-CsStaticRoutingConfiguration](get-csstaticroutingconfiguration.md)
    
> [New-CsStaticRoutingConfiguration](new-csstaticroutingconfiguration.md)
    
> [Remove-CsStaticRoutingConfiguration](remove-csstaticroutingconfiguration.md)
    
> [Set-CsStaticRoutingConfiguration](set-csstaticroutingconfiguration.md)
    
> [New-CsSipProxyCustom](new-cssipproxycustom.md)
    
> [New-CsSipProxyRealm](new-cssipproxyrealm.md)
    
> [New-CsSipProxyTCP](new-cssipproxytcp.md)
    
> [New-CsSipProxyTLS](new-cssipproxytls.md)
    
> [New-CsSipProxyTransport](new-cssipproxytransport.md)
    
> [New-CsSipProxyUseDefault](new-cssipproxyusedefault.md)
    
> [New-CsSipProxyUseDefaultCert](new-cssipproxyusedefaultcert.md)
    
> [New-CsIssuedCertId](new-csissuedcertid.md)
    
## See also

#### 

[Lync Server PowerShell Blog](https://go.microsoft.com/fwlink/p/?linkId=203150)

