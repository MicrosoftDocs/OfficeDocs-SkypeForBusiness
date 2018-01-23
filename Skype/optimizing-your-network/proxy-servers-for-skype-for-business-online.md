---
title: "Proxy Servers for Skype for Business Online"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: jastark
ms.date: 01/22/2018
ms.topic: article
ms.assetid: 7acaf2c2-35fa-490f-84cd-822e446e0fc7
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
ms.collection: Adm_Skype4B_Online
ms.audience: Admin
appliesto: Skype for Business, Microsoft Teams
localization_priority: Normal
f1keywords: None
ms.custom:
- Optimization
description: "This article will help you with guidance about using a proxy server with Skype for Business."
---

# Proxy Servers for Skype for Business Online

This article will help you with guidance about using a proxy server with Skype for Business.
  
## Not using a proxy server is recommended

When it comes to Skype for Business traffic over proxies, Microsoft recommends bypassing proxies. Proxies don't make Skype for Business more secure because its traffic is already encrypted.
  
And having a proxy can cause issues. Performance-related problems can be introduced to the environment through latency and packet loss. Issues such as these will result in a negative experience in such Skype for Business scenarios as audio and video, where real-time streams are essential.
  
## If you need to use a proxy server

Some organizations have no option to bypass a proxy for Skype for Business traffic. If that's the case for you, the problems mentioned above need to be kept in mind.
  
Microsoft also strongly recommends:
  
- Using external DNS resolution
    
- Using direct UDP based routing
    
- Allowing UDP traffic
    
- Following the other recommendations in our Networking guidelines:
    
  - [Media Quality and Network Connectivity Performance in Skype for Business Online](https://support.office.com/en-us/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
    
  - [Optimizing your network for Skype for Business Online](https://support.office.com/en-us/article/Optimizing-your-network-for-Skype-for-Business-Online-b363bdca-b00d-4150-96c3-ec7eab5a8a43)
    
Following this guidance should minimize potential problems.
  
## Proxy vendors with built-in Skype for Business support or configuration options

This section will contain information about proxy vendors who provide products or services that are proven to work successfully with Skype for Business traffic.
  
For organizations using **Bluecoat Proxy solutions**, a new firmware has been released which addresses several issues with:
    
  - SSL interception
    
  - OCSP/SRL checks
    
  - SIP over TLS
    
  - support for TURN
    
Bluecoat's native support for Skype for Business can easily be enabled, allowing for the identification of relevant traffic, and managing it appropriately. This ensures optimal authentication, signaling, and media traffic flow, to provide a great user experience without security concerns.
    
Please refer to the following link if Bluecoat Proxy is a part of your network topology: https://support.symantec.com/en_US/article.DOC9757.html

## Related topics

[Optimizing your network for Skype for Business Online](https://support.office.com/en-us/article/Optimizing-your-network-for-Skype-for-Business-Online-b363bdca-b00d-4150-96c3-ec7eab5a8a43)