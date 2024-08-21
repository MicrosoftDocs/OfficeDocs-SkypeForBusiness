---
title: Cloud IntelliFrame
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: suhailkhalid
ms.date: 08/21/2024
ms.topic: article
ms.service: msteams
ms.subservice: itpro-devices
audience: Admin
appliesto: 
  - Microsoft Teams
ms.collection: 
  - teams-rooms-devices
  - Teams_ITAdmin_Devices
  - Tier1
f1.keywords: 
  - NOCSH
search.appverid: MET150
description: This article describes the Cloud IntelliFrame feature.
---

# Cloud IntelliFrame

Cloud IntelliFrame is a new experience that allows online meeting attendees to see people in Teams Rooms more clearly through the smart video feeds of in-room participants. These smart video feeds are created by zooming into the faces of the in-room participants and by eliminating distractions, thereby enhancing the hybrid meeting experience. You can see the expressions and gestures of the people in the room more easily, which helps improve collaboration in hybrid meetings. It creates equity in hybrid meetings as everyone can be seen and heard.

## Experience overview

> [!IMPORTANT]
> Install appropriate signage outside any meeting room where you enable Cloud IntelliFrame advising people about the feature.

All Microsoft Teams Rooms on Windows with a Pro license equipped with cameras (specified in [Supported cameras](#supported-cameras)) automatically opt-in to Cloud IntelliFrame. Online participants on Microsoft Teams Desktop (Windows and Mac) will see the IntelliFrame video feed as a secondary option from rooms with these cameras.

Cloud IntelliFrame shows the smart feed when there are nine or less people in the room. It automatically switches between the standard room view and IntelliFrame view based on in-room activity. For example, if someone enters the meeting room, the view would automatically switch to standard room view until the individual settles down.

:::image type="content" source="../media/video-conference.png" alt-text="Screenshot that shows how a video conference looks like." lightbox="../media/video-conference.png":::

People in the room can disable IntelliFrame by using the in-meeting settings on the console. These settings turn off Cloud IntelliFrame and enable a switchback to standard view for the room. All online attendees would then see the standard view from the room.

:::image type="content" source="../media/standard-view-of-teams-room.png" alt-text="Screenshot that shows how the standard view of a Teams room looks on a computer." lightbox="../media/standard-view-of-teams-room.png":::

People on Teams Desktop can also toggle IntelliFrame on/off by right-clicking on the room's video tile and selecting **Turn off IntelliFrame**. This option switches off the IntelliFrame view just on their Teams client.

:::image type="content" source="../media/turning-off-intelliframe.png" alt-text="Screenshot that displays to the user the option to turn off IntelliFrame." lightbox="../media/turning-off-intelliframe.png":::

### Who can view Cloud IntelliFrame? 

The following table provides information about which client can view Cloud IntelliFrame:

|Client Type  |View Cloud IntelliFrame  |
|---------|---------|
|Windows     |   Available      |
|Mac     |        Available |
|iOS     |    Coming Soon     |
|Android     |  Coming Soon       |
|Web     |      Available   |
|Teams Rooms on Windows     |    Available     |
|Teams Rooms on Android     |     Coming Soon    |
|Teams Display     |   Coming Soon      |

### Data Retention

Cloud IntelliFrame runs on Azure and is fully compliant with M365 data processing with full separation between tenant boundaries. The infrastructure of Cloud IntelliFrame is no different from the infrastructure we use to record Teams Meetings.

 Cloud IntelliFrame does not store meeting data or any identifiable information. The only data we log is what is needed to improve the service (for example, how long did it take to switch from room view to gallery, how often does the view layout change during the meeting), and to understand how Cloud IntelliFrame was used (for example, are end-users enabling/disabling it?).

### Supported cameras

The following camera models when deployed in Microsoft Teams Rooms on Windows with a Pro license automatically use the Cloud IntelliFrame:

- AVer CAM520 Pro 
- AVer CAM520 Pro2
- Crestron P12

- Crestron P20

- Jabra PanaCast 
- Lenovo ThinkSmart One
- Logitech BRIO
- Logitech CC3000e
- Logitech MeetUp
- Logitech PTZ Pro
- Logitech PTZ Pro 2
- Logitech Rally
- Logitech Webcam C925e
- Logitech Webcam C920
- Logitech Webcam C930e
- Microsoft® LifeCam Studio
- Poly EagleEye CUBE
- Polycom EagleEye IV
- Surface Hub Smart Camera
- Surface Hub 2 Camera 
- Yealink UVC30 
- Yealink UVC34
- Yealink UVC40 
- Yealink UVC50 
- Yealink UVC80 
- Yealink UVC84

## Manage Cloud IntelliFrame

Cloud IntelliFrame is ideal for focus rooms and medium spaces. It may not be ideal for large spaces as people farthest from the camera may appear blurry after digital zoom. You may also want to switch off Cloud IntelliFrame in rooms with glass walls without any privacy filter.

To switch off Cloud IntelliFrame in a room, perform the following steps:

1. Create an XML configuration file by following the steps in [Create an XML configuration file](../rooms/xml-config-file.md).
1. Add the following element in the *SkypeSettings.xml* file.

   ```XML
   <EnableCloudIntelliframe>false</EnableCloudIntelliframe>
   ```

1. Restart the console for the configuration changes to take effect.

> [!IMPORTANT]
> You are responsible for compliance with local laws and regulations when you enable Cloud IntelliFrame in a particular jurisdiction, including with respect to obligations around notice, consent, and data retention. These obligations may include installing appropriate signage outside any meeting room where you enable Cloud IntelliFrame advising people about the feature.
> Cloud IntelliFrame does not have the capacity to identify particular individuals, due to the uncertainty regarding the scope of “biometrics” in the State of Illinois law; therefore, Cloud IntelliFrame is not intended for use in Illinois.
