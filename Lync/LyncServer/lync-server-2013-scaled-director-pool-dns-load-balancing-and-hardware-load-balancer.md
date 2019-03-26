---
title: 'Scaled Director pool - DNS load balancing and hardware load balancer'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Scaled Director pool - DNS load balancing and hardware load balancer
ms:assetid: a1f6ffc0-9e6e-4217-a923-025c9679e154
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205142(v=OCS.15)
ms:contentKeyID: 48185023
ms.date: 03/29/2016
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Scaled Director pool - DNS load balancing and hardware load balancer in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-22_

A scaled Director pool, where there are more than one Director deployed to handle additional capacity and to provide high availability, requires load balancing to distribute client and server communication to all members of the pool. A Director hosts web services much like a Front End pool. To provide the load balancing, you can use either hardware load balancing or domain name system (DNS) load balancing and hardware load balancing. Hardware load balancing is required for the web services, and DNS load balancing alone does not provide the capabilities required for the web services.

The following topics describe the planning considerations for deploying a Director pool using DNS load balancing in conjunction with hardware load balancing. If you intend to use hardware load balancing, but not DNS load balancing for the Director pool, see the topic [Scaled Director pool - hardware load balancer in Lync Server 2013](lync-server-2013-scaled-director-pool-hardware-load-balancer.md) that describes the planning requirements for that topology.

![Scaled Director Pool](images/JJ205142.35a78a7a-b781-4c8f-951e-168451ba6a65(OCS.15).jpg "Scaled Director Pool")

<div>

## In This Section

  - [Certificate summary - DNS and HLB load balanced in Lync Server 2013](lync-server-2013-certificate-summary-dns-and-hlb-load-balanced.md)

  - [Port summary - DNS and HLB load balanced in Lync Server 2013](lync-server-2013-port-summary-dns-and-hlb-load-balanced.md)

  - [DNS summary - DNS and HLB load balanced in Lync Server 2013](lync-server-2013-dns-summary-dns-and-hlb-load-balanced.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

