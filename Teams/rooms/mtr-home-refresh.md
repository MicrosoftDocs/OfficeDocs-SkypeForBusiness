---
title: Teams Rooms home screen and admin controls
ms.author: tonysmit
author: mstonysmith
manager: pamgreen
ms.reviewer: henrikalim
ms.date: 06/26/2024
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
description: Learn about the Microsoft Teams Rooms home screen design and features.
---

# Teams Rooms (Windows and Android) home screen and admin controls

Microsoft Teams Rooms includes a modern home screen design that provides a seamless, intuitive, and consistent look and feel with other Teams devices. The touch console (or touch board) offers a clean and straightforward user experience, prominently displaying a room calendar, an easy access to join upcoming scheduled meetings with a single touch, and commonly used actions like starting a meeting, making a call, and sharing content. Additionally, the home screen features customizable background options, allowing you to tailor the interface to your organization's needs. This user-centric design ensures efficient collaboration and communication, enhancing productivity in a modern workplace environment.

This article explains the various features available on a Teams Rooms touch console (or touch board), including the default experience, the ways you can configure a feature (if applicable), and any differences between Teams Rooms on Windows and Teams Rooms on Android. For a more comprehensive overview of the Teams Rooms user features beyond the home screen experience, see [Get started with Teams Rooms](https://support.microsoft.com/office/get-started-with-microsoft-teams-rooms-0e3b47c5-5bc0-4b96-af31-56ac7d4606f9).


## User actions

### Meet now

Room users can instantly start an ad-hoc Teams meeting using Meet now on any **Teams Rooms (Windows and Android)** device. To ensure that you are not blocking this functionality using policy, see [Manage who can start instant meetings](/microsoftteams/manage-who-can-schedule-meetings).

### Call

**Teams Rooms (Windows and Android)** devices include Call. By default, Teams Calling is available, allowing room users to make and receive peer to peer and group calls with other user(s) in the organization or with federated Teams user(s).

Additionally, **Teams Rooms (Windows and Android)** devices also support Public Switched Telephone Network (PSTN) calling as the Teams Rooms Pro license includes the M365 Phone System functionality. In addition to having the proper license, you need to add a Calling Plan, Operator Connect, or Direct Routing configuration to your Teams Rooms account for the PSTN functionality to work. Learn more at [Teams PSTN connectivity](/microsoftteams/pstn-connectivity).

Furthermore, with a Teams Rooms Pro license, **Teams Rooms on Windows** devices support SIP/H.323 calling. For more information, see [Meetings with SIP and H.323 devices](/microsoftteams/rooms/meetings-with-sip-h323-devices).

### Share

Room users can share content to any **Teams Rooms (Windows and Android)** device either wirelessly using Teams cast or by connecting their personal device to the room system using an HDMI or USB-C cable.

#### Teams cast

By default, Bluetooth beaconing is enabled on all **Teams Rooms (Windows and Android)** devices so room users can [cast content from desktop](https://support.microsoft.com/office/cast-content-from-your-desktop-to-a-microsoft-teams-room-6d62cdbb-3da2-4bb9-80bd-9cf1098beb3d) or [cast content from mobile](https://support.microsoft.com/office/cast-content-from-a-mobile-device-to-a-microsoft-teams-room-c4e5fb1b-6b94-4d48-88f2-6bcd8e7e339d) to the front-of-room display. To disable Bluetooth beaconing:

- On a **Teams Rooms on Windows** device, open **Settings** > **Device** > toggle **Bluetooth beaconing** to Off as desired. You can also make the configuration change using Teams Rooms Pro Management portal, Teams admin center, or XML setting:
```xml
<BluetoothAdvertisementEnabled>false</BluetoothAdvertisementEnabled>
```

- On a **Teams Rooms on Android** device, open **Teams Admin Settings** > **General** > toggle **Bluetooth beaconing** to Off as desired. You can also make the configuration change using the Teams Rooms on Android configuration profile in the Teams admin center.

#### HDMI input

By default, upon plugging in an HDMI device to the room system, all **Teams Rooms (Windows and Android)** devices automatically share the audio and video output of a connected HDMI ingest device. If dual screens are connected to your **Teams Rooms on Windows** device, by default, HDMI content is shared onto both front-of-room displays. On **Teams Rooms on Android** devices with a dual screen deployment, HDMI content is only shared onto the extended front-of-room display. 

> [!WARNING]
> We don't recommend having devices which always output a video signal connected to the HDMI ingest. This is known to cause challenges when trying to present content in a Teams meeting and leads to a misreport in usage data due to the system believing it is always in use.

On a **Teams Rooms on Windows** device, you can disable automatic sharing into a Teams meeting but this doesn't disable automatic sharing onto the front-of-room display. To disable automatic sharing into a meeting, open **Settings** > **Meetings** and toggle **Automatic screen sharing** to Off. You can also disable HDMI ingest audio and disable sending the HDMI content to both front-of-room displays by default. All of which you can make using XML setting:

```xml
<AutoScreenShare>0</AutoScreenShare>
<DuplicateIngestDefault>false</DuplicateIngestDefault>
<DisableTeamsAudioSharing>true</DisableTeamsAudioSharing>

```

On a **Teams Rooms on Android** device, you can disable HDMI ingest audio and automatic HDMI content sharing onto the front-of-room display (which also disables automatic sharing into a Teams meeting). To do so, open **Teams Admin Settings** > select **Meeting** and toggle **Include Audio** and/or **Automatically share to the room display** to Off as desired. Alternatively, you can adjust these settings through the Teams Rooms on Android configuration profile in the Teams admin center.

### Whiteboard

For in person brainstorming sessions, **Teams Rooms (Windows and Android)** devices offer a quick way to start an ad-hoc Microsoft Whiteboard session from the home screen. 

If the front-of-room display of your **Teams Rooms on Android** device is not touch-enabled, you can disable this feature: open **Teams Admin Settings** > **Meetings** and toggle **Allow room to initiate whiteboarding** to Off as desired. You can also update this setting using the Teams Rooms on Android configuration profile in the Teams admin center. 

> [!NOTE]
> All Teams Rooms on Android devices support starting Whiteboard from the home screen. However, for Teams Rooms on Windows, this feature is only supported on the touch board form factor.### Join with an ID

If room users would like to join a meeting that is not on the room calendar, **Teams Rooms (Windows and Android)** devices allow users to enter the meeting ID and passcode to join a meeting. Entering the meeting ID and passcode to join third-party meetings is also supported if third-party meetings are enabled on the device. To enable third-party meetings, see [Enable Teams Rooms devices to join third-party meetings](/microsoftteams/rooms/third-party-join).

### Room Controls

**Teams Rooms on Windows** devices offer an extensibility option referred to as Room controls, supported by Teams Rooms device manufacturers or Audio Visual (AV) partners. Consult your Teams Rooms device manufacturer or your AV partner if you wish to add extensibility controls for lights/blinds, cameras, or custom video routing.

### Accessibility

For accessibility, **Teams Rooms on Windows** devices allow room users to switch on/off a high contrast screen mode. Installation of an external keyboard is also supported if desired. Accessibility options on **Teams Rooms on Android** devices are controlled by the Teams Rooms device manufacturer. 

### Language

By default, **Teams Rooms on Windows** devices allow room users to change the language of the Teams Rooms app using the Language button in the home screen. The language choices offered are the same as the ones available on the Teams desktop app. Once the language has been changed on the device from the home screen, the device continues using that language until a restart occurs (can be triggered by a user or during the device maintenance reboot). To disable room users from temporarily changing the language of the Teams Rooms app, apply this XML setting: 

```xml
<RoomLanguageSwitchEnabled>false</RoomLanguageSwitchEnabled>. 
```

Language options on **Teams Rooms on Android** devices are controlled by the Teams Rooms device manufacturer. 

### Help

#### Report a problem

Under Help, Report a problem will show if your **Teams Rooms (Windows and Android)** device has a preview app or if your account is in a preview ring.

Outside of the preview experience, Report a problem can be enabled on **Teams Rooms on Windows** devices in two ways:
- By default, Report a problem is enabled on any **Teams Rooms on Windows** device that has an account with a Teams Rooms Pro license. When a room user reports an issue, a feedback event is created in the Teams Rooms Pro Management portal. This event gives you the data to address the feedback or open a support case with logs from the room. Sending logs and feedback events to the Teams Rooms Pro Management portal can be disabled using XML setting: 

```xml
<SendFeedbackToPMP>true</SendFeedbackToPMP>
```
- Report a problem can also be enabled on **Teams Rooms on Windows** devices in the production environment by adding an email address in the device settings, in which case reported issues are sent to the configured email address. To enable sending logs and feedback to the admin-configured email address, go to **Settings** > **Device** > add email address or use the following XML setting:

```xml
<SendLogs>
    <EmailAddressForLogsAndFeedback>username@microsoft.com</EmailAddressForLogsAndFeedback>
    <SendLogsAndFeedback>true</SendLogsAndFeedback>
</SendLogs>
```

Report a problem outside of the preview environment is not yet available on **Teams Rooms on Android** devices.

#### Give feedback

Give feedback is enabled on all **Teams Rooms (Windows and Android)** devices by default. Room users can fill out Give feedback to send any comments or suggestions about Teams Rooms to Microsoft. We'll use this feedback to improve the Teams experience. Data sent through Give feedback is considered as Support Data under your Microsoft 365 or Office 365 agreement, including information that would otherwise be considered Customer Data or Personal Data. You can control this functionality using the Teams feedback policies outlined in [Manage feedback policies in Microsoft Teams](/microsoftteams/manage-feedback-policies-in-teams).

## Calendar

The room calendar on **Teams Rooms (Windows and Android)** devices shows the room availability and scheduled meetings in the room which includes third-party meetings (when enabled). By default, room users can join meetings in one touch and view meeting details including the meeting name, organizer, time, and platform. To enable third-party meetings, see [Enable Teams Rooms devices to join third-party meetings](/microsoftteams/rooms/third-party-join). 

For privacy purposes, meeting names can be hidden from **Teams Rooms (Windows and Android)** calendar and replaced with the organizer name if desired:
- On a **Teams Rooms on Windows** device, open **Settings** > **Meetings** and toggle **Show meeting names** to Off to hide meeting names. This device setting can also be modified using the Teams admin center or XML setting:

```xml
<HideMeetingName>1</HideMeetingName>
```
- On a **Teams Rooms on Android** device, open **Teams Admin Settings** > **Meetings** and toggle **Show meeting names** to Off to hide meeting names on the Teams Room device. 

For increased security in the meeting join experience on a shared device, **Teams Rooms (Windows and Android)** devices support requiring room users to enter the meeting credentials (ID and passcode) before joining scheduled Teams meetings. This feature requires the account on the device to have a Teams Rooms Pro license. To enable this functionality: 

- On **Teams Rooms on Windows** devices, you can either require the meeting ID and passcode for all scheduled Teams meetings or only for meetings that are marked as private with the following XML settings:

```xml
<RequirePasscodeForAllTeamsMeetings>true</RequirePasscodeForAllTeamsMeetings> 
<RquirePasscodeForAllPrivateTeamsMeetings>true</RequirePasscodeForAllPrivateTeamsMeetings>
```

- On **Teams Rooms on Android** devices, open **Teams Admin Settings** > **Meetings** and toggle **Require passcode for all meetings** to On to require room users to enter the meeting credentials to join all scheduled Teams meetings.

The way **Teams Rooms (Windows and Android)** devices communicate with Exchange is aligned with the same method Teams desktop, web, and mobile clients utilize. To ensure that meetings appear correctly on your Teams Rooms clients, see [How Exchange and Microsoft Teams interact](../Exchange-Teams-interact.md). You may also want to review your Exchange calendar processing settings for additional customizations on the room calendar, see [Configure mailbox properties](/microsoftteams/rooms/create-resource-account?tabs=m365-admin-center%2Cgraph-powershell-password#configure-mailbox-properties).

> [!WARNING]
> Only on-premises Exchange servers with Hybrid Configuration and AutoDiscover v2 published externally are supported which is consistent with how other Teams clients connect with Exchange. If you're using Teams Rooms with an on-premises Exchange server, we recommend that you review how on-premises mailboxes work with Teams: [Microsoft Teams and on-premises mailboxes](https://techcommunity.microsoft.com/t5/microsoft-teams-community-blog/microsoft-teams-and-on-premises-mailboxes-part-1-how-do-teams/ba-p/2229851)


## QR code

**Teams Rooms (Windows and Android)** devices display a QR code on the console and front-of-room display by default to allow users to easily bring their meetings to the room. For more information, see[ Join meeting with QR codes](/microsoftteams/rooms/teams-rooms-qr-codes).

## Background

**Teams Rooms (Windows and Android)** devices include several out of the box backgrounds that can be selected as desired. 

If your Teams Rooms device has an account with a Teams Rooms Pro license, you can configure custom backgrounds for your device, see [Teams Rooms on Windows custom backgrounds](/microsoftteams/rooms/custom-backgrounds) or [Teams Rooms on Android custom backgrounds](/microsoftteams/rooms/custom-backgrounds-android)

## Release Ring Indicator

**Teams Rooms (Windows and Android)** indicate with a pill icon below the time if they are in an earlier release ring for Microsoft Teams (no pill is present on a device not in preview). This is indiciator is intentional to ensure users know the device is running an earlier release of Microsoft Teams. Teams Rooms can be put into a preview state in any of the following ways, if you wish to move the devices out of the preview ring, review the options and undo those changes:
- [Teams Public Preview](/microsoftteams/public-preview-doc-updates)
- [M365 Targeted Release](/microsoft-365/admin/manage/release-options-in-office-365)
- Participating in a private preview in partnership with Microsoft. Please contact your Microsoft account team for more information.
- On a **Teams Rooms on Windows** device an XML setting can be used to enable public preview:

```xml
<EnablePublicPreview>true</EnablePublicPreview>
```

