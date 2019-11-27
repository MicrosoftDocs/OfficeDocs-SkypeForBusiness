---
title: Improve and monitor call quality for Microsoft Teams
author: lolajacobsen
ms.author: lolaj
manager: Serdars
ms.topic: conceptual
ms.service: msteams
audience: admin
ms.reviewer: vkorlep, siunies
description: Use Quality of Service (QoS) settings and then Call Analytics and Call Quality Dashboard in Microsoft Teams.
localization_priority: Normal
search.appverid: MET150
ms.collection: 
  - M365-voice
appliesto: 
  - Microsoft Teams
---

# Improve and monitor call quality Microsoft Teams

This article tells you how to use Quality of Service (QoS) to improve call quality in Microsoft Teams. It also introduces the ways you can monitor and troubleshoot call quality in Teams, by using the Call Quality Dashboard (CQD) and per-user call analytics, both found in the Teams admin center. 

## Prioritize important network traffic using QoS
As your users start using Teams for making calls and holding meetings, they may experience a caller's voice breaking up or chopping in and out of a call or meeting. Shared video may freeze or pixelate, or fail altogether. This is due to the IP packets that represent voice and video traffic encountering network congestion and arriving out of sequence or not at all. If this happens (or to prevent it from happening in the first place), use **Quality of Service (QoS)**. 

With **Quality of Service (QoS)**, you prioritize delay-sensitive network traffic (for example, voice or video streams), allowing it to "cut in line" in front of traffic that is less sensitive (like downloading a new app, where an extra second to download isn't a big deal). QoS identifies and marks all packets in real-time streams using Windows Group Policy Objects and a routing feature called Port-based Access Control Lists, which instructs your network to give voice, video, and screen sharing their own dedicated network bandwidth.

Ideally, you'll implement QoS on your internal network while getting ready to roll out Teams, but if you're small enough, it can be optional. 

When you're ready, read [Implement Quality of Service (QoS) in Microsoft Teams](QoS-in-Teams.md).

To use QoS to manage meeting traffic, read [Set how you want to handle real-time media traffic for Teams meetings](meeting-settings-in-teams.md#set-how-you-want-to-handle-real-time-media-traffic-for-teams-meetings).


## Monitor and troubleshoot call quality
You'll use [**per-user call analytics and Call Quality Dashboard**](difference-between-call-analytics-and-call-quality-dashboard.md) to find and troubleshoot call-quality problems that come up during ongoing operation.  

**Per-user call analytics** shows detailed information about the devices, networks, and connectivity related to  ***specific calls and meetings*** for each user in Teams or Skype for Business. Use this information to troubleshoot call quality and connection problems in a specific call. To learn more, read [Set up Call Analytics](set-up-call-analytics.md) and [Use Call Analytics to troubleshoot poor call quality](use-call-analytics-to-troubleshoot-poor-call-quality.md).

**Call Quality Dashboard (CQD)** gives you a ***network-wide view*** of call quality across your organization. Use CQD information to help you identify and fix problems. To learn more, read [Turning on and using Call Quality Dashboard](turning-on-and-using-call-quality-dashboard.md).

## Related Topics

[Set QoS on Windows clients](qos-in-teams-clients.md)

[Dimensions and measures available in Call Quality Dashboard](dimensions-and-measures-available-in-call-quality-dashboard.md)

[Stream Classification in Call Quality Dashboard](stream-classification-in-call-quality-dashboard.md)

[Video: Call Quality Overview](https://aka.ms/teams-quality)

