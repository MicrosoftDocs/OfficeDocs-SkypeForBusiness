---
title: Network Assessment Tool
author: v-judegn
ms.author: v-judegn
manager: serdars
ms.date: 09/26/2018
ms.topic: reference
ms.service: msteams
ms.reviewer: lola
audience: admin
description: About the Network Assessment Tool (NAT)
localization_priority: Priority
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

The Network Assessment Tool (NAT) tests the connection to Microsoft Network Edge by streaming a set of packets to the nearest edge site and back for approximately 20s for a configured number of iterations. 

- Network performance – Test the connection to Microsoft Network Edge by streaming audio packets to the nearest edge site and back for approximately 17 seconds for a configured number of iterations. The tool collects, packet loss, jitter, round-trip latency and packet reorder percentage from each call. The results from set of test calls can be analyzed to determine if it meets the media quality and performance targets described here: https://support.office.com/en-us/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917 . These targets and testing apply for Microsoft Teams calls.
- Network connectivity – Verify network and network elements between the test location and the Microsoft Network are correctly configured to enable communication to the IP addresses and ports needed for Microsoft Teams calls. The addresses and ports are described here: https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#bkmk_teams. These tests are performed using UDP and TCP transport protocol.

This tool can be downloaded at https://go.microsoft.com/fwlink/?linkid=855799.