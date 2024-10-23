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

Deploying one or many Microsoft Teams phone devices requires planning. One of the key considerations is your organization's network capacity and quality of service (QoS) configuration.

This article explains:

1. [How much bandwidth does a Microsoft Teams phone device use?](#how-much-bandwidth-does-a-microsoft-teams-phone-device-use)
1. [How to control that bandwidth usage?](#how-do-i-control-microsoft-teams-phone-bandwidth-usage)
1. [How to ensure your devices are optimized with the right quality of service (QoS) configuration to align to your organizations requirements?](#quality-of-service-qos-with-microsoft-teams-phones)

Wired network connectivity is recommended for Microsoft Teams phone devices. If wireless network connectivity is the only option, see best practice guidance [here](../Phones/prepare-network-teams-phones.md#wireless-network-considerations).

## How much bandwidth does a Microsoft Teams phone device use?

Microsoft Teams phone is designed to give the best audio experience regardless of your network conditions.

The following table provides rough estimates of bandwidth utilized for the various streams in *kbps* (down/up)

|Feature  |Standard  |Advanced  |
|---------|---------|---------|
|Audio     | 58/58        |     76/75    |

## How do I control Microsoft Teams phone bandwidth usage?

If you wish to implement a bandwidth policy on your common area phones, we recommend allocating 100 kbps to each Teams phone resource account. This implementation can be accomplished by assigning a Teams meeting policy with a media bitrate limit configured. When setting the meeting policy at 100 kbps, Teams phones still only use the bandwidth required for the call, and dynamically adjusts if its network connection isn't able to sustain 100 kbps. For user signed in devices, the meeting policy assigned to the users account will also apply to the Teams phone device.

For information on how to configure a Teams meeting policy, see [Meeting policy settings for audio and video](../meeting-policies-audio-and-video.md). You want to create a custom policy and assign it to all Microsoft Teams phone resource accounts, with the limit for media bitrate configured for 100 kbps.

## Quality of Service (QoS) with Microsoft Teams phones

Microsoft Teams Rooms supports Quality of Service (QoS) Differentiated Services Code Point (DSCP) markings to ensure you can manage the media traffic on your corporate network.

We recommend the following QoS markings and port ranges for the audio, video, and application/screen sharing types of media traffic:

**Audio**:

- Client source port range: **50,000-50,019**
- Protocol: **TCP/UDP**
- DSCP value: **46**
- DSCP class: **Expedited Forwarding (EF)**

**Calling and Meetings Signaling**:

- Client source port range: **50,070-50,089**
- Protocol: **UDP**
- DSCP value: **40**
- DSCP class: **CS5**

For more information on Teams Media and implementing QoS, see [Implement Quality of Service (QoS) in Microsoft Teams](../QoS-in-Teams.md).

For Teams phones, you need to configure your Microsoft Teams tenant to insert QoS markings. Teams phone devices honor this policy and apply the markings defined earlier in this document.

For instructions on how to configure your tenant to insert QoS markings, see [Teams settings and policies reference](../settings-policies-reference.md).

## Related articles

- [Implement Quality of Service (QoS) in Microsoft Teams](../QoS-in-Teams.md)
- [Implement Quality of Service (QoS) in Microsoft Teams clients](../QoS-in-Teams-clients.md)
- [Configure the NetworkQoSPolicy CSP](/windows/client-management/mdm/networkqospolicy-csp)
- [Prepare your organization's network for Microsoft Teams](../prepare-network.md)
