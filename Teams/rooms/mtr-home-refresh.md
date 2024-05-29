---
title: Microsoft Teams Rooms home screen design and features
ms.author: tonysmit
author: mstonysmith
manager: pamgreen
ms.reviewer: henrikalim
ms.date: 05/28/2024
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

Microsoft Teams Rooms include modern home screen design that includes a calendar on the console and front-of-room displays, quick access to more commonly used actions on the console, built-in background options, and a consistent look and feel to other Teams devices.

## Teams Room Calendar

Teams Rooms devices communicate with Exchange aligned to the same method Teams desktop, web, and mobile clients utilize.  To ensure that meetings appear correctly on your Teams Rooms clients, see [How Exchange and Microsoft Teams interact](../Exchange-Teams-interact.md).

> [!WARNING]
> Only on-premises Exchange servers with Hybrid Configuration and AutoDiscover v2 published externally are supported on Teams Rooms on Windows. which is consistent with how other Teams clients connect with Exchange. If you're using Teams Rooms with an on-premises Exchange server, we recommend that you review how on-premises mailboxes work with Teams: [Microsoft Teams and on-premises mailboxes](https://techcommunity.microsoft.com/t5/microsoft-teams-community-blog/microsoft-teams-and-on-premises-mailboxes-part-1-how-do-teams/ba-p/2229851)
### Calendar Entry Join Buttons

Teams Rooms devices read Exchange calendar entries and will automatically generate "Join" buttons for end users to to one touch join into Teams meetings. This functionality can also be enabled for third-party meeting platforms following this guidance: [Join third-party meetings](/microsoftteams/rooms/third-party-join)

If you wish to restrict the one touch join experience on Teams meetings, Teams Rooms offer controls to require users to enter the Teams Meeting ID and Passcode after a user selects the "Join" button adding further security to your Teams Rooms, this can be achieved by applying this configuration:

#### Teams Rooms on Windows

Require the Meeting ID and Passcode for all Teams Meetings


```xml
<RequirePasscodeForAllTeamsMeetings>true</RequirePasscodeForAllTeamsMeetings> 
```

Require the Meeting ID and Passcode for Teams Meetings marked as Private in Outlook


```xml
<RquirePasscodeForAllPrivateTeamsMeetings>true</RequirePasscodeForAllPrivateTeamsMeetings> 
```

#### Teams Rooms on Android

On the device, open Teams Admin Settings > Meetings and toggle "Require passcode for all meetings" to On to require users to enter the Teams Meeting passcode on all Teams Meeting "Join" button presses.

### Calendar entry details

Teams Rooms devices by default show the subject and organizer name for each meeting on the room calendar except those calendar invites which have been marked as private. The meeting body is not accessible on a Teams Room device to ensure data privacy and security.

#### Exchange Calendar Settings

Based on your organizations desired configuration you may want to review Exchange calendar processing settings for your room mailboxes: [Set-CalendarProcessing](/powershell/module/exchange/set-calendarprocessing) We've outlined important elements to check as well:

- RemovePrivateProperty - If this is set to "true" devices will show the meeting subject and organizer name regardless of if meeting is set to private

- DeleteComments - If this is set to "true" devices may not be able to show join buttons for third-party meetings

- DeleteSubject - If this is set to "true" the meeting subject will not be visible on Teams Rooms devices

#### Teams Rooms on Windows

On a Teams Rooms on Windows device, open Settings > Meetings and toggle "Show meeting names" to Off to hide meeting names. This can also be modified using an XML configuration file with a value of 1 to hide the meeting names:


```xml
<HideMeetingName>1</HideMeetingName>
```

#### Teams Rooms on Android

On the device, open Teams Admin Settings > Meetings and toggle "Show meeting names" to Off to hide meeting names on the Teams Room device.

### Hide the calendar from the front-of-room display

Teams Rooms on Windows allows you to hide the calendar on your front-of-room display, add the following to your XML configuration file to do so:


```xml
<RemoveFoRCalendar>true</RemoveFoRCalendar> 
```

## Console Buttons

### Meet Now

