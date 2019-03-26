---
title: Lync Server 2013 compatibility with Lync Server 2010 metropolitan site resiliency
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Lync Server 2010 metropolitan site resiliency
ms:assetid: 18673ff6-b664-4a57-a89b-cbda8b129e6a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204715(v=OCS.15)
ms:contentKeyID: 48183526
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Lync Server 2010 metropolitan site resiliency

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-03-19_

The metropolitan site resiliency solution supported for Lync Server 2010 is not supported for Lync Server 2013. This solution involved spanning a single Front End pool across two data centers in the same metropolitan area.

The metropolitan site resiliency solution was designed to recover from the loss of a full datacenter. When you span your pool across two datacenters, you typically put half of your front ends in one datacenter and the other half in the second datacenter. If you lose an entire datacenter, you have lost half of your Front End Servers. This can cause issues with the new distributed system model for Front End Pools in Lync Server 2013. For more information, see [Topologies and components for Front End Servers, instant messaging, and presence in Lync Server 2013](lync-server-2013-topologies-and-components-for-front-end-servers-instant-messaging-and-presence.md).

</div>

<span> </span>

</div>

</div>

</div>

