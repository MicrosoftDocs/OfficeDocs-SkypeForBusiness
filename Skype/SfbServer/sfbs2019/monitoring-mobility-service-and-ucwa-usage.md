---
title: "Monitoring Mobility Service and UCWA usage in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8389b37a-ca3e-4047-8b51-85bc07da87e8
description: "On an ongoing basis, you should monitor the CPU and memory that is used by the Lync Server Mobility Service (Mcx) and the Unified Communications Web API (UCWA). To monitor usage, you can use the following:"
---

# Monitoring Mobility Service and UCWA usage in Lync Server 2013
[]
On an ongoing basis, you should monitor the CPU and memory that is used by the Lync Server Mobility Service (Mcx) and the Unified Communications Web API (UCWA). To monitor usage, you can use the following:
  
 **For Unified Communications Web API (UCWA):**
  
- The **LyncUcwa** worker process in Internet Information Services (IIS) Manager. In the **Worker Processes** pane, look at the **CPU %** and **Private Bytes (KB)** (memory) columns. 
    
- The **CPU** and **Processor** performance counters. 
    
For most deployments, UCWA CPU usage should be below 15 percent on average. Memory usage should fall within the limits described in [Monitoring for server memory capacity limits in Lync Server 2013](monitoring-for-server-memory-capacity-limits.md).
  
In addition to CPU and memory usage counters, you can use the following performance counters to help determine when a server is overloaded with requests:
  
- **LS:WEB - Throttling and Authentication\WEB - Total Requests in Processing**, which indicates the number of pending web requests on the server. When this counter reaches 10,000, subsequent requests will fail, with the error message, "503 - Service Unavailable." 
    
- **ASP.NET\Requests Queued** (should always be zero). 
    
> [!NOTE]
> If you meet or exceed these values, you should revisit and re-compute your capacity planning for the correct sizing of CPU, number of cores and memory for the computers hosting the Web services. 
  
 **For the Mobility Service (Mcx):**
  
- The **CSIntMcxAppPool** and **CSExtMcxAppPool** worker processes in Internet Information Services (IIS) Manager. In the **Worker Processes** pane, look at the **CPU %** and **Private Bytes (KB)** (memory) columns. 
    
- The **CPU** and **Processor** performance counters. 
    
For most deployments, Mobility Service CPU usage should be below 15 percent, on average. Memory usage should fall within the limits described in [Monitoring for server memory capacity limits in Lync Server 2013](monitoring-for-server-memory-capacity-limits.md).
  
In addition to CPU and memory usage counters, you can use the following ASP.NET performance counters to help determine when a server is overloaded with requests:
  
- **ASP.NET v2.0.50727\Requests Current**, which indicates the number of pending web requests on the server. When this counter reaches 5,000, subsequent requests will fail with the error message, "503 - Service Unavailable." 
    
- **ASP.NET\Requests Queued** (should always be zero). 
    
> [!NOTE]
> If you meet or exceed these values, you should revisit and recompute your capacity planning for the correct sizing of CPU, number of cores, and memory for the computers hosting the Web services. 
  
## See also

#### 

[Monitoring for server memory capacity limits in Lync Server 2013](monitoring-for-server-memory-capacity-limits.md)

