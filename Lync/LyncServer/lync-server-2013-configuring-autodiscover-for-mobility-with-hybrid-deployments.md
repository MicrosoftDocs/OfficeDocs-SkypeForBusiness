---
title: 'Configuring Autodiscover for mobility with hybrid deployments'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configuring Autodiscover for mobility with hybrid deployments
ms:assetid: f838af79-d8b4-4122-b81c-7889573d143e
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ215885(v=OCS.15)
ms:contentKeyID: 48706012
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring Autodiscover in Lync Server 2013 for mobility with hybrid deployments

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-06-18_

Hybrid Deployments are configurations that use both the Microsoft Lync Online cloud service and the on premises deployment. In this type of configuration, the Autodiscover service must be able to locate where the user is actually located. That is to say, Autodiscover aids in finding the user account and where the server that hosts the user’s account is, regardless if it is in the on premises deployment or in the Lync Online deployment.

For example, if a user’s account is hosted on a server in Lync Online, the attempt to locate the user will happen as follows, in a process known as *discoverability*:

  - User initiates a connection attempt to the on premises deployment, **contoso.com**.

  - The attempt is sent to lyncdiscover.contoso.com, the DNS name associated with the Autodiscover service.

  - Autodiscover refers to the assumed registrar pool at the contoso.com on premises deployment and is given information on the user’s actual home server hosted in Lync Online. Autodiscover then sends the user a referral to the **lync.com** online Autodiscover service.

  - The user initiates a connection attempt to the lync.com online Autodiscover service and is able to locate the user’s account and the user’s home server.

To enable mobile clients to discover the deployment where the user home server is located, you must configure the Autodiscover service with a new uniform resource locator (URL). Do the following to configure the Autodiscover service.

<div>

## Configuring Autodiscover for Hybrid Deployments

1.  You use Get-CsHostingProvider to retrieve the value of the attribute ProxyFQDN.

2.  From the Lync Server Management Shell, type
    
        Set-CsHostingProvider -Identity [identity] -AutodiscoverUrl https://webdir.online.lync.com/autodiscover/autodiscoverservice.svc/root
    
    Where \[identity\] is replaced with the domain name of the shared SIP address space.

</div>

<div>

## See Also


[Get-CsHostingProvider](https://technet.microsoft.com/en-us/library/Gg413078(v=OCS.15))  
[Set-CsHostingProvider](https://technet.microsoft.com/en-us/library/Gg398532(v=OCS.15))  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

