---
title: 'Lync Server 2013: Configuring Mobility Service for high performance'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Configuring Mobility Service for high performance
ms:assetid: c2b8aadb-cffb-49f0-ba7a-e8541a1ff475
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Hh690042(v=OCS.15)
ms:contentKeyID: 48185332
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring Mobility Service for high performance in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-17_

<div>


> [!IMPORTANT]  
> This topic applies only to the Lync Server 2013 Mobility Service (Mcx), and does not apply to Unified Communications Web API (UCWA), as delivered in the Cumulative Updates for Lync Server 2013: February 2013.



</div>

When you install the Mobility Service (Mcx) on Internet Information Services (IIS) 7.5, the Mobility Service installer configures some performance settings on the Front End Server. We recommend that you use IIS 7.5 for mobility. The settings affect the maximum number of concurrent user requests and the maximum number of threads that are allowed for the Mobility Service.

Here are the performance settings:

<div>

## Settings for Mcx on IIS 7.5

1.  **maxConcurrentThreadsPerCPU** is set to zero (0).

2.  **maxConcurrentRequestsPerCPU** is set to zero (0).

3.  ASP.NET process model is set to AutoConfig (for IIS 7.5 only).

4.  HTTP.sys queue limit is set to 1,000 (by default).

</div>

</div>

<span> </span>

</div>

</div>

</div>

