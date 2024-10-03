---
title: Proximity Join using Bluetooth and ultrasound
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
description: Learn how to use the Proximity Join feature using Bluetooth and Ultrasound connnectivity to nudge a Microsoft Teams Room console into a meeting you are having for an optimum meeting room experience.
f1keywords: NOCSH
---

# Proximity Join using Bluetooth and ultrasound

Proximity Join is a feature that lets you use your Teams app on a desktop or mobile device to invite or nudge a Microsoft Teams Rooms console into a Teams meeting. Before you nudge the Teams Rooms console into the meeting, the room doesn't have to be already invited or added to the meeting. This feature uses wireless technologies that can be individually turned on or off depending on the requirements of the environment including:

- [Bluetooth](#bluetooth)
- [Ultrasonic sound (Ultrasound)](#ultrasound)

The end user experience is the same if Bluetooth or ultrasound are used for Proximity Join to join a meeting. If they're both turned on, they operate together and in parallel. A Teams Room that is found with ultrasound turned on is always put in the meeting's prejoin screen at the top of the list of nearby rooms. You can see it's available in the room audio option. Teams Rooms that are found using Bluetooth are listed after the room that have ultrasound turned on in that list.

Once a connection is established between a personal laptop or mobile device with the Teams app and a Teams Room console, the user's video won't appear in the room's display, and the room's video stream is hidden on the personal device's meeting stage.

## Bluetooth

Bluetooth is a short range wireless technology in which compatible devices can use it to communicate. However, this signal can penetrate through walls. Rooms discovered through Bluetooth are sorted by signal strength in descending order, and it includes all Teams Rooms both in use and not in use. This is because the Bluetooth signal isn't paused when Microsoft Teams Room has joined a meeting.

Bluetooth connectivity is available on both Microsoft Teams Rooms on Android and Microsoft Teams Rooms on Windows.

## Ultrasound

Ultrasound signaling is available on Microsoft Teams Rooms on Windows, beacons from compatible consoles, and can be used to along with Bluetooth for people that want a Teams Rooms to join a meeting. 

> [!NOTE]
> Proximity Join using ultrasound isn't currently available for Teams Rooms on Android.

The Proximity Join via ultrasound works by emitting an ultrasonic (19.5 kHz - 21.5 kHz) signal from the Teams Room console that isn't audible to humans. It's more accurate than Bluetooth because at reasonable volume, it won't penetrate through walls. Plus, the signal is paused when the Microsoft Teams Room is either in a meeting or HDMI ingest is active. For example, you walk into a conference room with ultrasound turned on the Teams Rooms console, and you want to join your meeting to the Teams Room, you see it in the meeting's prejoin screen in the list of available rooms because those rooms are sorted and listed at the top of the screen. This lets someone select the exact Teams Rooms console and conference room they want to use for their meeting.

> [!NOTE]
> Room Remote can't be used with ultrasound only because the ultrasound beacon is paused while the Teams Room is in a call. Room Remote can't use ultrasound to verify that the personal device is in proximity with the room, so Room Remote won't work if only ultrasound is turned on.

> [!CAUTION]
> Some younger people and animals with sensitive hearing may be able to hear it. In our testing, this sound hasn't been distressing, but take note if young people or animals are in your meeting room environment. We recommend that younger people and animals aren't present in the meeting room environments. If the beacon can be heard outside of the space for which it is intended to represent, speak with your admin. While Microsoft works with partners to ensure volume levels are adequately capped, your admin may have overridden the volume for ultrasound emission on a console or audio peripheral that will in turn may have unintended consequences.

### Ultrasound supported devices

|Sender (Consoles for Teams Rooms on Windows)|Receiver|
| -------- | -------- |
|Crestron UC-2   |Teams on Windows (minimum version 24193.1805.3040.8975)|
|Crestron MercuryX   |Teams on MacOS (minimum version 24193.1707.3028.4282)   |
|Lenovo Hub 500||
|Lenovo ThinkSmart Audio G2||
|Logi Tap||



## Administration and settings

There are multiple ways and tools you can use to manage Proximity Join settings for Microsoft Teams Rooms.

> [!NOTE]
> The settings for ultrasound don't apply to Teams Room on Android but the Bluetooth settings are available for those devices.

### [Teams Rooms Pro portal](#tab/portal)

Management of proximity features is available in the Teams Rooms Pro Management portal:

- Enable Bluetooth beaconing

  - Remote control from personal devices
    
  - Automatically accept proximity-based meeting invitations
    
- Enable ultrasound beaconing

  - Remote control from personal devices
    
### [Teams Rooms app settings](#tab/app-settings)

Management of proximity features is available on Microsoft Teams Rooms admin settings:

- Enable Bluetooth beaconing

  - Remote control from personal devices
    
  - Automatically accept proximity-based meeting invitations
    
- Enable ultrasound beaconing

  - Remote control from personal devices
    
### [XML configuration file](#tab/xml)

Like most Teams Rooms on Windows features, you can update the settings of your device with the Teams Rooms XML configuration file. The XML configuration file lets you remotely deploy configuration changes to one or more Teams Rooms on Windows devices in your organization. For more information, see [Manage a Microsoft Teams Rooms console settings remotely with an XML configuration file](/microsoftteams/rooms/xml-config-file).

|**Paramater**|**Type**|**Level**|**Usage**|
|:-------- |:-------- |:-------- |:-------- |
|BluetoothAdvertisementEnabled|Boolean ❷|First ❶|Enabled by default.|
|AutoAcceptProximateMeetingInvitations|Boolean ❷|First ❶|If true, proximity based meeting invitations using Bluetooth are automatically accepted. Enabled by default.|
|AutoAcceptProximateMeetingInvitations|Boolean ❷|First ❶|If true, proximity based meeting invitations using Bluetooth are automatically accepted. Enabled by default.|
|UltrasoundAdvertisementEnabled|Boolean ❷|First ❶|Enabled by default.|
|UltrasoundAutoAcceptProximateMeetingInvitations|Boolean ❷|First ❶|If true, proximity based meeting invitations using Bluetooth are automatically accepted. Enabled by default.|

