---
title: "Configure Mobility Service for high performance in Skype for Business Server 2015"
ms.author: jambirk
author: jambirk
manager: serdars
ms.date: 3/28/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c2b8aadb-cffb-49f0-ba7a-e8541a1ff475
description: "Summary: Learn about the Mobility Service in Skype for Business Server 2015."
---

# Configure Mobility Service for high performance in Skype for Business Server 2015
 
**Summary:** Learn about the Mobility Service in Skype for Business Server 2015.
  
> [!IMPORTANT]
> This topic applies only to the Skype for Business Server 2015 Mobility Service (Mcx), and does not apply to Unified Communications Web API (UCWA), as delivered in the Cumulative Updates for Lync Server 2013: February 2013. 
  
When you install the Mobility Service (Mcx) on Internet Information Services (IIS) 7.5, the Mobility Service installer configures some performance settings on the Front End Server. We recommend that you use IIS 7.5 for mobility. The settings affect the maximum number of concurrent user requests and the maximum number of threads that are allowed for the Mobility Service.
  
Here are the performance settings:
  
### Settings for Mcx on IIS 7.5

1. **maxConcurrentThreadsPerCPU** is set to zero (0).
    
2. **maxConcurrentRequestsPerCPU** is set to zero (0).
    
3. ASP.NET process model is set to AutoConfig (for IIS 7.5 only).
    
4. HTTP.sys queue limit is set to 1,000 (by default).
    

