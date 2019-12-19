---
title: Planning and preparing your network
author: judegn
ms.author: v-lanac
manager: serdars
ms.topic: article
audience: admin
ms.service: msteams
ms.reviewer: dearbeen
description: Use this guidance to prepare your network for Teams deployment and rollout 
localization_priority: Normal
search.appverid: MET150
ms.custom: Teams-guidance
ms.collection: 
- Teams_ITAdmin_JourneyFromSfB
- M365-collaboration
appliesto:
- Microsoft Teams
---

# Planning and preparing your network

## Why should you plan and prepare your network?
 Failing to prepare your network will likely lead to dissatisfied users and costly, ad-hoc fixes. By preparing your network—and your organization—for Teams, you can dramatically increase your chance of optimal and consistent performance.

## Where do I begin?
Start your preparation and planning by familiarizing yourself with our framework for successful planning. As illustrated below, each step in the framework builds on the step prior and, for optimal results, we recommend following the steps in order.

### [Step 1: Review network requirements for Teams](prepare-environment-prepare-network.md)
Have an overall view of your network requirements before going into the networking details.

### [Step 2: Perform a network readiness assessment](plan-journey-evaluate-environment.md)
Ensure your environment is ready for Teams to help optimize the user experience and facilitate your network planning.

### [Step 3: Perform network bandwidth planning](prepare-environment-prepare-network#bandwidth-planning.md)
This article describes a concise version of how bandwidth is utilized by Teams real time audio, video, and desktop sharing modalities in various use cases. Teams is always conservative on bandwidth utilization and can deliver HD video quality in under 1.2Mbps. The actual bandwidth consumption in each audio/video call or meeting will vary based on several factors, such as video layout, video resolution, and video frames per second. When more bandwidth is available, quality and usage will increase to deliver the best experience.

### [Step 4: Validate the NAT pool size required for user connectivity] (prepare-environment-prepare-network#nat-pool-size.md)
Ensure that adequate public IP addresses are assigned to the NAT pools to prevent port exhaustion. Port exhaustion will contribute to internal users and devices being unable to connect to the Office 365 service.
Connectivity problems are a leading cause of user perception issues for cloud services.

### [Step 5: Network remediation](prepare-environment-prepare-network#network-remediation.md)

If the results of bandwidth planning, port testing, or network requirements testing show that your current network needs remediation before you deploy Teams, you can accomplish this in several ways:

- For blocked ports, change firewall rules and retest the ports.
- For network impairments, always perform a root-cause analysis.

