---
title: Use NDI in Microsoft Teams
author: cichur
ms.author: v-cichur
ms.reviewer: aaglick
manager: serdars
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn how to use NDI in Microsoft Teams.
localization_priority: Normal
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

# Use NDI® technology in Microsoft Teams

 NewTek NDI® (Network Device Interface) technology is a modern solution for connecting media devices (such as a studio camera and mixer). Instead of using physical connections, NDI® technology enables connectivity over a local intranet, including on a local machine.

NDI® technology has become a standard industry solution for producing live content for streams and has gained significant awareness and adoption in the professional broadcast world.

Skype previously added NDI®-out functionality to Skype in late 2018. Microsoft Teams uses this functionality to improve the meeting experience.

NDI® technology is limited to a local network and should only be considered a part of the production workflow, not a broadcast solution.

## Turn on NDI® technology

NDI® technology requires two steps to be turned on for a user.

1. The tenant admin must enable the end user to have NDI turned on for their meeting policy. This can be done on an individual basis in the Teams Admin portal or via the Teams PowerShell by the _AllowNDIStreaming_ property in CsTeamsMeetingPolicy.

```PowerShell
Set-CsTeamsMeetingPolicy -Identity MEETING_POLICY -AllowNDIStreaming $true
```

2. After this change has populated, the end user must turn on NDI® technology for their specific client from **Settings** > **Permissions**.

After being turned on for a user and their particular client, the user can turn on NDI via the overflow menu and selecting "Broadcast over NDI."

After starting the NDI and having an endpoint subscribe to an NDI feed, they'll see a message that notifies them that the meeting is being broadcast. If users don’t want to be included in the broadcast, they’ll need to drop from the meeting.

The following image shows the banner message that a user sees in a Teams meeting.

![he NDI® technology banner that displays in a Teams meeting.](media/NDI-disclosure.png)

The banner has a link to the [Microsoft privacy policy](https://aka.ms/teamsprivacy).

> [!NOTE]
> NDI® is activated per session only. In the next meeting, the user must activate it before using NDI®.

## Supported locales and user types

NDI® technology is supported in all locales.

Access to using NDI is determined by the meeting policy for the user attempting to activate the feature. For the most secure solution, do not turn on the NDI policy as a global setting.