All Teams Rooms devices include meet now functionality which automatically launches the Teams Rooms device into an ad-hoc Teams meeting.  Lean more about Meet Now here: [Start an instant meeting in Microsoft Teams](https://support.microsoft.com/office/start-an-instant-meeting-in-microsoft-teams-ff95e53f-8231-4739-87fa-00b9723f4ef5)

### Call

#### Calling a Teams User

All Teams Rooms devices include "call" functionality, which allows end users to manually call an individual participant in the organization or a federated Teams users.

#### PSTN

Teams Rooms support PSTN calling just like a Teams user. The Teams Rooms Pro licensing includes the Phone System functionality, but you'll need to add a calling plan, Operator Connect, or direct routing configuration to your Teams Rooms account for the PSTN functionality to work. You can learn more here: [Teams PSTN connectivity](/microsoftteams/pstn-connectivity)

#### SIP/H.323 Calling

Teams Rooms on Windows devices support making a SIP/H.323 call, guidance can be found here: [Meetings with SIP and H.323 devices](/microsoftteams/rooms/meetings-with-sip-h323-devices)

### Share

Teams Rooms devices automatically share the audio & video output of a connected HDMI ingest device to the front-of-room screens outside of a meeting as well as automatically share as content into a call during a meeting.

#### Teams Rooms on Windows

On a Teams Rooms on Windows device you can disable automatic sharing into a Teams Meeting but you cannot disable automatic sharing onto the front of room display. To disable automatic sharing into a meeting, open Settings > Meetings and toggle "Automatic screen sharing" to Off. This can also be modified using an XML configuration file with a value of 0 to disable automatic sharing.

Likewise, Teams Rooms on Windows supports XML configuration to disable HDMI ingest audio and an option to disable sending the HDMI ingest to multiple front-of-room screens if multiple screens are connected.


```xml
<AutoScreenShare>0</AutoScreenShare>
<DuplicateIngestDefault>false</DuplicateIngestDefault>
<DisableTeamsAudioSharing>true</DisableTeamsAudioSharing>
```

#### Teams Rooms on Android

On the device, open Teams Admin Settings > Meetings and toggle "Include Audio" and/or "Automatically share to the room display" to Off as desired.

### Join with an ID

Teams Rooms offer an option for end user to be able to enter the Teams Meeting ID and Passcode to be able to join a meeting.  If third party meetings are enabled on the device, they may also have the ability to join by ID into a third party meeting platform.

### Whiteboard

aaa

### Room Controls

Teams Rooms on Windows devices offer an extensibility option referred to as "Room Controls". Consult your Teams Rooms manufacturer or your AV partner if you wish to add extensibility controls for: lights/blinds, cameras, or custom video routing. These room controls are directly supported by your Teams Room manufacturer or AV partner.

### Accessibility

Teams Rooms on Windows devices offer an accessibility button which allows end user to enable/disable a high contrast screen mode making the Teams Rooms user interface more accessible.

### Language

Teams Rooms on Windows devices by default allow end users to change the language of the Microsoft Teams Rooms on the Microsoft Windows app. The language choices offered are the same as those that are offered in the Microsoft Teams desktop app. Once the language has been changed on the device, the device will continue using that language until a restart occurs (this restart could be triggered by a user or during the device maintenance reboot).

### ?

#### Report a Problem

Repprt a Problem is.....

#### Give Feedback

Give Feedback is enabled on all Teams Rooms devices by default, Users can fill out Give feedback to send any comments or suggestions about Teams Rooms to Microsoft. We will use this feedback to improve the Teams experience. Data sent through Give feedback is considered as Support Data under your Microsoft 365 or Office 365 agreement, including information that would otherwise be considered Customer Data or Personal Data. This functionality is controllable by the Teams feedback policies outlined here: [Manage Feedback Policies](/microsoftteams/manage-feedback-policies-in-teams)

## QR Codes for Meeting Join

Teams Rooms devices offer QR codes on the console and front-of-room screens which allow users an easy path to join a Microsoft Teams Meeting, see[ Join meeting with QR codes](/microsoftteams/rooms/teams-rooms-qr-codes) for more information.

## Custom backgrounds

Teams Rooms on Windows devices support custom backgrounds, see [Set up and manage Teams Rooms on Windows custom backgrounds](custom-backgrounds.md).

## Updating Teams Rooms on Windows device configuration

To apply the configuration changes included in this article to your Teams Rooms for Windows devices, you need to use the Teams Rooms XML configuration file. The XML configuration file lets you remotely deploy configuration changes to one or more Teams Rooms devices in your organization. For more information, see [Manage a Microsoft Teams Rooms console settings remotely with an XML configuration file](xml-config-file.md).

### 

