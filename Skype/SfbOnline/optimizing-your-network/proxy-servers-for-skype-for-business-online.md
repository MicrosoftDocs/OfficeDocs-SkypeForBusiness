---
ms.date: 01/08/2020
title: "Proxy servers for Teams or Skype for Business Online"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: jastark
ms.topic: reference
ms.assetid: 7acaf2c2-35fa-490f-84cd-822e446e0fc7
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-collaboration
audience: Admin
appliesto: 
  - Skype for Business
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom: 
  - Optimization
description: "This article provides information about using a proxy server with Skype for Business."
---

# Proxy servers for Skype for Business Online

[!INCLUDE [sfbo-retirement](../../Hub/includes/sfbo-retirement.md)]

This article provides guidance about using a proxy server with Skype for Business.
  
## Not using a proxy server is recommended

When it comes to Skype for Business traffic over proxies, Microsoft recommends bypassing proxies. Proxies don't make Skype for Business more secure because the traffic is already encrypted.
  
And having a proxy can cause issues. Performance-related problems can be introduced to the environment through latency and packet loss. Issues such as these will result in a negative experience in such Teams or Skype for Business scenarios as audio and video, where real-time streams are essential.
  
## If you need to use a proxy server

Some organizations have no option to bypass a proxy for Skype for Business traffic. If that's the case for you, the problems mentioned above need to be kept in mind.
  
Microsoft also strongly recommends:
  
- Using external DNS resolution
    
- Using direct UDP based routing
    
- Allowing UDP traffic
    
- Following the other recommendations in our networking guidelines:
    
  - [Media Quality and Network Connectivity Performance in Skype for Business Online](media-quality-and-network-connectivity-performance.md)
    
  - [Optimizing your network for Skype for Business Online](optimizing-your-network.md)
    
Following this guidance should minimize potential problems.
  
## Related topics

[Optimizing your network for Skype for Business Online](optimizing-your-network.md)
 

