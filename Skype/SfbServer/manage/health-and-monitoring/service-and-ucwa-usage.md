---
title: "Monitor Mobility Service and UCWA usage in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 8389b37a-ca3e-4047-8b51-85bc07da87e8
description: "Summary: Manage the Mobility Service (Mcx) and the Unified Communications Web API (UCWA) in Skype for Business Server."
---

# Monitor Mobility Service and UCWA usage in Skype for Business Server
 
**Summary:** Manage the Mobility Service (Mcx) and the Unified Communications Web API (UCWA) in Skype for Business Server.

> [!NOTE]
> MCX (Mobility Service) support for legacy mobile clients is no longer available in Skype for Business Server 2019. All current Skype for Business mobile clients already use Unified Communications Web API (UCWA) to support instant messaging (IM), presence, and contacts. Users with legacy clients using MCX will need to upgrade to a current client.
  
On an ongoing basis, you should monitor the CPU and memory that is used by the Skype for Business Server Mobility Service (Mcx) and the Unified Communications Web API (UCWA). To monitor usage, you can use the following:
  
 **For Unified Communications Web API (UCWA):**
  
- The **LyncUcwa** worker process in Internet Information Services (IIS) Manager. In the **Worker Processes** pane, look at the **CPU %** and **Private Bytes (KB)** (memory) columns.
    
- The **CPU** and **Processor** performance counters.
    
For most deployments, UCWA CPU usage should be below 15 percent on average. Memory usage should fall within the limits described in [Monitor for server memory capacity limits in Skype for Business Server](server-memory-capacity-limits.md).
  
In addition to CPU and memory usage counters, you can use the following performance counters to help determine when a server is overloaded with requests:
  
- **LS:WEB - Throttling and Authentication\WEB - Total Requests in Processing**, which indicates the number of pending web requests on the server. When this counter reaches 10,000, subsequent requests will fail, with the error message, "503 - Service Unavailable."
    
- **ASP.NET\Requests Queued** (should always be zero).
    
> [!NOTE]
> If you meet or exceed these values, you should revisit and re-compute your capacity planning for the correct sizing of CPU, number of cores and memory for the computers hosting the web services. 
  
 **For the Mobility Service (Mcx):**
  
- The **CSIntMcxAppPool** and **CSExtMcxAppPool** worker processes in Internet Information Services (IIS) Manager. In the **Worker Processes** pane, look at the **CPU %** and **Private Bytes (KB)** (memory) columns.
    
- The **CPU** and **Processor** performance counters.
    
For most deployments, Mobility Service CPU usage should be below 15 percent, on average. Memory usage should fall within the limits described in [Monitor for server memory capacity limits in Skype for Business Server](server-memory-capacity-limits.md).
  
In addition to CPU and memory usage counters, you can use the following ASP.NET performance counters to help determine when a server is overloaded with requests:
  
- **ASP.NET v2.0.50727\Requests Current**, which indicates the number of pending web requests on the server. When this counter reaches 5,000, subsequent requests will fail with the error message, "503 - Service Unavailable."
    
- **ASP.NET\Requests Queued** (should always be zero).
    
> [!NOTE]
> If you meet or exceed these values, you should revisit and recompute your capacity planning for the correct sizing of CPU, number of cores, and memory for the computers hosting the web services. 

> [!NOTE]
> MCX (Mobility Service) support for legacy mobile clients is no longer available in Skype for Business Server 2019. All current Skype for Business mobile clients already use Unified Communications Web API (UCWA) to support instant messaging (IM), presence, and contacts. Users with legacy clients using MCX will need to upgrade to a current client.
  
## See also

[Monitor for server memory capacity limits in Skype for Business Server](server-memory-capacity-limits.md)
