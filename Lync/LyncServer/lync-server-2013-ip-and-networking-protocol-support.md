---
title: 'Lync Server 2013: IP and networking protocol support'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: IP and networking protocol support
ms:assetid: b0cffb10-3478-445c-89c7-8cb8b5027424
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412848(v=OCS.15)
ms:contentKeyID: 48185128
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# IP and networking protocol support in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-21_

Lync Server 2013 supports the following IP and networking protocols:

  - **IP Protocols.**   Lync Server 2013 supports either IP version 4 (IPv4) or IP version 6 (IPv6) for the server network.
    
    <div>
    

    > [!NOTE]  
    > Lync Server 2013 can function in a network with dual IP stack enabled.

    
    </div>

  - **SIP Transport Protocols.**   Generically, SIP can use at least three transport types: User Datagram Protocol (UDP), Transmission Control Protocol (TCP), and Transport Layer Security (TLS). In the default SIP transport configuration, TLS runs over TCP. TLS is used within the Lync Server 2013 network. At the edge of the network, Lync Server 2013 can interoperate over TCP. Lync Server 2013 does not support UDP for SIP transport because it doesn’t meet the minimum standards for enterprise communications security, reliability, and scalability. For details, see the NextHop blog article, "To UDP, or not to UDP, that is the question," at [http://go.microsoft.com/fwlink/p/?linkId=185369](http://go.microsoft.com/fwlink/p/?linkid=185369).
    
    <div>
    

    > [!NOTE]  
    > The content of each blog and its URL are subject to change without notice.

    
    </div>

</div>

<span> </span>

</div>

</div>

</div>

