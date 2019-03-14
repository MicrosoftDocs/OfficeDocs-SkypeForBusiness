---
title: Implement QoS and Monitor Call Analytics in Microsoft Teams
author: jambirk
ms.author: jambirk
manager: Serdars
ms.topic: conceptual
ms.service: msteams
ms.reviewer: jambirk
description: Use Quality of Service (QoS) settings and then Call Analytics and Call Quality Dashboard in Microsoft Teams.
localization_priority: Normal
search.appverid: MET150
MS.collection: 
- Teams_ITAdmin_PracticalGuidance
- M365-voice 
appliesto:
- Microsoft Teams
---

# Implement QoS and Monitor Call Quality in Microsoft Teams

## Get Started

As your users start using Teams for making calls and holding meetings, they may experience a caller's voice breaking up or chopping in and out of a call or meeting. Shared video may freeze or pixelate, or fail altogether. This is due to the IP packets that represent voice and video traffic encountering network congestion and arriving out of sequence or not at all. There are ways to identify these problems when they surface and prevent their return, primarily Quality of Service (QoS).

**Quality of Service (QoS)** is a way to allow real-time network traffic (like voice or video streams) that is sensitive to network delays to "cut in line" in front of traffic that is less sensitive (like downloading a new app, where an extra second to download isn't a big deal). QoS identifies and marks all packets in real-time streams using Windows Group Policy Objects and a routing feature called Port-based Access Control Lists, which then helps your network to give voice, video, and screen share streams their own dedicated portions of network bandwidth.

 For now, we'll just say that it's a lot like sending a letter through the mail: If you send it book rate it gets there pretty soon and that's good enough, if you send it first class it gets there a lot faster, and if you send it Priority Mail, it gets there within two days. Of course networks run faster than the mail, but it still runs true that speed is critical for some applications and is not so critical for others. This subject is inherently detailed and tricky to understand at first, but it makes a huge difference in the user experience so it's worth investing time and energy upfront. Read [Implement Quality of Service (QoS) in Microsoft Teams](QoS-in-Teams.md) for a more detailed discussion.

Ideally you would implement QoS on your internal network while setting up Teams, but if you're small enough it can be optional. This allows the delay-sensitive voice and video traffic to get prioritized ahead of other traffic. You'd do this prioritization on all the [client devices](QoS-in-Teams-clients.md), in the [Microsoft Teams admin center](meeting-settings-in-teams.md#set-how-you-want-to-handle-real-time-media-traffic-for-teams-meetings), as well as on the switches and routers in your network.

[**Call Analytics and Call Quality Dashboard**](difference-between-call-analytics-and-call-quality-dashboard.md) are used to find and troubleshoot problems that come up during ongoing operation.  

**Call Analytics** shows detailed information about the devices, networks, and connectivity related to  ***specific calls and meetings*** for each user in a Microsoft Teams or Skype for Business account. If you're an Office 365 admin, you can use Call Analytics to troubleshoot call quality and connection problems experienced in a specific call. This can help you to identify and eliminate problems.

**Call Quality Dashboard (CQD)** is designed to help admins and network engineers optimize their ***network***, not analyze and troubleshoot a single call. CQD shifts focus from specific users to look at aggregated information for an entire organization. This can also help you to identify and eliminate problems.

## Related Topics

[Implement Quality of Service (QoS) in Microsoft Teams](QoS-in-Teams.md)

[Video: Call Quality Overview](https://aka.ms/teams-quality)

[Set up Call Analytics](set-up-call-analytics.md)

[Use Call Analytics to troubleshoot poor call quality](use-call-analytics-to-troubleshoot-poor-call-quality.md)

[Turning on and using Call Quality Dashboard](turning-on-and-using-call-quality-dashboard.md)

[Dimensions and measures available in Call Quality Dashboard](dimensions-and-measures-available-in-call-quality-dashboard.md)

[Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md)