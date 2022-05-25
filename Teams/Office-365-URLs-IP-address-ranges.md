---
title: Microsoft 365 and Office 365 URLs and IP address ranges
ms.reviewer: 
author: SerdarSoysal
ms.author: serdars
manager: serdars
ms.date: 08/21/2018
ms.topic: article
audience: admin
ms.service: msteams
description: Learn how to properly configure Microsoft 365 or Office 365 URLs and IP address ranges and bypass the forward proxy when possible for connections with Microsoft Teams service.
ms.localizationpriority: medium
search.appverid: MET150
f1.keywords:
  - CSH
ms.custom: 
 - ms.teamsadmincenter.meetingsettings.network.ports
 - seo-marvel-mar2020
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

# Microsoft 365 and Office 365 URLs and IP address ranges

Go to [Microsoft 365 and Office 365 URLs and IP address ranges](/office365/enterprise/urls-and-ip-address-ranges#skype-for-business-online-and-microsoft-teams) for a detailed and up-to-date list of the URLs, IP addresses, ports, and protocols that must be correctly configured for Teams. Microsoft is continuously improving the Microsoft 365 and Office 365 services and adding new functionality, which means the required ports, URLs, and IP addresses may change over time. We recommend that you [subscribe via RSS](/office365/enterprise/urls-and-ip-address-ranges#skype-for-business-online-and-microsoft-teams) to receive notifications when this information is updated or changed.

The Teams calling and meetings experience is built on the next generation cloud-based infrastructure that is also used by Skype and Skype for Business. These technology investments include Azure-based cloud services for media processing and signaling, H.264 video codec, SILK and Opus audio codec, network resiliency, telemetry, and quality diagnostics. As such, there are URLs and IPs that are required that may be associated with both Skype and Skype for Business.

For all Microsoft 365 and Office 365 workloads, the recommended connection method to Teams services is bypassing the forward proxy where possible. When a proxy server sits between a client and the Office 365 data centers, media might be forced over TCP instead of UDP, which would impact media quality. Download sample proxy PAC files that can be used to configure traffic bypass from [Managing Microsoft 365 and Office 365 endpoints](/office365/enterprise/managing-office-365-endpoints).

If your networking and security policies require Microsoft 365 or Office 365 traffic to flow through a proxy server, make sure that the above requirements are already met before deploying Teams into production. For more information, read [Proxy Servers for Teams or Skype for Business Online](proxy-servers-for-skype-for-business-online.md).