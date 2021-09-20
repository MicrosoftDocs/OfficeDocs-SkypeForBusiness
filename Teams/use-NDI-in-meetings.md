---
title: Use NDI in Microsoft Teams
author: CarolynRowe
ms.author: crowe
ms.reviewer: aaglick
manager: serdars
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn how to use NDI in Microsoft Teams.
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

# Use NDI® and SDI technology in Microsoft Teams

Teams provides two options for broadcasting Teams meeting content, NewTek NDI® (Network Device Interface) and SDI (serial digital interface):

- NewTek NDI® (Network Device Interface) technology is a modern solution for connecting media devices (such as a studio camera and mixer). Instead of using physical connections, NDI® technology enables connectivity over a local intranet, including on a local machine.

  NDI® technology has become a standard industry solution for producing live content for streams and has gained significant awareness and adoption in the professional broadcast world.

  **DO WE NUKE THE FOLLOWING SENTENCE?**
  NDI® technology is limited to a local network and should only be considered a part of the production workflow, not a broadcast solution.

- SDI has been used in broadcast productions since 1989 and is supported on most legacy studio hardware devices. Hardware devices from AJA Video Systems and Blackmagic Design  provide connectivity to legacy broadcast devices that use SDI.

NDI® and SDI technology is supported in all locales.

Access to using NDI and SDI is determined by the meeting policy for the user attempting to activate the feature. For the most secure solution, do not turn on the local streaming parameter as a global setting.


## Enable broadcast features

To enable NDI® and SDI broadcast features for a user:

1. The tenant admin must enable the end user to have local streaming turned on for their meeting policy. 

2. The end user must turn on local streaming for their specific client.


To enable the end user, you can use the Teams Admin center or Teams PowerShell as follows.

In the Teams admin center, go to **Meeting policies > Audio & video** and select **Allow Local Streaming**.

To use PowerShell, use the Set-CsTeamsMeetingPolicy cmdlet as follows:

```PowerShell
Set-CsTeamsMeetingPolicy -Identity MEETING_POLICY -AllowLocalStreaming $true
```

After this change has populated, the end user must turn on local streaming for their specific client from **Settings** > **Permissions**.  For more information, see ...  LINK TO END USER CONTENT.





