---
title: Stream Teams meetings and live events
author: KarliStites
ms.author: kastites
manager: serdars
ms.reviewer: suchakr
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
appliesto: 
  - Microsoft Teams
localization_priority: Normal
search.appverid: MET150
f1.keywords:
- CSH
ms.custom: 
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
description: Learn how to set up and manage streaming for your your meetings and live events in Teams.
---

# Stream Teams meetings and live events

This article will help you set up streaming for Teams meetings and live events.

## What is streaming and how does it work?

Streaming allows meeting organizers to stream a meeting or live event to external endpoints by providing a RTMP URL and key to the built-in Custom Streaming app in Teams.

## Set up streaming with PowerShell

You can set up your organization for streaming with PowerShell. Currently, this policy is not available in the Teams admin center. The per-user policy is used to specify **who** can enable live streaming. It's turned off by default.

You can use the following attribute within the Windows PowerShell **Set-CsTeamsMeetingPolicy** cmdlet to set up streaming. For more information on the cmdlet, see [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy).

- LiveStreamingMode

Set **LiveStreamingMode** to **Enabled** to turn on streaming capabilities for one or more users.

> [!IMPORTANT]
> If you want to stream live events, make sure your organization is set up for live events. For more information, see [Set up for live events in Microsoft Teams](/teams-live-events/set-up-for-teams-live-events.md).

### Assign the policy

For more information on how to assign policies with PowerShell, see [Assign policies in Teams](policy-assignment-overview.md).

## Related topics

- [Set up for live events in Microsoft Teams](/teams-live-events/set-up-for-teams-live-events.md)
- [Assign policies in Teams](policy-assignment-overview.md)
- [Set-CsTeamsMeetingPolicy](/powershell/module/skype/set-csteamsmeetingpolicy)
- [Quick start - Meetings, webinars, and live events](quick-start-meetings-live-events.md)