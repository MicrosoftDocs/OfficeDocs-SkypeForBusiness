---
title: "Monitor for server memory capacity limits in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 1697ea71-6fcf-480d-b4e9-cd79f94d247e
description: "Summary: Learn how to monitor for server memory capacity limits in Skype for Business Server."
---

# Monitor for server memory capacity limits in Skype for Business Server
 
**Summary:** Learn how to monitor for server memory capacity limits in Skype for Business Server.
  
> [!CAUTION]
> The information in this topic that refers to Capacity Planning pertains only to Lync 2010 Mobile clients and the Mobility Service (Mcx). Capacity Planning for the Unified Communications Web API (UCWA), used by the Lync 2013 Mobile clients, is provided by the Lync Server 2013, Planning Tool. 

> [!NOTE]
> MCX (Mobility Service) support for legacy mobile clients is no longer available in Skype for Business Server 2019. All current Skype for Business mobile clients already use Unified Communications Web API (UCWA) to support instant messaging (IM), presence, and contacts. Users with legacy clients using MCX will need to upgrade to a current client.
  
Two mobility performance counters can help you to determine your current usage and help you plan capacity for the Skype for Business Server Mobility Service (Mcx), as well as to monitor memory usage for UCWA. For UCWA, the counter category is **LS:WEB - UCWA**. For the Mobility Service (Mcx), the counters are under the category **LS:WEB - Mobile Communication Service**. The counters to monitor are:
  
- **Currently Active Session Count with Active Presence Subscriptions**, which is the current number of endpoints registered through UCWA or the Mobility Service (Mcx) that have active presence subscriptions (number of always-connected mobile users)
    
- **Currently Active Session Count**, which is the current number of endpoints registered through UCWA or the Mobility Service
    
If the difference between **Currently Active Session Count with Active Presence Subscriptions** and **Currently Active Session Count** is small over time, this means that most mobile device users have an always-connected device, such as an Android or Nokia mobile device (for Mcx only). UCWA always-connected devices include Apple and Android devices running Lync 2013 Mobile clients). If **Currently Active Session Count** is much higher than **Currently Active Session Count with Active Presence Subscriptions**, this indicates that more users are using a background endpoint device, such as an Apple iOS device or Windows Phone under Mcx. (Windows Phone is the only Lync 2013 Mobile client that will register as this).
  
You should set a limit on the **Currently Active Session Count with Active Presence Subscriptions** and **Currently Active Session Count** performance counters based on your expected usage, capacity planning results, and ongoing monitoring of Mobility Service and other Front End Server counters. The limits you set should enable you to evaluate server capacity and raise alerts when capacity is exceeded.
  
To determine the appropriate limits, you need to first determine how much memory is available on the Front End Server for the Mobility Service. Monitor the counters to determine when you need to plan for extra capacity, according to the following formula:
  
Total memory used by the Mcx Mobility Service (MB) = 164 + (400 + 134) / 1024 * **Currently Active Session Count with Active Presence Subscriptions** + 400 / 1024 * ( **Currently Active Session Count** - **Currently Active Session Count with Active Presence Subscriptions**)
  
> [!IMPORTANT]
> The Microsoft Lync Server 2010 Capacity Calculator is a spreadsheet that is prepopulated with all of the formulas that enable a planner to determine what the requirements will be for the Skype for Business servers, including CPU, memory, and hard drive. You can [download the spreadsheet and an associated document](https://go.microsoft.com/fwlink/p/?LinkID=212657). 
  
The Front End Server needs enough available memory to support the Mobility Service in failover situations. You can monitor the current available memory on the Front End Server by using the **Memory\Available Mbytes** counter, or by using the equation mentioned earlier, to plan for the amount of memory that you expect the Mobility Service to use.
  
If the amount of memory available on the Front End Server is lower than 1,500 MB when you plan for the expected number of mobility users, you need to add more hardware to support the Mobility Service. For more details, see [Monitor mobility for performance in Skype for Business Server](monitor-mobility-performance.md) in the Operations documentation.
  
## See also

[Monitor mobility for performance in Skype for Business Server](monitor-mobility-performance.md)
