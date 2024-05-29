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

Proximity Join is a feature that enables you to nudge your Microsoft Teams Rooms into a Teams meeting from your Teams app on desktop or mobile. It does not require the room to be invited to the meeting prior to nudging it into the meeting. This feature uses wireless technologies that can be individually enabled or disabled depending on the requirements of the environment:

1. [Bluetooth](#bluetooth)

1. [Ultrasonic sound (Ultrasound)](#ultrasonic-sound-ultrasound)

### How to use

*update for mobile vs desktop

1. Ensure IT admins have correctly configured the Microsoft Teams Rooms correctly. See [Admin Controls](#Admin-Controls)

1. On your personal device, ensure Bluetooth is enabled for Bluetooth, and the microphone is not muted or disabled for ultrasound

1. Join an existing meeting or start a new one on your Teams app

1. In pre-join, click Room Audio. If you don’t immediately see the room you are in, wait for 5-10 seconds

   1. Warning: the UI may indicate no rooms were found while it is still searching
      
1. Select the room you are in and click join

   1. Warning: double check the room you have selected is the one you are in to avoid disruptions and security leaks
      
1. The Microsoft Teams Room should now be in the meeting

## Admin Controls

Admins have the ability to configure each Microsoft Teams Room to emit either Bluetooth, ultrasound, or both depending on device capability. 

### XML configuration file for Teams Rooms on Windows

Like most Teams Rooms on Windows features, you can update the settings of your device with the Teams Rooms XML configuration file. The XML configuration file lets you remotely deploy configuration changes to one or more Teams Rooms on Windows devices in your organization. For more information, see [Manage a Microsoft Teams Rooms console settings remotely with an XML configuration file](/microsoftteams/rooms/xml-config-file).


|Element|Type|Level|Usage|
| -------- | -------- | -------- | -------- |
|<BluetoothAdvertisementEnabled>|Boolean ❷|First ❶|Enabled by default.|
|<AutoAcceptProximateMeetingInvitations>|Boolean ❷|First ❶|If true, proximity based meeting invitations via Bluetooth are automatically accepted. Enabled by default.|
|<UltrasoundAdvertisementEnabled>|Boolean ❷|First ❶|Enabled by default.|
|<UltrasoundAutoAcceptProximateMeetingInvitations>|Boolean ❷|First ❶|If true, proximity based meeting invitations via Bluetooth are automatically accepted. Enabled by default.|
| <UltrasoundSpeaker> | ? | ? | Device name (string) is the acceptable value. No default value. If empty, MTR will use console speaker provided it's a supported speaker |
| <UltrasoundSpeakerVolume> | ? | ? | Value can be from 0 to 100, default value is 0 |


Pro Management Portal

Teams Rooms App Settings

## Bluetooth

Bluetooth is a short range wireless technology that compatible devices can communicate over. This signal can penetrate through walls. The signal is not paused when Microsoft Teams Room is in a meeting. Rooms appearing in the list of discovered rooms via Bluetooth are sorted by signal strength in descending order.

Supported devices

## Ultrasound

Proximity Join via ultrasound works by emitting an ultrasonic (19.5 kHz - 21.5 kHz) signal not usually audible to humans. It is more secure and accurate than Bluetooth because at reasonable volume will not penetrate through walls. The signal is paused when the Microsoft Teams Room is either in a meeting or HDMI ingest is active. 
> [!CAUTION]
> Some younger people and animals with sensitive hearing may be able to hear it. In our testing, this sound hasn't been distressing, but take note if young people or animals are in your meeting room environment. We recommend that younger people and animals are not present in the meeting room environments. If the beacon can be heard outside of the space for which it is intended to represent, speak to your admin. While Microsoft works with partners to ensure volume levels are adequately capped, your admin may have overridden the volume for ultrasound emission on a console or audio peripheral.

Supported devices:

- Microsoft Teams Rooms on Windows with a dedicated ultrasonic speaker

- Desktop - Teams on Windows

- Desktop - Teams on MacOS

## FAQ

Q: Is Proximity Join secure?

Yes. We're aware that meetings can have confidential data, and that bad actors may attempt to join meetings they aren't physically present for. The proximity beaconing technology was built with security in mind, and contains various safeguards to mitigate risks.

Q: Why did the Microsoft Teams Rooms not automatically accept the call/why did it ring?

1. In some cases, your admin may have turned off auto-accept for security reasons. Contact hour administrator.
1. In other cases, if the beacon is missing certain required security data due to distance, signal strength, or data loss, the Microsoft Teams Rooms may require a manual accept to ensure your meeting stays secure.

Q: Why is my video not showing up on the room display?

To increase comfort and reduce distraction, the Microsoft Teams Rooms will hide your personal camera display in the grid after a proximity join.

Q: Why is the Microsoft Teams Rooms that is in the room with me not at the top of the list?

1. Bluetooth signals penetrate walls; hence, it may be the case that a Microsoft Teams Rooms in a room adjacent to you or above/below you is actually physically closer to your device than the Microsoft Teams Rooms in your meeting room. This scenario is especially likely in the following circumstances:
   1. If your room is large and the Microsoft Teams Rooms is on the other side of it.
   1. In floor arrangements where meeting rooms are built back to back.
   1. In setups where the MTR is physically located outside the room (in a server room or equipment closet).
1. Bluetooth signals are also subject to wireless interference. Something may be interfering with the wireless signal of the Microsoft Teams Rooms in your room, causing it’s signal to be weaker than expected.

Q: Does Proximity Join work across tenants?

Yes, Proximity Join works across tenants, though this provision is currently bugged. A workaround is required to get this provision to work. To allow your personal device to resolve the identity of a Microsoft Teams Rooms external to your O365 tenant, you must first search for the name or email address of the Microsoft Teams Rooms device in Teams and send it a chat message. Microsoft is working on addressing this issue; so, a workaround will no longer be required.

Q: What is TeamsCast?

TeamsCast is a feature that uses Proximity Join to nudge a Microsoft Teams Rooms into a meeting, immediately followed by an automatic content share. Most issues with TeamsCast fall under the umbrella of Proximity Join, and the guidance in this article can be cross-applied.

___

# Proximity Join

Proximity Join is a feature that enables you to nudge your meeting room into a Microsoft Teams Rooms so that your meeting room can sync with Microsoft Teams Rooms. Your personal device, for example, your desktop or mobile phone, detects Microsoft Teams Rooms through a wireless signal.

The Proximity Join feature provides you with the following advantages:

1. You can easily access a meeting room that has Microsoft Teams Rooms in it. That is, the process of making your meeting room equipped what Microsoft Teams Rooms offers is easy.
    1. You don't have to touch any console or enter the ID of your meeting room when you're nudging it into Microsoft Teams Rooms.
1. You enter into such a meeting room (that has Microsoft Teams Rooms in it) in which your personal webcam feed is hidden from the room display.

## How does Proximity Join work?

When the Proximity Join feature is enabled, MTRs emit beacons for nearby devices to find. This beacon contains the identity of the MTR so your personal device can “nudge” it into a meeting, and some security and configuration data.

Once your personal device receives the beacon, it resolves the identity of the MTR in your enterprise database and “calls” it, asking the MTR to join the meeting you’ve requested it to.

Beacons are of two types:

1. [Ultrasonic sound (Ultrasound)](#ultrasonic-sound-ultrasound)
1. [Bluetooth](#bluetooth)

## Ultrasonic sound (Ultrasound)

The "Ultrasound" is one of the types of the beacon that's emitted for personal devices to detect and to resolve the MTR into which you nudge your meeting room.

> [!NOTE]
> This type of beacon isn't supported in mobile phones.

The Ultrasound beacon works in the following way:

1. It emits an ultrasonic sound on a cyclical basis. The beacon information is contained within the sound wave.
1. It uses a frequency range of 19.5 kHz to 21.5 kHz.
1. It isn't audible to humans.

   > [!CAUTION]
   > Some younger people and animals with sensitive hearing may be able to hear it. In our testing, this sound hasn't been distressing, but take note if young people or animals are in your meeting room environment. We recommend that younger people and animals are not present in the meeting room environments.

1. It's more secure and accurate because at reasonable amplitudes, it doesn't go through walls. Because of this advantage, rooms discovered via ultrasound are always placed at the top of the list.
1. This beacon doesn't emit during a meeting.

### How to use Ultrasound beacon to nudge your meeting room into an MTR?

> [!NOTE]
> You can detect an "ultrasound" beacon only if you use desktop, because the "ultrasound" beacon isn't supported in mobile phones.

Using the Proximity Join feature, perform the following steps from the TEAMS app on your desktop to detect "ultrasound" or "bluetooth" beacon to nudge your meeting room into Microsoft Teams Rooms:

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

## Bluetooth

Bluetooth is the other type of beacon that's emitted for personal devices to detect and to discover the MTR into  which you nudge your meeting room.

The Bluetooth beacon has the following characteristics:

1. It emits a continuous Bluetooth signal that personal devices can detect.
1. This beacon does emit during a meeting.
1. The Microsoft Teams Rooms it discovers are sorted in order of descending signal strength.

#### Limitation

As Bluetooth signals typically go through walls, may be less accurate and less secure.

### How to use Bluetooth beacon to nudge your meeting room into an MTR?

Using the Proximity Join feature, perform the following steps from the TEAMS app on your mobile phone to detect "bluetooth" beacon to nudge your meeting room into Microsoft Teams Rooms:

1. Ensure Bluetooth is on (ultrasound isn't supported on mobile).
1. Choose a meeting from your calendar and select **Join**, or select the **+** button and select **Meet Now**.
1. In the pre-join screen, select **More Join Options**.
1. Select **Join a meeting room**.
1. Wait for a nearby meeting room to be found, select it, and select **Join**.

#### Q: Is Proximity Join secure?

Yes. We're aware that meetings can have confidential data, and that bad actors may attempt to join meetings they aren't physically present for. The proximity beaconing technology was built with security in mind, and contains various safeguards to mitigate risks.

#### Q: Why did the Microsoft Teams Rooms not automatically accept the call/why did it ring?

1. In some cases, your admin may have turned off auto-accept for security reasons. Contact hour administrator.
1. In other cases, if the beacon is missing certain required security data due to distance, signal strength, or data loss, the Microsoft Teams Rooms may require a manual accept to ensure your meeting stays secure.

#### Q: Why is my video not showing up on the room display?

To increase comfort and reduce distraction, the Microsoft Teams Rooms will hide your personal camera display in the grid after a proximity join.

#### Q: Why is the Microsoft Teams Rooms that is in the room with me not at the top of the list?

1. Bluetooth signals penetrate walls; hence, it may be the case that a Microsoft Teams Rooms in a room adjacent to you or above/below you is actually physically closer to your device than the Microsoft Teams Rooms in your meeting room. This scenario is especially likely in the following circumstances:
    1. If your room is large and the Microsoft Teams Rooms is on the other side of it.
    1. In floor arrangements where meeting rooms are built back to back.
    1. In setups where the MTR is physically located outside the room (in a server room or equipment closet).
1. Bluetooth signals are also subject to wireless interference. Something may be interfering with the wireless signal of the Microsoft Teams Rooms in your room, causing it’s signal to be weaker than expected.

#### Q: Does Proximity Join work across tenants?

Yes, Proximity Join works across tenants, though this provision is currently bugged. A workaround is required to get this provision to work. To allow your personal device to resolve the identity of a Microsoft Teams Rooms external to your O365 tenant, you must first search for the name or email address of the Microsoft Teams Rooms device in Teams and send it a chat message. Microsoft is working on addressing this issue; so, a workaround will no longer be required.

#### Q: What is TeamsCast?

TeamsCast is a feature that uses Proximity Join to nudge a Microsoft Teams Rooms into a meeting, immediately followed by an automatic content share. Most issues with TeamsCast fall under the umbrella of Proximity Join, and the guidance in this article can be cross-applied.

#### Troubleshooting

##### I don’t see any rooms nearby

If you don't see any Microsoft Teams Rooms nearby, perform the following steps:
1. Ensure that your Bluetooth is on and that your microphone is unmuted.
1. Ensure that your admin has not disabled proximity join in your tenant.

##### I/my dog/my child can hear the ultrasound beacon

Some young people and animals with sensitive hearing may be able to hear the beacon. This beacon is not harmful to health, but Microsoft does not expect these groups to commonly be found in shared workplaces. Microsoft recommends that you remove sensitive individuals or animals from the room. If the beacon can be heard outside of the space which it's intended to represent, contact your admin. While Microsoft works with partners to ensure that volume levels are adequately capped for Microsoft Teams Rooms consoles, your admin may have overridden the volume for ultrasound emission on a console or audio peripheral.

## Administrator

An administrator must do the following tasks to activate the Proximity Join feature:

1. **Make Microsoft Teams Room device bluetooth compatible**: You must ensure that the Microsoft Teams Rooms is compatible with the "bluetooth" beacon such that users using a mobile phone are able to detect the beacon that contains the identity of the Microsoft Teams Rooms.
1. **Make Microsoft Teams Room device ultrasound compatible**: Make the Microsoft Teams Rooms compatible with "ultrasound beacon" such that users using a desktop are able to detect the beacon that contains the identity of the Microsoft Teams Rooms.
    1. **Use the speaker and volume override settings**: You must use the speaker and volume override settings for the following reasons:
        1. If there is no compatible Microsoft Teams Rooms console on which defined volume levels of ultrasound can be emitted.
        1. If volumes levels different from the defined levels are required to emit ultrasound beacon on a compatible Microsoft Teams Rooms console.
3. **Enable/disable Proximity Join**:
    1. **For the Bluetooth beacon**: To enable/disable "Proximity Join" for the Bluetooth beacon, run the following command:
       `BluetoothAdvertisementEnabled`, where the default value is **True**.
    1. **For the Ultrasound beacon**: To enable/disable "Proximity Join" for the Ultrasound beacon, run the following command:
       `UltrasoundAdvertisementEnabled`, where the default value is **True**.
4. **-	Enable/Disable Auto-Accept**:
    1. **For the Bluetooth beacon**: To enable/disable "Auto-accept" for the Bluetooth beacon, run the following command:
       `AutoAcceptProximateMeetingInvitations`, where the default value is **False**.
    1. **For the Ultrasound beacon**: To enable/disable Proximity Join for the Ultrasound beacon, run the following command:
       `UltrasoundAutoAcceptProximateMeetingInvitations`, where the default value is **True**.
5. **Use the Ultrasound Speaker & Volume Override (not yet present)**:
    1. `UltrasoundSpeaker`
       - Device name (string) is the acceptable value.
       - No default value. If empty, MTR will use console speaker provided.
    1. `UltrasoundSpeakerVolume`
       - Value can be from 0 to 100; default value is 0.