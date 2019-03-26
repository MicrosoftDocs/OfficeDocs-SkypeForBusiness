---
title: 'Lync Server 2013: Components required for the Director'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Components required for the Director
ms:assetid: 15c7c8d4-b93f-4386-b2d1-d76dab8f801e
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398228(v=OCS.15)
ms:contentKeyID: 48183502
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Components required for the Director in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-08_

The only component required to create and configure a Director is to deploy the Director server role. You do this by using Topology Builder and define either a single computer pool or a multiple computer pool in the Director pool node. After you have defined the Director or Director pool, run the Lync Server Deployment Wizard on the computer that will be a Director. In the case of a Director pool, you run the Lync Server Deployment Wizard on each server that will be a member of the pool.

<div>

## Topologies

You can implement a single Director server or a Director pool. The Director is always a separate server or pool, not collocated with any other server role in Lync Server 2013.

<div>


> [!NOTE]  
> If you do not deploy Directors, the Front End Server or Front End pool will assume the Director role.



</div>

A pool of Directors must be load balanced. You can do one of the following:

  - Create a topology that uses a hardware load balancer for web services and Domain Name System (DNS) load balancing for the other traffic types.
    
    [Scaled Director pool - DNS load balancing and hardware load balancer in Lync Server 2013](lync-server-2013-scaled-director-pool-dns-load-balancing-and-hardware-load-balancer.md)

  - Create a topology that uses a hardware load balancer for load balancing needed for the Director pool.
    
    [Scaled Director pool - hardware load balancer in Lync Server 2013](lync-server-2013-scaled-director-pool-hardware-load-balancer.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

