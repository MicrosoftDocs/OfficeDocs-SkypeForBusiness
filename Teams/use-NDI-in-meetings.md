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
ROBOTS: NOINDEX, NOFOLLOW
---

# Use NDI in Microsoft Teams

Network Device Interface (NDI) is a modern solution for connecting media devices (such as a studio camera and mixer). Instead of using physical connections, NDI enables connectivity over a local intranet, including on a local machine.

NDI has become a standard industry solution for producing live content for streams and has gained significant awareness and adoption in the professional broadcast world.

Skype previously adding NDI-Out functionality to Skype in late 2018. Microsoft Teams leverages this functionality to improve the meeting experience.

NDI is not a broadcast solution for Teams by creating a streaming solution. NDI is limited to a local network and should only be considered a part of the production workflow, not a broadcast solution.

To initiate NDI, enable the feature flag enableStreamingCallsOverNdi.

When a user joins a meeting, they'll see a message that notifies them that the meeting is being broadcast. They can either opt in or out of being included in the broadcast. The following image shows the banner message that a user sees in a Teams meeting.

![An image of the NDI banner that displays in a Teams meeting.](media/NDI-disclosure.png)

The banner has a link to the [Microsoft privacy policy](https://support.skype.com/faq/FA34853/what-is-skype-for-content-creators?q=ndi).

## Supported locales and user types

NDI is supported in all locales. The following users are supported in an NDI meeting:

-	In-tenant – full support, delivered based on ring/tenantId/userId (controlled by Meetings Policy + Feature Flag)
-	Federated – no (even when they have NDI on)<sup>1</sup>
-	Freemium - no (default value)
-	Anonymous – no (default value)
-	Guest – no  (default value)

<sup>1</sup> Devices have an NDI setting that is on by default. If a meeting participant is using a device with NDI off, they'll need to turn on NDI.
