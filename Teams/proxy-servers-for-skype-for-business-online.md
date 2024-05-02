---
title: "Proxy servers for Teams or Skype for Business Online"
author: MicrosoftHeidi
ms.author: heidip
manager: jtremper
ms.reviewer: jastark
ms.date: 11/28/2017
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

# Proxy servers for Teams and Skype for Business Online

This article provides guidance about using a proxy server with Teams or Skype for Business.

## Microsoft 365 connectivity 

High quality, low latency connectivity is key to achieving call quality within Microsoft Teams and Skype for Business.

We recommend that the path between the end users device and Microsoft 365 is as short and direct as possible and utilizes local Internet egress that is close to the end user. This enables traffic to quickly reach the closest Microsoft network service front door location.
  
## Not using a proxy server is recommended

Many organizations utilize proxy servers today within their network. As Microsoft Teams and Skype for Business media traffic is already encrypted, passing this traffic through a proxy server doesn't make the traffic any more secure.

Proxies can cause issues too. Performance-related problems can be introduced to the environment through latency and packet loss by attempting to route Teams traffic through a proxy server. This can be caused by the proxy being unable to handle the amount of traffic passing through it, or by incorrectly routing the traffic to a Microsoft network service front door location that is further away from the end user.

Issues such as these will result in a negative experience within Teams and Skype for Business.

We recommend that Teams traffic bypasses proxy server infrastructure, including SSL inspection. You may wish to achieve this by putting Teams Phones and Meeting Room devices on their own VLAN and providing them with Internet access.

## Windows-Based Teams Devices

Windows-based Teams meeting rooms, and Surface Hubs support some proxy servers, but don't support proxy servers that require authentication.

We recommend that these devices bypass your proxy infrastructure and access Microsoft 365 services via your firewall.

## Android-Based Teams Devices

Android-based Teams devices, including Teams phones, panels, displays and boards don't support authenticated proxy servers or tenant restrictions. Contact your OEM partner for details on unauthenticated proxy support.

We recommend that these devices bypass your proxy infrastructure and access Microsoft 365 services via your firewall.

## If you need to use a proxy server

Some organizations have no option to bypass a proxy for Teams or Skype for Business traffic. If that's the case for you, the problems mentioned above need to be kept in mind.

> [!Note]
> If you use a privately signed certificate on your proxy infrastructure (commonly used for SSL inspection), you'll need to install the privately signed certificate and the certificate chain on the Teams meeting room device to allow the device to trust the certificate. Installing privately signed certificates on Teams Phones and other Android-based Teams devices is not supported.
  
Microsoft also strongly recommends:
  
- Using local, external DNS resolution (some cloud-based proxy solutions can cause DNS resolution to occur in another location).

- Ensuring the path between the Teams device and our service is as short and direct as possible
    
- Using direct UDP based routing rather than relying on TCP based routing for media
    
- Allowing UDP traffic for Teams Media (3478-3481) through your firewall

- Allowing all required URLs and IPs, including those for Azure, Office 365, Intune, and Teams Rooms Pro (where used) through your firewall
    
- Following the other recommendations in our networking guidelines:
  [Prepare your organization's network for Teams](prepare-network.md)
  
 Following this guidance should minimize potential problems.
  
## Additional recommendations for Teams live events and Teams view-only meetings

Viewers of Teams live events and Teams view-only meetings receive the stream via TCP HTTPS. We recommend that you bypass proxy servers and disable SSL inspection for the following URLs:

- *.media.azure.net
- *.bmc.cdn.office.net
  
## Related topics

[Microsoft 365 and Office 365 Network Connectivity Principles](/microsoft-365/enterprise/microsoft-365-network-connectivity-principles)

[Prepare your organization's network for Teams](prepare-network.md)
