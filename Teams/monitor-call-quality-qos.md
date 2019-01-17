---
title: Implement QoS and Monitor Call Analytics in Microsoft Teams
author: jambirk
ms.author: MyAdvisor
manager: Serdars
ms.topic: article
ms.service: msteams
ms.reviewer: jambirk
description: Use Quality of Service (QoS) settings and then Call Analytics and Call Quality Dashboard in Microsoft Teams.
localization_priority: Normal
search.appverid: MET150
MS.collection: Teams_ITAdmin_PracticalGuidance
appliesto:
- Microsoft Teams
---

# Implement QoS and Monitor Call Quality in Microsoft Teams

## Get Started

As your users start using Teams for making calls and holding meetings, they may find speakers breaking ups or chopping in and out of a call or meeting. Shared video may freeze or pixellate, or fail altogether. This is due to the IP packets that represent voice and video traffic encountering network congestion and arriving out of sequence or not at all. There are ways to prevent this and identify other problems when they surface, primarily Quality of Service (QoS).

[**Quality of Service (QoS)**](monitor-call-quality-qos.md)  is a way to identify packets that are sensitive to delays and congestion, and then provide the packets with preferential treatment so they encounter far less congestion. For now, we'll just say that it's a lot like sending a letter through the Mail: If you send it book rate it gets there pretty soon and that's good enough, if you send it first class it gets there a lot faster, and if you send it Priority Mail, it gets there within two days. Of course networks run faster than the mail, but it still runs true that speed is critical for some applications and is not so critical for others. This subject is inherently detailed and tricky to understand at first, but it makes a huge difference in the user experience so it's worth investing time and energy upfront.

Ideally you would implement QoS on your internal network while setting up Teams, but if you're small enough it can be optional. This allows the delay-sensitive voice and video traffic to get prioritized ahead of other traffic. You'd do this prioritization on all the client devices, as well as on the switches and routers in your network.

[**Call Analytics and Call Quality Dashboard**](difference-between-call-analytics-and-call-quality-dashboard.md) are used to find and troubleshoot problems that come up during ongoing operation.  

Call Analytics shows detailed information about the devices, networks, and connectivity related to the specific calls and meetings for each user in a Microsoft Teams or Skype for Business account. If you're an Office 365 admin, you can use Call Analytics to troubleshoot call quality and connection problems experienced in a specific call. This can help you to identify and eliminate problems.

Call Quality Dashboard (CQD) is designed to help admins and network engineers optimize a **network**, not analyze and troubleshoot a single call. CQD shifts focus from specific users to look at aggregated information for an entire organization. This can also help you to identify and eliminate problems.

## Related Topics

[Implement QoS for Microsoft Teams](monitor-call-quality-qos.md)

[Set up Call Analytics](set-up-call-analytics.md)

[Use Call Analytics to troubleshoot poor call quality](use-call-analytics-to-troubleshoot-poor-call-quality.md)

[Turning on and using Call Quality Dashboard ](turning-on-and-using-call-quality-dashboard.md)

[Dimensions and measures available in Call Quality Dashboard](dimensions-and-measures-available-in-call-quality-dashboard.md)

[Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md)