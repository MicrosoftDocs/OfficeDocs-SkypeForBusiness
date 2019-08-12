---
title: 'Lync Server 2013: Monitoring Mobility Service and UCWA usage'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Monitoring Mobility Service and UCWA usage
ms:assetid: 8389b37a-ca3e-4047-8b51-85bc07da87e8
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Hh690025(v=OCS.15)
ms:contentKeyID: 48184683
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Monitoring Mobility Service and UCWA usage in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-14_

On an ongoing basis, you should monitor the CPU and memory that is used by the Lync Server Mobility Service (Mcx) and the Unified Communications Web API (UCWA). To monitor usage, you can use the following:

**For Unified Communications Web API (UCWA):**

  - The **LyncUcwa** worker process in Internet Information Services (IIS) Manager. In the **Worker Processes** pane, look at the **CPU %** and **Private Bytes (KB)** (memory) columns.

  - The **CPU** and **Processor** performance counters.

For most deployments, UCWA CPU usage should be below 15 percent on average. Memory usage should fall within the limits described in [Monitoring for server memory capacity limits in Lync Server 2013](lync-server-2013-monitoring-for-server-memory-capacity-limits.md).

In addition to CPU and memory usage counters, you can use the following performance counters to help determine when a server is overloaded with requests:

  - **LS:WEB – Throttling and Authentication\\WEB – Total Requests in Processing**, which indicates the number of pending web requests on the server. When this counter reaches 10,000, subsequent requests will fail, with the error message, "503 - Service Unavailable."

  - **ASP.NET\\Requests Queued** (should always be zero).

<div>


> [!NOTE]  
> If you meet or exceed these values, you should revisit and re-compute your capacity planning for the correct sizing of CPU, number of cores and memory for the computers hosting the Web services.



</div>

**For the Mobility Service (Mcx):**

  - The **CSIntMcxAppPool** and **CSExtMcxAppPool** worker processes in Internet Information Services (IIS) Manager. In the **Worker Processes** pane, look at the **CPU %** and **Private Bytes (KB)** (memory) columns.

  - The **CPU** and **Processor** performance counters.

For most deployments, Mobility Service CPU usage should be below 15 percent, on average. Memory usage should fall within the limits described in [Monitoring for server memory capacity limits in Lync Server 2013](lync-server-2013-monitoring-for-server-memory-capacity-limits.md).

In addition to CPU and memory usage counters, you can use the following ASP.NET performance counters to help determine when a server is overloaded with requests:

  - **ASP.NET v2.0.50727\\Requests Current**, which indicates the number of pending web requests on the server. When this counter reaches 5,000, subsequent requests will fail with the error message, "503 - Service Unavailable."

  - **ASP.NET\\Requests Queued** (should always be zero).

<div>


> [!NOTE]  
> If you meet or exceed these values, you should revisit and recompute your capacity planning for the correct sizing of CPU, number of cores, and memory for the computers hosting the Web services.



</div>

<div>

## See Also


[Monitoring for server memory capacity limits in Lync Server 2013](lync-server-2013-monitoring-for-server-memory-capacity-limits.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

