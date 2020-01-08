---
title: "Proxy servers for Teams"
ms.author: lolaj
author: lolajacobsen
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
  - Microsoft Teams
localization_priority: Normal
f1keywords: None
ms.custom: 
  - Optimization
description: "This article provides information about using a proxy server with Teams."
---

# Proxy servers for Teams

This article provides guidance about using a proxy server with Microsoft Teams.
  
## Not using a proxy server is recommended

When it comes to Teams traffic over proxies, Microsoft recommends bypassing proxies. Proxies don't make Teams more secure because the traffic is already encrypted.
  
Having a proxy can also cause issues. Performance-related problems can be introduced to the environment through latency and packet loss. Issues such as these will result in a negative experience in such Teams scenarios as audio and video, where real-time streams are essential.
  
## If you need to use a proxy server

Some organizations don't have the option of bypassing a proxy for Teams traffic. If that's the case for you, Microsoft strongly recommends that you do the following:
  
- Use external DNS resolution
    
- Use direct UDP based routing
    
- Allow UDP traffic
    
- Follow the recommendations in our networking guidelines:
    - [Media Quality and Network Connectivity Performance in Skype for Business Online](https://docs.microsoft.com/SkypeForBusiness/optimizing-your-network/media-quality-and-network-connectivity-performance?redirectSourcePath=%252fen-us%252farticle%252fMedia-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
    - [Optimize your network](optimize-your-network)
    
  