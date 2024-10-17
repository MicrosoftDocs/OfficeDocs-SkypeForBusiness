---
title: Quality of service (QoS) configuration on Teams phones
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: mattslomka
ms.date: 10/17/2024
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
ms.localizationpriority: medium
search.appverid: MET150
description: Learn about the key considerations for deploying Quality of Service (QoS) on your network to support Teams phones.
---

# Quality of service (QoS) set up on Teams phones

Deploying one or many Microsoft Teams Rooms devices requires planning. One of the key considerations is your organization's network capacity and quality of service (QoS) configuration.

This article explains:

1. [How much bandwidth does a Microsoft Teams Rooms device use?](#how-much-bandwidth-does-a-microsoft-teams-rooms-device-use)
1. [How to control that bandwidth usage?](#how-do-i-control-microsoft-teams-rooms-bandwidth-usage)
1. [How to ensure your devices are optimized with the right quality of service (QoS) configuration to align to your organizations requirements?](#quality-of-service-qos-with-microsoft-teams-rooms)

Wired network connectivity is recommended for Microsoft Teams Rooms devices. If wireless network connectivity is the only option, see best practice guidance [here](../rooms/rooms-prep.md#wireless-network-considerations).

## How much bandwidth does a Microsoft Teams Rooms device use?

Microsoft Teams Rooms is designed to give the best audio, video, and content-sharing experience regardless of your network conditions. That said, when bandwidth is insufficient, Teams prioritizes traffic in the following order: audio, content sharing, lastly participant video.

Where bandwidth isn't limited, Teams optimizes media quality, including high-fidelity audio, up to 1080p video resolution, and up to 30 fps (frames per second) for video and content.

The following table provides rough estimates of bandwidth utilized for the various streams in *kbps* (down/up)


|Feature  |Standard  |Advanced  |
|---------|---------|---------|
|Audio     | 128/128        |     256/256    |
|Video    |    2000/4000     |8000/4000         |
|Screen share     |    2000/2000     |   2000/2000      |
|**Total**     |  **4128/6128**       |**10256/6256**         |


Teams Rooms can support up to 18 individual incoming video streams, up to five outbound video streams, and content sharing either inbound or outbound. The number of streams consumed by the Teams Rooms device can have a large impact on the downstream bandwidth consumed, and the capabilities of the connected Teams Rooms camera can impact the outbound bandwidth usage. Bandwidth consumption can also vary with the number and resolution of the videos from remote participants connected to the meeting.

## How do I control Microsoft Teams Rooms bandwidth usage?

By default, Teams Rooms don't have a bandwidth-limiting policy. If you wish to implement one, we recommend allocating 10 Mbps to each Teams Rooms resource account. This implementation can be accomplished by assigning a Teams meeting policy with a media bitrate limit configured. When setting the meeting policy at 10 Mbps, Teams Rooms still only use the bandwidth required for the meeting (typically 3-4 Mbps), and dynamically adjusts if its network connection isn't able to sustain 10 Mbps.

For information on how to configure a Teams meeting policy, see [Meeting policy settings for audio and video](../meeting-policies-audio-and-video.md). You want to create a custom policy and assign it to all Microsoft Teams Rooms resource accounts, with the limit for media bitrate configured for 10,000 kbps.

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

### QoS with Microsoft Teams Rooms on Windows devices

For Teams Rooms on Windows devices, you must configure Windows to add DSCP markings to the Teams Rooms application traffic. We recommend using Microsoft Intune to apply a Network QoS policy to Teams Rooms devices. You can use the Intune `NetworkQoSPolicy` configuration service provider (CSP) to apply the configuration based on the port ranges and DSCP value shown in [Quality of Service (QoS) with Microsoft Teams Rooms](#quality-of-service-qos-with-microsoft-teams-rooms).

For more information on this Intune CSP, see [NetworkQoSPolicy CSP](/windows/client-management/mdm/networkqospolicy-csp).

If your Teams Rooms devices are joined to Active Directory, you can use Group Policy to apply the markings. Follow the instructions for the Teams Desktop application, but don't specify the application name in the configuration; only specify the port range and the DSCP value in the configuration.

For more information, see [Implement Quality of Service (QoS) in Microsoft Teams clients](../QoS-in-Teams-clients.md).

### QoS with Microsoft Teams Rooms on Android devices

For Teams Rooms on Android devices, you need to configure your Microsoft Teams tenant to insert QoS markings. Teams Rooms on Android devices honor this policy and apply the markings defined earlier in [Quality of Service (QoS) with Microsoft Teams Rooms](#quality-of-service-qos-with-microsoft-teams-rooms) with one exception, Application/screen sharing uses a DSCP value of 34 (AF41) aligned to video traffic.

For instructions on how to configure your tenant to insert QoS markings, see [Teams settings and policies reference](../settings-policies-reference.md).

## Related articles

- [Implement Quality of Service (QoS) in Microsoft Teams](../QoS-in-Teams.md)
- [Implement Quality of Service (QoS) in Microsoft Teams clients](../QoS-in-Teams-clients.md)
- [Configure the NetworkQoSPolicy CSP](/windows/client-management/mdm/networkqospolicy-csp)
- [Prepare your organization's network for Microsoft Teams](../prepare-network.md)
