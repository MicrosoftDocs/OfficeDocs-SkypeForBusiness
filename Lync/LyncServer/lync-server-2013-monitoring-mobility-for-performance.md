---
title: 'Lync Server 2013: Monitoring mobility for performance'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Monitoring mobility for performance
ms:assetid: 9c831c63-9a7d-48ec-9118-f8a7e80ddd04
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Hh690033(v=OCS.15)
ms:contentKeyID: 48184908
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Monitoring mobility for performance in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-14_

The Lync Server Mobility Service (Mcx) and the Unified Communications Web API (UCWA) increase the load on Front End Servers and Front End pools. Mobile devices that maintain a connection to the server even when the mobile application is minimized, such as Android and Nokia devices running Lync 2010 Mobile, as well as Android and Apple devices running Lync 2013 Mobile, impose a greater load than devices that terminate their connection to the server when the mobile application is minimized. As your mobility usage increases, you must monitor mobility performance to determine when you need to increase your capacity.

Several limits influence mobility performance:

  - Available memory

  - Request queue limit

  - Concurrent connections

  - IIS queue length

Other limits on servers that can influence mobility performance are a maximum of twelve concurrent sign-ins, authentications, session renewals, and terminations. These maximums do not need to be modified for most deployments.

<div>

## In This Section

  - [Monitoring for server memory capacity limits in Lync Server 2013](lync-server-2013-monitoring-for-server-memory-capacity-limits.md)

  - [Monitoring Mobility Service and UCWA usage in Lync Server 2013](lync-server-2013-monitoring-mobility-service-and-ucwa-usage.md)

  - [Configuring Mobility Service for high performance in Lync Server 2013](lync-server-2013-configuring-mobility-service-for-high-performance.md)

  - [Monitoring IIS request tracing log files in Lync Server 2013](lync-server-2013-monitoring-iis-request-tracing-log-files.md)

  - [Mobility performance counters in Lync Server 2013](lync-server-2013-mobility-performance-counters.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

