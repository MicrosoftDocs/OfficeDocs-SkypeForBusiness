---
title: 'Lync Server 2013: Hybrid and split-domain - Autodiscover'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Hybrid and split-domain - Autodiscover
ms:assetid: c855bcc5-b656-4d2d-92d6-f016f2797d3a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ945652(v=OCS.15)
ms:contentKeyID: 51541520
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Hybrid and split-domain - Autodiscover in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-14_

A shared SIP address space, also known as a *split-domain* deployment, or a *hybrid* deployment, is a configuration where users are deployed across an on-premise deployment and an online environment. The desired outcome is to have a user, regardless of where their home server is located (on-premise or online), log into the deployment and be redirected to their home server location. To accomplish this, the Autodiscover feature of Lync Server 2013 is used to redirect the online user to the online topology. You can do this by configuring the Autodiscover uniform resource locator (URL) by using the Lync Server Management Shell, the **Get-CsHostingProvider** cmdlet, and the **Set-CsHostingProvider** cmdlet.

<div>

## Mobility for the Split Domain Deployment

You will need to collect and record the following deployed attributes:

  - From the Lync Server Management Shell, type
    
        Get-CsHostingProvider

  - In the results, find the online provider with the attribute **ProxyFQDN**. For example, sipfed.online.lync.com.

  - Record the value of the ProxyFQDN.

  - Enable federation in the on-premise Lync Server Control Panel, allowing federation with the online provider.

  - Enable federation for the online provider. By default, all online users are enabled for domain federation and can communicate with all domains.

  - If you will define blocked and allowed domains, determine the domains that you will explicitly allow or explicitly block.

  - For online federation, you must plan for firewall exceptions, certificates, and DNS host (A or AAAA, if using IPv6) records. Additionally, you must configure federation policies. For details, see [Planning for Lync Server 2013 and Office Communications Server federation](lync-server-2013-planning-for-lync-server-and-office-communications-server-federation.md).

</div>

</div>

<span> </span>

</div>

</div>

</div>

