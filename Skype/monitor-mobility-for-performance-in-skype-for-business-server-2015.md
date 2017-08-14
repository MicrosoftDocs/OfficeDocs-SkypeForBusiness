---
title: Monitor mobility for performance in Skype for Business Server 2015
ms.prod: SKYPEFORBUSINESS
ms.assetid: 9c831c63-9a7d-48ec-9118-f8a7e80ddd04
---


# Monitor mobility for performance in Skype for Business Server 2015
[] **Summary:** Learn about the Mobility Service (Mcx) and the Unified Communications Web API (UCWA) in Skype for Business Server 2015.
The Skype for Business Server Mobility Service (Mcx) and the Unified Communications Web API (UCWA) increase the load on Front End Servers and Front End pools. Mobile devices that maintain a connection to the server even when the mobile application is minimized, such as Android and Nokia devices running Lync 2010 Mobile, as well as Android and Apple devices running Lync 2013 Mobile, impose a greater load than devices that terminate their connection to the server when the mobile application is minimized. As your mobility usage increases, you must monitor mobility performance to determine when you need to increase your capacity.
  
    
    

Several limits influence mobility performance: 
- Available memory
    
  
- Request queue limit
    
  
- Concurrent connections
    
  
- IIS queue length
    
  
Other limits on servers that can influence mobility performance are a maximum of 12 concurrent sign-ins, authentications, session renewals, and terminations. These maximums do not need to be modified for most deployments.
## In this section


-  [Monitor for server memory capacity limits in Skype for Business Server 2015](monitor-for-server-memory-capacity-limits-in-skype-for-business-server-2015.md)
    
  
-  [Monitor Mobility Service and UCWA usage in Skype for Business Server 2015](monitor-mobility-service-and-ucwa-usage-in-skype-for-business-server-2015.md)
    
  
-  [Configure Mobility Service for high performance in Skype for Business Server 2015](configure-mobility-service-for-high-performance-in-skype-for-business-server-201.md)
    
  
-  [Monitoring IIS request tracing log files in Skype for Business Server 2015](monitoring-iis-request-tracing-log-files-in-skype-for-business-server-2015.md)
    
  
-  [Mobility performance counters in Skype for Business Server 2015](mobility-performance-counters-in-skype-for-business-server-2015.md)
    
  

