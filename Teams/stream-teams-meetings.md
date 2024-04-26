---
title: Live streaming Teams meetings
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.reviewer: bryannyce
ms.date: 04/26/2024
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
appliesto: 
  - Microsoft Teams
localization_priority: medium
search.appverid: MET150
f1.keywords: 
  - CSH
ms.custom: 
ms.collection: 
  - M365-collaboration
  - Tier2
  - m365initiative-meetings
description: Learn how to set up and manage streaming for your Teams meetings.
---

# Live streaming Teams meetings

Streaming allows your organization to expand your reach and gives meeting attendees more meeting options. When you enable streaming, organizers can stream meetings and webinars to external endpoints by providing a Real-Time Messaging Protocol (RTMP) URL and key to the built-in Custom Streaming app in Teams.

> [!NOTE]
> You can't stream live events.

To turn on live streaming
1. In the Teams admin center, expand **Meetings** and then select **Meeting policies**.
1. Select the policy that you want to edit.
1. Under **Audio & video**, set **Live streaming** to **On**.
1. Select **Save**.


#### Set up streaming with PowerShell

You can set up your organization for streaming with PowerShell. Currently, this policy is not available in the Teams admin center. The per-user policy is used to specify **who** can enable live streaming. It's turned off by default.

You can use the following attribute within the Windows PowerShell **Set-CsTeamsMeetingPolicy** cmdlet to set up streaming. For more information on the cmdlet, see [Set-CsTeamsMeetingPolicy](/powershell/module/teams/set-csteamsmeetingpolicy).

- LiveStreamingMode

Set **LiveStreamingMode** to **On** to turn on streaming capabilities for one or more users.

For information on how to assign policies with PowerShell, see [Assign policies in Teams](policy-assignment-overview.md).

## Related topics

- [Assign policies in Teams](policy-assignment-overview.md)
- [Set-CsTeamsMeetingPolicy](/powershell/module/teams/set-csteamsmeetingpolicy)
- [Quick start - Meetings, webinars, and live events](quick-start-meetings-live-events.md)
