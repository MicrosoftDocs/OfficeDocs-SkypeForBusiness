---
title: Proximity Join
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: leungsam
ms.date: 09/18/2024
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.subservice: itpro-rooms
audience: Admin
ms.collection: 
  - teams-rooms-devices
  - Teams_ITAdmin_Devices
  - Tier1
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn how to use Proximity Join to nudge your meeting room into MTR for an optimum meeting room experience.
f1keywords: NOCSH
---

# Overview of Proximity Join

Proximity Join is a feature that enables you to nudge your Microsoft Teams Rooms into a Teams meeting from your Teams app on desktop or mobile. It doesn't require the room to be invited to the meeting prior to nudging it into the meeting. This feature uses wireless technologies that can be individually enabled or disabled depending on the requirements of the environment:

1. [Bluetooth](#bluetooth)

1. [Ultrasonic sound (Ultrasound)](#ultrasonic-sound-ultrasound)

The end user experience is the same regardless of the technology used for proximity join. If both are enabled, both technologies operates in parallel. A room found with ultrasound will prioritize in the list of nearby rooms of a meeting pre-join screen in the room audio option. Rooms found with Bluetooth is listed after the ultrasound detected room.

Once proximity has been established between a personal device and a Teams Room, the user's video won't appear in the room's display, and the room's video stream is hidden on the personal device's meeting stage.

## Admin Controls

Admins have the ability to configure each Microsoft Teams Room to emit either Bluetooth, ultrasound, or both depending on device capability.

### XML configuration file for Teams Rooms on Windows

Like most Teams Rooms on Windows features, you can update the settings of your device with the Teams Rooms XML configuration file. The XML configuration file lets you remotely deploy configuration changes to one or more Teams Rooms on Windows devices in your organization. For more information, see [Manage a Microsoft Teams Rooms console settings remotely with an XML configuration file](/microsoftteams/rooms/xml-config-file).

|**Parmater**|**Type**|**Level**|**Usage**|
| -------- | -------- | -------- | -------- |
|BluetoothAdvertisementEnabled|Boolean ❷|First ❶|Enabled by default.|
|AutoAcceptProximateMeetingInvitations|Boolean ❷|First ❶|If true, proximity based meeting invitations via Bluetooth are automatically accepted. Enabled by default.|
|UltrasoundAdvertisementEnabled|Boolean ❷|First ❶|Enabled by default.|
|UltrasoundAutoAcceptProximateMeetingInvitations|Boolean ❷|First ❶|If true, proximity based meeting invitations via Bluetooth are automatically accepted. Enabled by default.|
|UltrasoundSpeaker| ? | ? | Device name (string) is the acceptable value. No default value. If empty, MTR uses console speaker provided it's a supported speaker |
|UltrasoundSpeakerVolume| ? | ? | Value can be from 0 to 100, default value is 0 |

### Teams Rooms Pro Management Portal

Management of proximity features is available in the Teams Rooms Pro Management portal:

- Allow bluetooth beaconing
- Automatically accept proximity-based meeting invitations
- Remote control from personal devices
- Enable ultrasound beacon
- Automatically accept proximity-based meeting invitations
  
### Teams Rooms App Settings

Management of proximity features is available on Microsoft Teams Rooms admin settings:

- Allow bluetooth beaconing
- Automatically accept proximity-based meeting invitations
- Remote control from personal devices
- Enable ultrasound beacon
- Automatically accept proximity-based meeting invitations
  
## Bluetooth

Bluetooth is a short range wireless technology that compatible devices can communicate over. This signal can penetrate through walls. The signal isn't paused when Microsoft Teams Room is in a meeting. Rooms appearing in the list of discovered rooms via Bluetooth are sorted by signal strength in descending order.

## Ultrasound

Proximity Join via ultrasound works by emitting an ultrasonic (19.5 kHz - 21.5 kHz) signal not audible to humans. It's more secure and accurate than Bluetooth because at reasonable volume won't penetrate through walls. The signal is paused when the Microsoft Teams Room is either in a meeting or HDMI ingest is active.

> [!NOTE]
> Room Remote cannot be used with ultrasound only because the ultrasound beacon is paused while the Teams Room is in a call. Room Remote cannot use ultrasound to verify that the personal device is in proximity with the room, and therefore, Room Remote won't work if only ultrasound is enabled.

> [!CAUTION]
> Some younger people and animals with sensitive hearing may be able to hear it. In our testing, this sound hasn't been distressing, but take note if young people or animals are in your meeting room environment. We recommend that younger people and animals are not present in the meeting room environments. If the beacon can be heard outside of the space for which it is intended to represent, speak to your admin. While Microsoft works with partners to ensure volume levels are adequately capped, your admin may have overridden the volume for ultrasound emission on a console or audio peripheral.

## Supported devices

Microsoft Teams Rooms on Windows with the following consoles:

- Crestron UC-2
- Crestron MercuryX
- Lenovo Hub 500
- Lenovo ThinkSmart Audio G2
- Logi Tap
- Desktop - Teams on Windows (minimum version 24193.1805.3040.8975)
- Desktop - Teams on MacOS (minimum version 24193.1707.3028.4282)