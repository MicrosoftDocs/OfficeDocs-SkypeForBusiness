---
title: Require a watermark for sensitive Teams meetings
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: 
audience: admin
ms.localizationpriority: high
f1.keywords:
- NOCSH
ms.collection: 
  - m365solution-compliantmeetings
appliesto: 
  - Microsoft Teams
description: 
---

# Require a watermark for sensitive Teams meetings

[!INCLUDE[Teams Premium ECM](includes/teams-premium-ecm.md)]

You can enable a watermark to be displayed in Teams meetings both for content shared on screen in the meeting and for attendee video. The watermark displays the email address of the meeting participant. Meeting participants can't turn the watermark off.

Meeting watermarks are enabled in the Teams admin center. They can then be added by the meeting organizer or enforced by a sensitivity label.

Anonymous participants and overflow participants have an audio-only experience when a watermark is in use.

The following table shows where watermarks are configured:

|Setting|Meeting organizer|Template|Sensitivity label|Teams admin|
|:------|:----------------|:-------|:----------------|:----------|
|Watermark shared content|Yes|No|Yes|Yes|
|Watermark videos|Yes|No|Yes|Yes|

When a watermark is being used in a meeting, the following features are turned off:

- Meeting recording, including automatic recording

- Large gallery

- Together mode 

- PowerPoint Live

- Whiteboard 

- Content from camera

## Watermarks for sensitive and highly sensitive meetings



## Enable watermarks
 
To enable watermarking for meetings

1. In the Teams admin center, expand **Meetings** and select **Meeting policies**.

1. Select the policy you want to update.

1. To enable watermark on attendee video, set **Watermark videos** to **On**.

1. To enable watermark on content shared on screen in a meeting, set **Watermark shared content** to **On**.

1. To see how the watermark will look on desktop and mobile devices, select **Preview**.

1. Select **Save**.

## Related topics

Link to sensitivity label article