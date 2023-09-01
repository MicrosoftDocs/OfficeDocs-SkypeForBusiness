---
title: Quality of service (QoS) configuration on Teams Room devices
author: v-smandalika
ms.author: v-smandalika
manager: dansimp
ms.date: 09/01/2023
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.subservice: itpro-devices
audience: Admin
ms.collection: 
  - M365-collaboration
  - teams-rooms-devices
  - Teams_ITAdmin_Devices
  - Tier1
f1.keywords: 
  - NOCSH
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn about how much bandwidth a Teams Room will use, how to control that bandwidth usage, and how to ensure your devices are optimized with the right quality of service configuration to align to your organizations requirements.
---

# Quality of service (QoS) configuration on Teams Room devices

Deploying one or many Microsoft Teams Rooms devices requires planning. The key considerations are your organization's network bandwidth and quality of service (QoS) configuration.

This article explains:

1. How much bandwidth a Teams Room device will use.
1. How to control that bandwidth usage.
1. How to ensure your devices are optimized with the right quality of service (QoS) configuration to align to your organizations requirements.

   :::image type="content" source="../media/teams-room-device-qos-configuration.png" alt-text="Screenshot that shows a Teams Room device with QoS configuration." lightbox="../media/teams-room-device-qos-configuration.png":::

Wired network connectivity is recommended for Microsoft Teams Room devices.

If wireless network connectivity is the only option, see best practice guidance [here](../rooms/rooms-plan.md).

## How much bandwidth a Teams Room device will use

Microsoft Teams Rooms is designed to give the best audio, video, and content-sharing experience regardless of your network conditions. That said, when bandwidth is insufficient, Teams prioritizes audio quality over video quality.

Where bandwidth isn't limited, Teams optimizes media quality, including high-fidelity audio, up to 1080p video resolution, and up to 30 fps (frames per second) for video and content.

|||Bandwidth in kbps (up/down)||
|---------|---------|---------|---------|
| **Media traffic type**   | **Minimum**         |**Standard**       |**Optimal performance**|
| Audio     | 64/64    | 128/128       | 256/256         |
| Video     | 150/200        | 2500/4000         | 8000/4000         |
| Screen share     | 250/250         | 2500/2500         | 4000/4000         |

Teams Rooms can support up to 18 incoming video streams at once, and the number of video streams on the screen(s) can have a large impact on the amount of downstream bandwidth consumed. This impact is because Teams will downscale the incoming streams to provide a high-quality-in-room experience while consuming the least amount of bandwidth possible.  The bandwidth consumption can also vary with the resolution of the cameras the remote participants have connected to the meeting.

## How to control bandwidth usage on a Teams Room

By default, Teams Rooms doesn't have a bandwidth-limiting policy assigned. If you wish to implement one, we recommend allocating 10 Mbps to each Teams Room account to set a Teams Meeting Policy to limit the media bitrate. When setting the meeting policy at 10 Mbps, Teams Rooms will still only use the bandwidth required for the meeting, and it will dynamically adjust if its network connection isn't able to sustain 10 Mbps.

For information on how to configure a Teams Meeting Policy, see [Meeting policy settings for audio and video](../meeting-policies-audio-and-video.md). You’ll want to create a custom policy and assign it to all Microsoft Teams Room resource accounts, which limits the media bitrate to 10,000 kbps.

## Quality of Service (QoS) with Microsoft Teams Rooms

Microsoft Teams Rooms supports Quality of Service (QoS) Differentiated Services Code Point (DSCP) markings to ensure you can manage the media traffic on your corporate network.

We recommend the following QoS markings and port ranges for the audio, video, and application/screen sharing types of media traffic:

**Audio**:

- Client source port range: **50,000-50,019**
- Protocol: **TCP/UDP**
- DSCP value: **46**
- DSCP class: **Expedited Forwarding (EF)**

**Video**:

- Client source port range: **50,020-50,039**
- Protocol: **TCP/UDP**
- DSCP value: **34**
- DSCP class: **Assured Forwarding (AF41)**

**Application/screen sharing**:

- Client source port range: **50,040-50,059**
- Protocol: **TCP/UDP**
- DSCP value: **18**
- DSCP class: **Assured Forwarding (AF21)**

For more information on Teams Media and implementing QoS, see [Implement Quality of Service (QoS) in Microsoft Teams](../QoS-in-Teams.md).

### QoS with Microsoft Teams Rooms on Windows

For Teams Rooms on Windows devices, you must configure Windows to add DSCP to the Teams Room application traffic. We recommend using Microsoft Intune to apply a Network QoS policy to Teams Rooms. You can use the Intune “NetworkQoSPolicy” CSP to apply the configuration based on the port ranges and DSCP value shown in [Quality of Service (QoS) with Microsoft Teams Rooms](#quality-of-service-qos-with-microsoft-teams-rooms).

For more information on this Intune CSP, see [NetworkQoSPolicy CSP](/windows/client-management/mdm/networkqospolicy-csp).

If your Teams Rooms devices are joined to Active Directory, you can use Group Policy to apply the markings. You can follow the same instructions that have been provided for the Teams Desktop application, but don't specify the application name in the configuration; only specify the port range and the DSCP value in the configuration.

For more information, see [Implement Quality of Service (QoS) in Microsoft Teams clients](../QoS-in-Teams-clients.md).

### QoS with Microsoft Teams Rooms on Android

For Teams Rooms on Android devices, you'll need to configure your tenant to insert QoS markings at which point the Teams Room on Android devices will apply the markings defined earlier in [Quality of Service (QoS) with Microsoft Teams Rooms](#quality-of-service-qos-with-microsoft-teams-rooms).

For instructions on how to configure your tenant to insert QoS markings, see [Teams settings and policies reference](../settings-policies-reference.md).

## Related articles

- [Implement Quality of Service (QoS) in Microsoft Teams](../QoS-in-Teams.md)
- [Implement Quality of Service (QoS) in Microsoft Teams clients](../QoS-in-Teams-clients.md)
- [NetworkQoSPolicy CSP](/windows/client-management/mdm/networkqospolicy-csp)
- [Prepare your organization's network for Microsoft Teams](../prepare-network.md)

