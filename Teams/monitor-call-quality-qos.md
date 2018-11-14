---
title: Implement QoS and Monitor Call Quality in Microsoft Teams
author: jambirk
ms.author: MyAdvisor
manager: Serdars
ms.date: 04/23/2018
ms.topic: article
ms.service: msteams
ms.reviewer: jambirk
description: Use Quality of Service (QoS) settings and then Call Analytics and Call Quality Dashboard  in Microsoft Teams.
localization_priority: Normal
search.appverid: MET150
MS.collection: Teams_ITAdmin_PracticalGuidance
appliesto:
- Microsoft Teams
---

The way you'd ideally do this is to implement QoS on your internal network while setting up Teams. This allows the lag- sensitive voice and video traffic to get prioritized ahead of other traffic. You'd do this prioritization on all the client devices, as well as on the switches and routers in your network.

Later on you'd use Call Analytics and Call Quality Dashboard to find and troubleshoot problems that come up. It may turn out you need to adjust how big the dedicated pipe is for the various kinds of traffic, or you might decide to increase the size of the pipe between certain especially busy network nodes.

