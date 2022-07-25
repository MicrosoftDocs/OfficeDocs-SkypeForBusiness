---
title: Monitor and improve call quality for Microsoft Teams
author: CarolynRowe
ms.author: crowe
manager: Serdars
ms.topic: conceptual
ms.service: msteams
audience: admin
ms.reviewer: vkorlep, siunies
description: Use Quality of Service (QoS) settings and then Call Analytics and Call Quality Dashboard in Microsoft Teams.
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-voice
f1.keywords:
 - NOCSH
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-mar2020
---

# Monitor and improve call quality for Microsoft Teams

This article introduces three key tools you can use to monitor, troubleshoot, manage, and improve call quality in Microsoft Teams. 

- **Call Quality Dashboard (CQD)**: To analyze org-wide trends or problems, drive improvements to performance

- **Call analytics**: To analyze call and meeting quality for individual users

- **Quality of Service (QoS)**: To prioritize important network traffic



## Monitor and troubleshoot call quality
You'll use per-user **Call analytics** and **Call Quality Dashboard** to find and troubleshoot call-quality problems that come up during ongoing operation. This lets you drive performance improvements across your network. Both of these tools are in the Teams admin center.

 - **Call analytics** shows detailed information about the devices, networks, and connectivity related to  ***specific calls and meetings*** for each user in Teams. Teams admin and helpdesk agents will use this information to troubleshoot call quality and connection problems in a specific call. To learn more, read [Set up call analytics](set-up-call-analytics.md) and [Use Call Analytics to troubleshoot poor call quality](use-call-analytics-to-troubleshoot-poor-call-quality.md).
 
 - **Call Quality Dashboard (CQD)** gives you a ***network-wide view*** of call quality across your organization. Use CQD information to help you identify and fix problems. First, [Set up CQD](turning-on-and-using-call-quality-dashboard.md). Then read [Manage call and meeting quality in Teams](quality-of-experience-review-guide.md).

 Call analytics and CQD run in parallel and can be used independently or together. For example, if a communications support specialist determines that they need more help troubleshooting a user's call problem, they escalate the call to a communications support engineer, who has access to additional information about the call. In turn, the communications support engineer alerts a network engineer to a possible site-related issue they noticed in the call analytics. The network engineer checks CQD to see if an overall site-related issue could be a contributing cause of the user's call problem.


## Prioritize important network traffic using QoS
As your users start using Teams for calls and meetings, they may experience a caller's voice breaking up or cutting in and out of a call or meeting. Shared video may freeze or pixelate, or fail altogether. This is due to the IP packets that represent voice and video traffic encountering network congestion and arriving out of sequence or not at all. If this happens (or to prevent it from happening in the first place), use **Quality of Service (QoS)**. 

With QoS, you prioritize delay-sensitive network traffic (for example, voice or video streams), allowing it to "cut in line" in front of traffic that is less sensitive (like downloading a new app, where an extra second to download isn't a big deal). QoS identifies and marks all packets in real-time streams using Windows Group Policy Objects and a routing feature called Port-based Access Control Lists, which instructs your network to give voice, video, and screen sharing their own dedicated network bandwidth.

Ideally, you'll implement QoS on your internal network while getting ready to roll out Teams, but you can do it anytime. If you're small enough, you might not need QoS.

When you're ready, read [Implement Quality of Service (QoS) in Microsoft Teams](QoS-in-Teams.md).

To use QoS to manage meeting traffic, read [Set how you want to handle real-time media traffic for Teams meetings](meeting-settings-in-teams.md#set-how-you-want-to-handle-real-time-media-traffic-for-teams-meetings).


## Related Topics

[Set up call analytics](set-up-call-analytics.md)

[Use Call Analytics to troubleshoot poor call quality](use-call-analytics-to-troubleshoot-poor-call-quality.md)

[Set up CQD](turning-on-and-using-call-quality-dashboard.md)

[Manage call and meeting quality in Teams](quality-of-experience-review-guide.md)

[Teams Troubleshooting](/MicrosoftTeams/troubleshoot/teams)
