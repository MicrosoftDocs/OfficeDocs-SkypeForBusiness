---
title: "IP and networking protocol support in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b0cffb10-3478-445c-89c7-8cb8b5027424
description: "Lync Server 2013 supports the following IP and networking protocols:"
---

# IP and networking protocol support in Lync Server 2013
[]
Lync Server 2013 supports the following IP and networking protocols:
  
- **IP Protocols.** Lync Server 2013 supports either IP version 4 (IPv4) or IP version 6 (IPv6) for the server network. 
    
    > [!NOTE]
    > Lync Server 2013 can function in a network with dual IP stack enabled. 
  
- **SIP Transport Protocols.** Generically, SIP can use at least three transport types: User Datagram Protocol (UDP), Transmission Control Protocol (TCP), and Transport Layer Security (TLS). In the default SIP transport configuration, TLS runs over TCP. TLS is used within the Lync Server 2013 network. At the edge of the network, Lync Server 2013 can interoperate over TCP. Lync Server 2013 does not support UDP for SIP transport because it doesn't meet the minimum standards for enterprise communications security, reliability, and scalability. For details, see the NextHop blog article, "To UDP, or not to UDP, that is the question," at [https://go.microsoft.com/fwlink/p/?linkId=185369](https://go.microsoft.com/fwlink/p/?linkId=185369).
    
    > [!NOTE]
    > The content of each blog and its URL are subject to change without notice. 
  

