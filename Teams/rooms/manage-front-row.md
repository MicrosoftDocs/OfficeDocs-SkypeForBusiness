---
title: Remotely configure front row layout on Teams Rooms
ms.author: tonysmit
author: mstonysmith
ms.reviewer: yoojinjung
ms.date: 08/21/2024
manager: pamgreen
ms.topic: article
audience: Admin
ms.service: msteams
ms.subservice: itpro-rooms
appliesto: 
  - Microsoft Teams
ms.collection: 
  - M365-collaboration
  - teams-rooms-devices
  - Tier1
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
description: Remotely configure the front row layout on Microsoft Teams Rooms systems.
---

# Remotely configure Front Row on Teams Rooms

Front Row is an inclusive meeting layout available on Microsoft Teams Rooms systems that fosters a deeper connection between in-person and virtual meeting participants. Front Row allows you to maximize screen real estate so you can see both people, content, and chat simultaneously.

If you have multiple Teams Rooms systems deployed in your organizations, you can configure Front Row on those systems remotely using an XML configuration file. This XML configuration file can be deployed from a central location to your Teams Rooms systems. When the XML file is deployed to a Teams Rooms system, the configuration settings defined within it will be applied the next time the system is restarted.

For more information about the Teams Rooms XML configuration file, see [Manage a Microsoft Teams Rooms console settings remotely with an XML configuration file](xml-config-file.md).

## Set Front Row as the default layout

If you don't set a default display layout for a room in your XML configuration, the default layout will be set to Gallery. To see Front Row as the default layout, add `<DefaultFoRExperience>1</DefaultFoRExperience>` to your XML configuration file.

End-users can switch from the default display layout using the view switcher during meetings.

## Set Front Row video height size

You can control the video height size of Front Row to give more or less space to meeting participant video or to meeting content. To set the size, add `<FrontRowVideoSize>` to your XML configuration file. You can set `<FrontRowVideoSize>` to `small`, `medium`, or `large`. The default is `medium`. For example, to set the front row size to large, use `<FrontRowVideoSize>large</FrontRowVideoSize>`.

## Set the default Front Row panel component

Configure the position of the raise hand and chat components in the meeting panels to the left and right of meeting content on front-of-room displays. To manually configure the position of the raise hand and chat components, specify the numeric values of the component that should be shown in the left and right panels respectively, separated by a comma. Panels using the same component will be ignored except for "Hide" (for example, `1,1` can be accepted).
- `1` Hide the panel.
- `2` Show meeting chat.
- `3` Show raised hand list.

If `FrontRowPanelDefaults` isn't specified in dual display mode, the raise hand component is shown in the left panel and chat component is shown in the right panel. In single display mode, the left panel isn't displayed by default for front-of-room displays narrower than 21:9.

For example, to default to have the raised hand list in the left panel and chat in the right panel, use the following:

```xml
<FrontRowPanelDefaults>3,2</FrontRowPanelDefaults>
```

## Turn off Front Row

Front Row is enabled by default. Turn off Front Row if you don't want to allow end-users to use Front Row in a certain room. To disable Front Row, add `<FrontRowEnabled>false</FrontRowEnabled>` to your XML configuration file.

## Video segmentation and unified background :::image type="icon" source="../media/mtr-pro-icon.png":::

Front Row removes individual backgrounds, adjusts video participant’s size, and applies a unified background for remote participants to make them appear as if they are in the same room. This removes distractions and provides in-room meeting participants with better connection to remote participants in Teams meetings.
The unified background is turned ON by default for the Teams Rooms on Windows devices with 4 cores or higher CPUs. Devices with lower processing capability will optimize for audio and video quality and will not enable this feature. Room admins can turn this feature ON or OFF via XML and end user control is also provided in the layout switcher during a Teams meeting.
To turn off the unified background, add `<IsFrontRowUnifiedBackgroundEnabled>false</IsFrontRowUnifiedBackgroundEnabled>` to your XML configuration file.

## Spatial audio on Front Row :::image type="icon" source="../media/mtr-pro-icon.png":::

Spatial Audio in Teams Rooms on Windows brings next-generation audio to the Front Row experience when connected to stereo speakers. This intelligent audio technology delivers a more natural and inclusive experience for in-room participants by playing audio from channel closer to physical location of remote participants on Front row layout, making it feel like remote people are in the room with them and reducing meeting fatigue.

You can achieve the best spatial audio experience with [Teams-certified stereo speakers](certified-hardware.md?tabs=Peripherals) and by following guidance on designing a [Signature Teams Rooms](room-planning-guidance.md?tabs=emtr#signature-teams-room-1).

Spatial audio is turned OFF by default. To enable the feature, add `<IsSpatialAudioEnabled>true</IsSpatialAudioEnabled>` to your XML configuration file. Once the feature is enabled, you can also turn it ON or OFF using the audio setting under … (More) menu during a meeting. This toggle affects every meeting joining from the device. 


