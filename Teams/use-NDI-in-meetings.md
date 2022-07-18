---
title: Broadcast meeting content
author: CarolynRowe
ms.author: crowe
ms.reviewer: aalinne
manager: serdars
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
appliesto: 
  - Microsoft Teams
---

# Broadcast meeting content 



Teams provides two options for broadcasting Teams meeting content: Network Device Interface (NewTek NDI®) and Serial Digital Interface (SDI):

- NewTek NDI® technology is a modern solution for connecting media devices (such as a studio camera and mixer). Instead of using physical connections, NDI® technology enables connectivity over a local intranet, including on a local machine.

  NDI® technology has become a standard industry solution for producing live content for streams and has gained significant awareness and adoption in the professional broadcast world.

- SDI has been used in broadcast productions since 1989 and is supported on most legacy studio hardware devices. Hardware devices from AJA Video Systems and Blackmagic Design provide connectivity to legacy broadcast devices that use SDI.

> [!NOTE]
> The Video Hardware Out feature the supports SDI is currently in Preview release.

NDI® and SDI technology is supported in all locales.

Access to using NDI and SDI is determined by the meeting policy for the user attempting to activate the feature. For the most secure solution, do not turn on the local streaming parameter as a global setting.


## Enable broadcast features

To enable NDI® and SDI broadcast features for a user:

1. The tenant admin must enable the end user to have local streaming turned on for their meeting policy. 

2. The end user must turn on local streaming for their specific client.


To enable the end user, you can use the Teams Admin center or Teams PowerShell as follows.

In the Teams admin center, go to **Meeting policies > Audio & video** and select **Local Broadcasting**.

To use PowerShell, use the Set-CsTeamsMeetingPolicy cmdlet as follows:

```PowerShell
Set-CsTeamsMeetingPolicy -Identity MEETING_POLICY -AllowNDIStreaming $true
```

After this change has populated, the end user must turn on local streaming for their specific client from **Settings** > **Permissions**. For more information, see [Broadcasting audio and video from Teams](https://support.microsoft.com/office/broadcasting-audio-and-video-from-teams-with-ndi-technology-e91a0adb-96b9-4dca-a2cd-07181276afa3).





