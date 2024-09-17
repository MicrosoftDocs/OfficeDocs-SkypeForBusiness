---
title: Proximity Join
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.date: 02/07/2024
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
description: Learn how to use Proximity Join to nudge your meeting room into MTR for an optimum meeting room experience
f1keywords: NOCSH
---

# Proximity Join

## Overview

Proximity Join is a feature that enables you to nudge your Microsoft Teams Rooms into a Teams meeting from your Teams app on desktop or mobile. It doesn't require the room to be invited to the meeting prior to nudging it into the meeting. This feature uses wireless technologies that can be individually enabled or disabled depending on the requirements of the environment:

1. [Bluetooth](#bluetooth)

1. [Ultrasonic sound (Ultrasound)](#ultrasonic-sound-ultrasound)

The end user experience is the same regardless of the technology used for proximity join.

## Admin Controls

Admins have the ability to configure each Microsoft Teams Room to emit either Bluetooth, ultrasound, or both depending on device capability. 

### XML configuration file for Teams Rooms on Windows

Like most Teams Rooms on Windows features, you can update the settings of your device with the Teams Rooms XML configuration file. The XML configuration file lets you remotely deploy configuration changes to one or more Teams Rooms on Windows devices in your organization. For more information, see [Manage a Microsoft Teams Rooms console settings remotely with an XML configuration file](/microsoftteams/rooms/xml-config-file).


|Parmater|Type|Level|Usage|
| -------- | -------- | -------- | -------- |
|BluetoothAdvertisementEnabled|Boolean ❷|First ❶|Enabled by default.|
|AutoAcceptProximateMeetingInvitations|Boolean ❷|First ❶|If true, proximity based meeting invitations via Bluetooth are automatically accepted. Enabled by default.|
|UltrasoundAdvertisementEnabled|Boolean ❷|First ❶|Enabled by default.|
|UltrasoundAutoAcceptProximateMeetingInvitations|Boolean ❷|First ❶|If true, proximity based meeting invitations via Bluetooth are automatically accepted. Enabled by default.|
|UltrasoundSpeaker| ? | ? | Device name (string) is the acceptable value. No default value. If empty, MTR uses console speaker provided it's a supported speaker |
|UltrasoundSpeakerVolume| ? | ? | Value can be from 0 to 100, default value is 0 |


### Pro Management Portal

Management of proximity features is available on PMP:

- Allow bluetooth beaconing

  - Automatically accept proximity-based meeting invitations
  
  - Remote control from personal devices
  
- Enable ultrasound beacon

  - Automatically accept proximity-based meeting invitations
  
### Teams Rooms App Settings

Management of proximity features is available on MTR admin settings:

- Allow bluetooth beaconing

  - Automatically accept proximity-based meeting invitations
  
  - Remote control from personal devices
  
- Enable ultrasound beacon

  - Automatically accept proximity-based meeting invitations
  
## Bluetooth

Bluetooth is a short range wireless technology that compatible devices can communicate over. This signal can penetrate through walls. The signal isn't paused when Microsoft Teams Room is in a meeting. Rooms appearing in the list of discovered rooms via Bluetooth are sorted by signal strength in descending order.

## Ultrasound

Proximity Join via ultrasound works by emitting an ultrasonic (19.5 kHz - 21.5 kHz) signal not audible to humans. It's more secure and accurate than Bluetooth because at reasonable volume won't penetrate through walls. The signal is paused when the Microsoft Teams Room is either in a meeting or HDMI ingest is active.

> [!CAUTION]
> Some younger people and animals with sensitive hearing may be able to hear it. In our testing, this sound hasn't been distressing, but take note if young people or animals are in your meeting room environment. We recommend that younger people and animals are not present in the meeting room environments. If the beacon can be heard outside of the space for which it is intended to represent, speak to your admin. While Microsoft works with partners to ensure volume levels are adequately capped, your admin may have overridden the volume for ultrasound emission on a console or audio peripheral.

Supported devices:

- Microsoft Teams Rooms on Windows with a dedicated ultrasonic speaker

- Desktop - Teams on Windows

- Desktop - Teams on macOS

## FAQ

#### Q: Is Proximity Join secure?

Yes. We're aware that meetings can have confidential data, and that bad actors may attempt to join meetings they aren't physically present for. The proximity beaconing technology was built with security in mind, and contains various safeguards to mitigate risks.

#### Q: Why did the Microsoft Teams Rooms not automatically accept the call/why did it ring?

1. In some cases, your admin may have turned off autoaccept for security reasons. Contact hour administrator.
1. In other cases, if the beacon is missing certain required security data due to distance, signal strength, or data loss, the Microsoft Teams Rooms may require a manual accept to ensure your meeting stays secure.

#### Q: Why is my video not showing up on the room display?

To increase comfort and reduce distraction, the Microsoft Teams Rooms will hide your personal camera display in the grid after a proximity join.

#### Q: Why is the Microsoft Teams Rooms that is in the room with me not at the top of the list?

1. Bluetooth signals penetrate walls; hence, it may be the case that a Microsoft Teams Rooms in a room next to you or above/below you are physically closer to your device than the Microsoft Teams Rooms in your meeting room. This scenario is especially likely in the following circumstances:
   1. If your room is large and the Microsoft Teams Rooms is on the other side of it.
   1. In floor arrangements where meeting rooms are built back to back.
   1. In setups where the MTR is physically located outside the room (in a server room or equipment closet).
1. Bluetooth signals are also subject to wireless interference. Something may be interfering with the wireless signal of the Microsoft Teams Rooms in your room, causing it’s signal to be weaker than expected.

1. Ultrasound signals are susceptible to noise from other ultrasound beacons and may cause the signal to not be recognizable.

#### Q: Does Proximity Join work across tenants?

Yes, Proximity Join works across tenants, though this currently requires a workaround to get this provision to work. To allow your personal device to resolve the identity of a Microsoft Teams Rooms external to your O365 tenant, you must first search for the name or email address of the Microsoft Teams Rooms device in Teams and send it a chat message. Microsoft is working on addressing this issue; so, a workaround will no longer be required.

#### Q: What is TeamsCast?

TeamsCast is a feature that uses Proximity Join to nudge a Microsoft Teams Rooms into a meeting, immediately followed by an automatic content share. Most issues with TeamsCast fall under the umbrella of Proximity Join, and the guidance in this article can be cross-applied.

#### Q: What happens if both Bluetooth and ultrasound is enabled?

Both technologies will operate in parallel. A room found with ultrasound will be prioritized in the list of nearby rooms of a meeting pre-join screen in the room audio option. Rooms found with Bluetooth will be listed after the ultrasound detected room.

#### Q: Why can't I use Room Remote with ultrasound only?

Because the ultrasound beacon is paused while the Teams Room is in a call, Room Remote cannot use ultrasound to verify that the personal device is in proximity with the room, and therefore, Room Remote will not work if only ultrasound is enabled.

