---
title: "Proxy servers for Teams or Skype for Business Online"
ms.author: mikeplum
author: MikePlumleyMSFT
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
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom: 
  - Optimization
  - seo-marvel-apr2020
description: This article provides information about using a proxy server with Microsoft Teams or Skype for Business.
---

# Proxy servers for Teams or Skype for Business Online

This article provides guidance about using a proxy server with Teams or Skype for Business.
  
## Not using a proxy server is recommended

When it comes to Teams or Skype for Business traffic over proxies, Microsoft recommends bypassing proxies. Proxies don't make Teams or Skype for Business more secure because the traffic is already encrypted.
  
And having a proxy can cause issues. Performance-related problems can be introduced to the environment through latency and packet loss by attempting to route Teams traffic through a proxy server. Issues such as these will result in a negative experience in such Teams or Skype for Business scenarios as audio and video, where real-time streams are essential.

We recommend that Teams traffic bypasses proxy server infrastructure.

## Teams Phones

Teams Phones don't support proxy servers.

Our recommendation is to ensure that both signaling (TCP 443) and media (UDP 3478-3481) traffic bypasses proxy server infrastructure.

## Teams Meeting Rooms and Panels

Our recommendation is to ensure your Teams Meeting Rooms bypass proxy infrastructure.

Windows-based Teams Meeting Rooms support proxy servers, but do not support proxy servers that require authentication. Android-based Teams Meeting Rooms do not support proxy servers.
  
## If you need to use a proxy server

Some organizations have no option to bypass a proxy for Teams or Skype for Business traffic. If that's the case for you, the problems mentioned above need to be kept in mind.
  
Microsoft also strongly recommends:
  
- Using local, external DNS resolution (some cloud-based proxy solutions can cause DNS resolution to occur in another location).
    
- Using direct UDP based routing rather than relying on TCP based routing for media
    
- Allowing UDP traffic (3478-3481)

- Allowing all required URLs and IPs, including those for Azure, Office 365, Intune and Teams Room Pro (where used)
    
- Following the other recommendations in our networking guidelines:
  [Prepare your organization's network for Teams](prepare-network.md)
  
    
Following this guidance should minimize potential problems.
  
## Related topics

[Microsoft 365 and Office 365 Network Connectivity Principles](/microsoft-365/enterprise/microsoft-365-network-connectivity-principles)

[Prepare your organization's network for Teams](prepare-network.md)
