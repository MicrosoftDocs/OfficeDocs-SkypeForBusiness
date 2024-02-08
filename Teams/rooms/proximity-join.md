---
title: Proximity Join
author: v-smandalika
ms.author: v-smandalika
manager: dansimp
ms.date: 02/07/2024
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.subservice: itpro-rooms
audience: Admin
ms.collection: 
  - M365-collaboration
  - teams-rooms-devices
  - Tier3
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn how to use Proximity Join to nudge your meeting room into MTR for an optimum meeting room experience
f1keywords: 
---

# Proximity Join

Proximity Join is a feature that enables you to nudge your meeting room into a Microsoft Teams Rooms so that your meeting room can sync with Microsoft Teams Rooms. Your personal device, for example, your desktop or mobile phone, detects Microsoft Teams Rooms through a wireless signal.

If your personal device is a desktop, then using the TEAMS app, you detect an ultrasonic sound and capture a Microsoft Teams Rooms and nudge your meeting room into it. For more information, see [How to detect Microsoft Teams Rooms using Proximity Join from TEAMS app on your desktop](#how-to-detect-microsoft-teams-rooms-using-proximity-join-from-teams-app-on-your-desktop).

If your personal device is a mobile phone, then using the TEAMS app, you detect a bluetooth signal and capture a Microsoft Teams Rooms and nudge your meeting room into it. For more information, see [How to detect Microsoft Teams Rooms using Proximity Join from TEAMS app on your mobile](#how-to-detect-microsoft-teams-rooms-using-proximity-join-from-teams-app-on-your-mobile).

The Proximity Join feature provides you with the following advantages:

1. You can easily access a meeting room that has Microsoft Teams Rooms in it. That is, the process of making your meeting room equipped what Microsoft Teams Rooms offers is easy.
1. You don't have to touch any console or enter the ID of your meeting room when you're nudging it into Microsoft Teams Rooms.
1. You enter into such a meeting room (that has Microsoft Teams Rooms in it) in which your personal webcam feed is hidden from the room display.

## Why is Proximity Join useful/desirable

The advantages of the Proximity Join feature are:

- It's the easiest way to join a meeting on Microsoft Teams Rooms.
- There's no need to touch the console or type in a meeting ID.
- It activates other helpful features, like hiding your personal webcam feed on the room display.

## How does it work?

When the Proximity Join feature is enabled, MTRs emit beacons for nearby devices to find. This beacon contains the identity of the MTR so your personal device can “nudge” it into a meeting, and some security and configuration data.

Beacons are of two types:

1. [Ultrasonic sound (Ultrasound)](#ultrasonic-sound-ultrasound)
1. [Bluetooth](#bluetooth)

### Ultrasonic sound (Ultrasound)

The "Ultrasound" is one of the types of the beacon that's emitted for personal devices to detect and to resolve the MTR into which you nudge your meeting room.

> [!NOTE]
> This type of beacon isn't supported in mobile phones.

The Ultrasound beacon has the following characteristics:

1. It emits an ultrasonic sound on a cyclical basis. The beacon information is contained within the sound wave.
1. It uses a frequency range of 19.5kHz to 21.5 kHz.
1. It isn't audible to humans .

   > [!CAUTION]
   > Some younger people and animals with sensitive hearing may be able to hear it. In our testing, this sound hasn't been distressing, but take note if young people or animals are in your meeting room environment. We recommend that younger people and animals are not present in the meeting room environments.

1. It's more secure and accurate because at reasonable amplitudes, it doesn't go through walls. Because of this advantage, rooms discovered via ultrasound are always placed at the top of the list.
1. This beacon does not emit during a meeting.

### Bluetooth

Bluetooth is the other type of beacon that's emitted for personal devices to detect and to discover the MTR into  which you nudge your meeting room.

The Bluetooth beacon has the following characteristics:

1. It emits a continuous Bluetooth signal that personal devices can detect.
1. This beacon does emit during a meeting.
1. The Microsoft Teams Rooms it discovers are sorted in order of descending signal strength.

##### Limitation

As Bluetooth signals typically go through walls, may be less accurate and less secure.

Once your personal device receives the beacon, it resolves the identity of the MTR in your enterprise database and “calls” it, asking the MTR to join the meeting you’ve requested it to

## How to use Proximity Join

You can use the Proximity Join feature through the TEAMS application on your desktop or mobile.

### How to detect Microsoft Teams Rooms using Proximity Join from TEAMS app on your desktop

To use the Proximity Join to nudge your meeting room into Microsoft Teams Rooms from the TEAMS app on your desktop, perform the following steps:

1. Ensure your Bluetooth is on and your microphone isn't disabled or muted. 
 
  > [!NOTE]
  > When your desktop has bluetooth and microphone turned on, it will be able to detect an [ultrasonic sound](#ultrasonic-sound-ultrasound) or a [bluetooth](#bluetooth) signal which contains information about the beacon

1. Join an existing meeting or start a new one.
1. In pre-join, select **Room Audio**.
1. If you don’t immediately see your meeting room listed, wait for 5-10 seconds.
   > [!WARNING]
   > The UI may indicate no rooms were found while it's still searching.
1. Select your meeting room once it's listed, and select **Join**.
   > [!WARNING]
   > Double-check that the meeting room you've selected is the one you are in, so as to avoid disruptions and security leaks.

   The Microsoft Teams Rooms should now be in your meeting room.

### How to detect Microsoft Teams Rooms using Proximity Join from TEAMS app on your mobile

To use the Proximity Join to nudge your meeting room into Microsoft Teams Rooms from the TEAMS app on your mobile, perform the following steps:

1. Ensure Bluetooth is on (ultrasound isn't supported on mobile).
1. Choose a meeting from your calendar and select **Join**, or select the **+** button and select **Meet Now**.
1. In the pre-join screen, select **More Join Options**.
1. Select **Join a meeting room**.
1. Wait for a nearby meeting room to be found, select it, and select **Join**.



