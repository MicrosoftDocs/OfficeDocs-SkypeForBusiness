---
title: "Monitor mobility for performance in Skype for Business Server"
ms.reviewer: 
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 9c831c63-9a7d-48ec-9118-f8a7e80ddd04
description: "Summary: Learn about the Mobility Service (Mcx) and the Unified Communications Web API (UCWA) in Skype for Business Server."
---

# Monitor mobility for performance in Skype for Business Server
 
**Summary:** Learn about the Mobility Service (Mcx) and the Unified Communications Web API (UCWA) in Skype for Business Server.
  
The Skype for Business Server Mobility Service (Mcx) and the Unified Communications Web API (UCWA) increase the load on Front End Servers and Front End pools. Mobile devices that maintain a connection to the server even when the mobile application is minimized, such as Android and Nokia devices running Lync 2010 Mobile, as well as Android and Apple devices running Lync 2013 Mobile, impose a greater load than devices that terminate their connection to the server when the mobile application is minimized. As your mobility usage increases, you must monitor mobility performance to determine when you need to increase your capacity.

> [!NOTE]
> MCX (Mobility Service) support for legacy mobile clients is no longer available in Skype for Business Server 2019. All current Skype for Business mobile clients already use Unified Communications Web API (UCWA) to support instant messaging (IM), presence, and contacts. Users with legacy clients using MCX will need to upgrade to a current client.
  
Several limits influence mobility performance: 
  
- Available memory
    
- Request queue limit
    
- Concurrent connections
    
- IIS queue length
    
Other limits on servers that can influence mobility performance are a maximum of 12 concurrent sign-ins, authentications, session renewals, and terminations. These maximums do not need to be modified for most deployments.
  
## In this section

- [Monitor for server memory capacity limits in Skype for Business Server](server-memory-capacity-limits.md)
    
- [Monitor Mobility Service and UCWA usage in Skype for Business Server](service-and-ucwa-usage.md)
    
- [Configure Mobility Service for high performance in Skype for Business Server](configure-service.md)
    
- [Monitoring IIS request tracing log files in Skype for Business Server](iis-request-tracing-log-files.md)
    
- [Mobility performance counters in Skype for Business Server](performance-counters.md)
    

