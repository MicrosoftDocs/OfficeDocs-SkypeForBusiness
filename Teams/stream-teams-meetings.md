---
title: Live streaming Teams meetings
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.reviewer: bryannyce
ms.date: 04/29/2024
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

**APPLIES TO:** ✔️Meetings ✔️Webinars ✖️Town halls

Streaming allows your organization to expand your reach and gives meeting attendees more meeting options. When you enable streaming, organizers can stream meetings and webinars to external endpoints by providing a Real-Time Messaging Protocol (RTMP) URL and key to the built-in Custom Streaming app in Teams.

> [!NOTE]
> You can't stream live events.

## Manage live streaming for your users

You can use the Teams admin center or PowerShell to manage whether organizers with this assigned policy can live stream their meetings and webinars through RTMP.

### Manage live streaming in the Teams admin center

Follow these steps to manage live streaming in the Teams admin center:

1. In the Teams admin center, expand **Meetings** and then select **Meeting policies**.
1. Select the policy that you want to edit.
1. Under **Audio & video**, set **Live streaming** to **On**.
1. Select **Save**

### Manage live streaming with PowerShell

To manage whether organizers with this policy can live stream their meetings and webinars through RTMP, use the **`-LiveStreamingMode`** parameter within the PowerShell [**CsTeamsMeetingPolicy**](/powershell/module/teams/set-csteamsmeetingpolicy) cmdlet.

To allow organizers with this policy to stream their meetings through RTMP, use the following script:

```PowerShell
Set-CsTeamsMeetingPolicy -Identity Global -LiveStreamingMode Enabled
```

For information on how to assign policies with PowerShell, see [Assign policies in Teams](policy-assignment-overview.md).

## Related topics

- [Assign policies in Teams](policy-assignment-overview.md)
- [Set-CsTeamsMeetingPolicy](/powershell/module/teams/set-csteamsmeetingpolicy)
- [Quick start - Meetings, webinars, and live events](quick-start-meetings-live-events.md)
- [Plan meetings](plan-meetings-external-participants.md)
- [Plan webinars](plan-webinars.md)
