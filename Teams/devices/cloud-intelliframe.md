---
title: Cloud IntelliFrame
ms.author: v-smandalika
author: v-smandalika
manager: dansimp
ms.reviewer: dansimp
ms.date: 08/09/2023
ms.service: msteams
ms.subservice: itpro-devices
audience: Admin
appliesto: 
  - Microsoft Teams
f1.keywords: 
  - NOCSH
ms.collection: 
  - M365-voice
  - Teams_ITAdmin_Devices
  - Tier1
ms.topic: reference
search.appverid: MET150
description: This article describes the Cloud IntelliFrame feature.
---

# Cloud IntelliFrame
> [!IMPORTANT]
> Cloud IntelliFrame is not intended for use in Illinois. Please do not enable Cloud IntelliFrame in a meeting room in Illinois. 

Cloud IntelliFrame is a new experience that allows online meeting attendees to see people in Teams Rooms more clearly through the smart video feeds of in-room participants. These smart video feeds are created by zooming into the faces of the in-room participants and by eliminating distractions, thereby enhancing the hybrid meeting experience. You can see the expressions and gestures of the people in the room more easily, which helps improve collaboration in hybrid meetings. It creates equity in hybrid meetings as everyone can be seen and heard.

> [!IMPORTANT]
> You are responsible for compliance with local laws and regulations when you enable Cloud IntelliFrame
in a particular jurisdiction, including with respect to obligations around notice, consent, and data retention. 

Cloud IntelliFrame will be rolling out across Microsoft Teams Rooms on Windows with the Pro license and can be viewed on Microsoft Teams Desktop (Windows and Mac) with any license.

## Experience overview

> [!IMPORTANT]
> Please install appropriate signage outside any meeting room where you enable Cloud IntelliFrame advising people about the feature.

All Microsoft Teams Rooms on Windows with a Pro license equipped with cameras (specified in [Supported cameras](#supported-cameras)) automatically opt-in to Cloud IntelliFrame. Online participants on Microsoft Teams Desktop (Windows and Mac) will see the IntelliFrame video feed by default from rooms with these cameras.

Cloud IntelliFrame shows the smart feed when there are nine or less people in the room. It automatically switches between the standard room view and IntelliFrame view based on in-room activity. For example, if someone enters the meeting room, the view would automatically switch to standard room view until the individual settles down.

:::image type="content" source="../media/video-conference.png" alt-text="Screenshot that shows how a video conference looks like." lightbox="../media/video-conference.png":::

This icon ![Icon indicating activation and display of IntelliFrame](../media/intelliframe-activation-icon.png) on the top-right of the room video feed indicates that Cloud IntelliFrame is being displayed.

People in the room can disable IntelliFrame by using the in-meeting settings on the console. These settings turn off Cloud IntelliFrame and enables a switchback to standard view for the room. All online attendees would then see the standard view from the room.

:::image type="content" source="../media/standard-view-of-teams-room.png" alt-text="Screenshot that shows how the standard view of a Teams room looks on a computer." lightbox="../media/standard-view-of-teams-room.png":::

People on Teams Desktop can also toggle IntelliFrame on/off by right-clicking on the room's video tile and selecting **Turn off IntelliFrame**. This option switches off the IntelliFrame view just on their Teams client.

:::image type="content" source="../media/turning-off-intelliframe.png" alt-text="Screenshot that displays to the user the option to turn off IntelliFrame." lightbox="../media/turning-off-intelliframe.png":::

### Supported cameras

The following camera models when deployed in a Microsoft Teams Room on Windows with a Pro license automatically use the Cloud IntelliFrame:

- AVer CAM520 Pro 
- AVer CAM520 Pro2 
- BRIO 4K Stream Edition 
- EagleEye Cube USB 
- HD Pro Webcam C920 
- Jabra PanaCast 
- Logi Rally Camera 
- Logitech BRIO 
- Logitech ConferenceCam CC3000e 
- Logitech MeetUp 
- Logitech Webcam C925e 
- Logitech Webcam C930e 
- Microsoft® LifeCam Studio 
- Polycom EagleEye IV USB Camera 
- PTZ Pro 2 
- PTZ Pro Camera 
- ThinkSmart Cam 
- Yealink UVC30 
- Yealink UVC34 
- Yealink UVC50 
- Yealink UVC80 
- Yealink UVC86

## Manage Cloud IntelliFrame

Cloud IntelliFrame is ideal for focus rooms and medium spaces. It may not be ideal for large spaces as people farthest from the camera may appear blurry after digital zoom. You may also want to switch off Cloud IntelliFrame in rooms with glass walls without any privacy filter.

To switch off Cloud IntelliFrame in a room, perform the following steps:

1. Create an XML configuration file by following the steps in [Create an XML configuration file](../rooms/xml-config-file.md#create-an-xml-configuration-file).
1. Add the following element in the *SkypeSettings.xml* file.

   ```XML
   <EnableCloudIntelliFrame>false</EnableCloudIntelliFrame>
   ```

1. Restart the console for the configuration changes to take effect.
