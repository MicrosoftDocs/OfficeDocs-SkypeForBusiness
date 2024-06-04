---
title: Microsoft Teams Rooms home screen design and features
ms.author: tonysmit
author: mstonysmith
manager: pamgreen
ms.reviewer: henrikalim
ms.date: 06/04/2024
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

# Microsoft Teams Rooms home screen design and features

Microsoft Teams Rooms includes a modern home screen design that with a calendar, quick access to commonly used actions on the console, built-in background options, and a consistent look and feel to other Teams devices.

## User Features

This section explains the various features available on a Teams Rooms console (or all-in-one screen).

### Meet Now

All Teams Rooms devices include Meet Now functionality that automatically launches the Teams Rooms device into an ad-hoc Teams meeting. Lean more about Meet Now here: [Start an instant meeting in Microsoft Teams](https://support.microsoft.com/office/start-an-instant-meeting-in-microsoft-teams-ff95e53f-8231-4739-87fa-00b9723f4ef5)

### Call

#### Calling a Teams User

All Teams Rooms devices include Call functionality, which allows end users to call an individual participant in the organization or a federated Teams user.

#### Public Switched Telephone Network (PSTN)

Teams Rooms support PSTN calling just like a Teams user and Teams Rooms Pro licensing includes the Phone System functionality. You need to add a Calling Plan, Operator Connect, or Direct Routing configuration to your Teams Rooms account for the PSTN functionality to work. You can learn more here: [Teams PSTN connectivity](/microsoftteams/pstn-connectivity)

#### SIP/H.323 Calling

Teams Rooms on Windows devices support making a SIP/H.323 call. Guidance can be found here: [Meetings with SIP and H.323 devices](/microsoftteams/rooms/meetings-with-sip-h323-devices)

### Share

Teams Rooms devices automatically share the audio & video output of a connected HDMI ingest device.

> [!WARNING]
> Microsoft does not recommend having devices which always output a video signal connected to the HDMI ingest. This can cause challenges when trying to present content in a Teams Meeting as well as misreport in usage data as the system believes it is always in use.

On a Teams Rooms on Windows device, you can disable automatic sharing into a Teams Meeting but you can't disable automatic sharing onto the front of room display. To disable automatic sharing into a meeting, open Settings > Meetings and toggle "Automatic screen sharing" to Off or via XML outlined below.

Likewise, Teams Rooms on Windows support XML configuration to disable HDMI ingest audio and an option to disable sending the HDMI ingest to multiple front-of-room screens if multiple screens are connected.


```xml
<AutoScreenShare>0</AutoScreenShare>
<DuplicateIngestDefault>false</DuplicateIngestDefault>
<DisableTeamsAudioSharing>true</DisableTeamsAudioSharing>
```

On a Teams Rooms on Android device, open Teams Admin Settings > Meetings and toggle "Include Audio" and/or "Automatically share to the room display" to Off as desired.

### Join with an ID

Teams Rooms offer an option for end user to be able to enter the Teams Meeting ID and Passcode to be able to join a meeting. If third party meetings are enabled on the device, you may also have the ability to join by ID into a third-party meeting platform.

### Whiteboard

Teams Rooms devices offer a way to start an ad-hoc Microsoft whiteboard for in person interactive meetings. This functionality is only available on all-in-one Teams Rooms on Windows devices. All Teams Rooms on Android devices support starting a Whiteboard from the home screen. To change this setting, open Teams Admin Settings > Meetings and toggle "Allow room to initiate whiteboarding" as desired.

### Room Controls

Teams Rooms on Windows devices offer an extensibility option referred to as Room Controls. Consult your Teams Rooms manufacturer or your Audio Visual (AV) partner if you wish to add extensibility controls for: lights/blinds, cameras, or custom video routing. These controls are supported by your Teams Rooms manufacturer or AV partner.

### Accessibility

Teams Rooms on Windows devices offer an accessibility button which, allows end user to enable/disable a high contrast screen mode making the Teams Rooms user interface more accessible.

### Language

Teams Rooms on Windows devices by default allow end users to change the language of the Microsoft Teams Rooms on the Microsoft Windows app. The language choices offered are those that are offered in the Microsoft Teams desktop app. Once the language has been changed on the device, the device continues using that language until a restart occurs (this restart can be triggered by a user or during the device maintenance reboot).

### The '?' button

#### Report a Problem

Report a Problem will always show if your Teams Room device has a preview build or if your Teams Rooms account is in a preview ring.

Outside of preview, report a problem is enabled by default on Teams Rooms on Windows devices so that when a user in a Microsoft Teams Room reports an issue, a feedback event is created in the Teams Rooms Pro Management portal. This event gives device managers the data they need to address the feedback or open a support case with logs from the room. This Pro Portal feature can be disabled via XML. Likewise, Report a Problem can also be enabled by adding an email address in Settings > Device or via XML, in this case when an issue is reported an email is sent to the configured email address with the feedback.


```xml
<SendFeedbackToPMP>true</SendFeedbackToPMP>
<SendLogs>
    <EmailAddressForLogsAndFeedback>username@microsoft.com</EmailAddressForLogsAndFeedback>
    <SendLogsAndFeedback>true</SendLogsAndFeedback>
</SendLogs>
```

#### Give Feedback

Give Feedback is enabled on all Teams Rooms devices by default. Users can fill out Give feedback to send any comments or suggestions about Teams Rooms to Microsoft. We'll use this feedback to improve the Teams experience. Data sent through Give feedback is considered as Support Data under your Microsoft 365 or Office 365 agreement, including information that would otherwise be considered Customer Data or Personal Data. This functionality is controllable by the Teams feedback policies outlined here: [Manage Feedback Policies](/microsoftteams/manage-feedback-policies-in-teams)

## Teams Rooms Calendar

Teams Rooms devices communicate with Exchange aligned to the same method Teams desktop, web, and mobile clients utilize. To ensure that meetings appear correctly on your Teams Rooms clients, see [How Exchange and Microsoft Teams interact](../Exchange-Teams-interact.md).

> [!WARNING]
> Only on-premises Exchange servers with Hybrid Configuration and AutoDiscover v2 published externally are supported which is consistent with how other Teams clients connect with Exchange. If you're using Teams Rooms with an on-premises Exchange server, we recommend that you review how on-premises mailboxes work with Teams: [Microsoft Teams and on-premises mailboxes](https://techcommunity.microsoft.com/t5/microsoft-teams-community-blog/microsoft-teams-and-on-premises-mailboxes-part-1-how-do-teams/ba-p/2229851)
### Calendar Join Buttons

Teams Rooms devices read Exchange calendar entries and automatically generate "Join" buttons for end users to one touch join into Teams meetings. The "Join" details for the Teams Meeting come from hidden meeting invite properties and aren't read directly from the meeting body. This one touch join functionality can also be extended for third-party meeting platforms following this guidance: [Join third-party meetings](/microsoftteams/rooms/third-party-join)

If you wish to restrict the one touch join experience on Teams meetings, Teams Rooms offer controls to require users to enter the Teams Meeting ID and Passcode after a user selects the "Join" button. This adds further security to your Teams Rooms and can be achieved by applying this configuration:


For Teams Rooms on Windows devices, you can either require the Meeting ID and Passcode for all Teams Meetings or require the Meeting ID and Passcode for Teams Meetings marked as private

```xml
<RequirePasscodeForAllTeamsMeetings>true</RequirePasscodeForAllTeamsMeetings> 
<RquirePasscodeForAllPrivateTeamsMeetings>true</RequirePasscodeForAllPrivateTeamsMeetings>
```

On the Teams Rooms on Android devices, open Teams Admin Settings > Meetings and toggle "Require passcode for all meetings" to On to require users to enter the Teams Meeting passcode on all Teams Meeting "Join" button presses.

### Calendar entry details

Teams Rooms devices show the meeting subject and organizer name for event on the rooms calendar except those calendar invites that are marked as private. The meeting body isn't accessible on a Teams Room device to ensure data privacy and security.

#### Exchange Calendar Settings

Based on your organizations desired configuration, you may want to review Exchange calendar processing settings for your room mailboxes: [Set-CalendarProcessing](/powershell/module/exchange/set-calendarprocessing) The important paramaters to check are:

- RemovePrivateProperty - If set to "true" devices will show the meeting subject and organizer name regardless of if meeting is set to private

- DeleteComments - If set to "true" devices may not be able to show join buttons for third-party meetings

- DeleteSubject - If set to "true" the meeting subject isn't visible on Teams Rooms devices

On a Teams Rooms on Windows device, open Settings > Meetings and toggle "Show meeting names" to Off to hide meeting names. This can also be modified using an XML configuration file with a value of 1 to hide the meeting names:

```xml
<HideMeetingName>1</HideMeetingName>
```

On a Teams Rooms on Android device, open Teams Admin Settings > Meetings and toggle "Show meeting names" to Off to hide meeting names on the Teams Room device.

### Hide the calendar from the front-of-room display

Teams Rooms on Windows allow you to hide the calendar on your front-of-room display and only see the calendar on the console. Add the following to your XML configuration file to do so:

```xml
<RemoveFoRCalendar>true</RemoveFoRCalendar> 
```

## QR Codes for Meeting Join

Teams Rooms devices offer QR codes on the console and front-of-room screens to allow users an easy path to join a Microsoft Teams Meeting, for more information, see: [ Join meeting with QR codes](/microsoftteams/rooms/teams-rooms-qr-codes).

## Backgrounds

Teams Rooms devices include several out of the box backgrounds that can be selected as desired.

Teams Rooms on Windows devices also support custom backgrounds, see [Set up and manage Teams Rooms on Windows custom backgrounds](custom-backgrounds.md).

## Teams Rooms on Windows XML Configuration

To apply the configuration changes included in this article to your Teams Rooms for Windows devices, you need to use the Teams Rooms XML configuration file. The XML configuration file lets you remotely deploy configuration changes to one or more Teams Rooms devices in your organization. For more information, see [Manage a Microsoft Teams Rooms console settings remotely with an XML configuration file](xml-config-file.md).

