---
title: Allow broadcast production in Teams meetings with NDI and SDI hardware
ms.author: wlibebe
author: wlibebe
ms.reviewer: bryanyce
ms.date: 5/23/2024
manager: pamgreen
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn how to use NDI and SDI to broadcast meeting content in Microsoft Teams.
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
appliesto: 
  - Microsoft Teams
---

# Allow broadcast production in Teams meetings with NDI and SDI hardware

Teams offers two options for broadcasting Teams meeting content: Network Device Interface(NewTek NDI®) and Serial Digital Interface (SDI):

- NewTek NDI® is a modern solution for connecting multiple media devices, such as studio cameras and mixers, without physical connections. Instead, NDI® technology enables connectivity over a local intranet, including on a local machine. This technology is a widely adopted industry standard for producing live content for streams, with significant awareness and adoption in the professional broadcast world.

- SDI, known for its reliable long-distance transmission, is a widely used technology for sending video through cables. It's a goto choice in professional broadcasting because it carries uncompressed, high-quality video along with audio and other data. Hardware devices from AJA Video Systems and Blackmagic Design provide connectivity to legacy broadcast devices that use SDI.

NDI® and SDI technology is supported in all locales.

As an admin, you can allow your users to use NDI® and SDI for broadcast production in their meetings. For the most secure solution, don't enable this policy as a global setting.

## 1. Enable the broadcast production policy

To enable NDI® and SDI broadcast features for a user, you can use the Teams admin center or PowerShell.

### Enable broadcast production in the Teams admin center

1. Open the Teams admin center.
2. Expand **Meetings** from the navigation pane.
3. Under **Meetings**, select **Meeting Policies**.
4. Either select an existing policy or create a new one.
5. Navigate to the **Audio & video** section.
6. Toggle **Broadcast production with NDI and SDI hardware** to  **On**.
7. Select **Save**

### Enable broadcast production in PowerShell

You can use the **`-ContentSharingInExternalMeetings`** parameter in the [**CsTeamsMeetingPolicy**](/powershell/module/teams/set-csteamsmeetingpolicy) cmdlet to enable broadcast production for your users.

To allow users with this policy to use broadcast production, use the following script:

```powershell
Set-CsTeamsMeetingPolicy -Identity <policy name> -AllowNDIStreaming $true
```

## 2. Instruct your users to turn on production capabilities

Users with an enabled **Broadcast production with NDI and SDI hardware** policy must turn on **Production capabilities**  from **Settings** > **App Permissions** in their specific client.
For details on how your user can turn on production capabilities, see [Broadcasting audio and video from Teams](https://support.microsoft.com/office/broadcasting-audio-and-video-from-teams-with-ndi-technology-e91a0adb-96b9-4dca-a2cd-07181276afa3).

## Related topics

- [Plan for meetings](plan-meetings.md)