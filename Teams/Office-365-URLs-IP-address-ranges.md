---
title: Office 365 URLs and IP address ranges
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 03/13/2018
ms.topic: article
ms.service: msteams
description: Learn how to properly configure Office 365 URLs and IP address ranges, bypass the forward proxy where available for connections with Microsoft Teams service, and the requirements for networking and security policies.
MS.collection: Strat_MT_TeamsAdmin
appliesto: 
- Microsoft Teams
---

Office 365 URLs and IP address ranges
=====================================

Go to [Office 365 URLs and IP address ranges](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#bkmk_teams) for a detailed and up-to-date list of the URLs, IP addresses, ports, and protocols that must be correctly configured for Teams. Microsoft is continuously improving the Office 365 service and adding new functionality, which means the required ports, URLs, and IP addresses may change over time. We recommend that you [subscribe via RSS](https://go.microsoft.com/fwlink/p/?linkid=236301) to receive notifications when this information is updated or changed.

The Teams calling and meetings experience is built on the next generation cloud-based infrastructure that is also used by Skype and Skype for Business. These technology investments include Azure-based cloud services for media processing and signaling, H.264 video codec, SILK and Opus audio codec, network resiliency, telemetry, and quality diagnostics. As such, there are URLs and IPs that are required that may be associated with both Skype and Skype for Business.

For all Office 365 workloads, the recommended connection method to Teams services is bypassing the forward proxy where possible. When a proxy server sits between a client and the Office 365 data centers, media might be forced over TCP instead of UDP, which would impact media quality. Download sample proxy PAC files that can be used to configure traffic bypass from [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a).

If your networking and security policies require Office 365 traffic to flow through a proxy server, make sure that the above requirements are already met before deploying Teams into production (review [Proxy Servers for Skype for Business Online](https://support.office.com/article/Proxy-Servers-for-Skype-for-Business-Online-7acaf2c2-35fa-490f-84cd-822e446e0fc7?ui=en-US&rs=en-US&ad=US) for guidance).
