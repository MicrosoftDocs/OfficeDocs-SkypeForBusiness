---
title: "Audio Conferencing common questions"
ms.author: heidip
author: MicrosoftHeidi
manager: serdars
ms.reviewer: oscarr
ms.topic: conceptual
ms.assetid: a90ea695-aabf-4f10-ae92-24b3f6b27c56
ms.tgt.pltfrm: cloud
audience: admin
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - M365-collaboration
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom: 
  - Audio Conferencing
description: "The following are some of the top questions we get from our customers who want to use Audio Conferencing."
---

# Audio Conferencing common questions

The following are some of the top questions we get from our customers who want to use Audio Conferencing.
  
## What are the benefits of Audio Conferencing?

Calling in to meetings is beneficial when people are on the road, for example, and can't attend a meeting using the Microsoft Teams app on their laptop or mobile devices. But there are other scenarios in which using a phone to attend a Teams meeting can be a better option than using an app on a computer:
  
- Internet connectivity is limited.

- A meeting is audio only.

- The person tried to join a Teams meeting and it failed.

- The call quality is better if they dial in.

- People can join a meeting "hands free" using Bluetooth devices.

- People find it's easier and more convenient for their situation.

## Who can attend an Audio Conferencing meeting? And who can I hear?

Anyone who has the dial-in number and conference ID can join a Teams meeting, unless the meeting organizer has locked the meeting.
  
Whether you're calling in using a phone or the Teams apps, you'll be able to hear everyone else on the call, and they can hear you. The meeting organizer has the ability to "mute" meeting attendees if they don't want to hear them.
  
## Can I add a toll-free number for my Audio Conferencing users?

Yes, toll-free phone numbers (service numbers) are available but only in some countries/regions. For a list of the numbers that are available, see [Country and region availability for Audio Conferencing and Calling Plans](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md).
  
## How many local dial-in numbers are currently supported?

There are local dial-in numbers that are assigned to you when you purchase the licenses for Audio Conferencing. The dial-in numbers will be included in the meeting invite. These local numbers will be only available to your organization. The phone assigned to your organization and that number is shared by the users within that organization that are enabled for Audio Conferencing. That means that Teams meetings scheduled by User A and another User B will both have the same dial-in number.
  
Local dial-in numbers, and also in some cases international dial-in numbers from the country where your organization is located, will be included on the meeting invite. If a meeting attendee uses a different number that is included in the invite, it will be a shared phone number.
  
## How many international dial-in numbers does Audio Conferencing in Microsoft 365 or Office 365 support?

For a current list of countries/regions, see [Phone numbers for Audio Conferencing in Microsoft Teams](phone-numbers-for-audio-conferencing-in-teams.md).
  
## What is the maximum length of the Audio Conferencing meetings?

The maximum length of time depends on who is in the meeting and the type of authentication they used to join the meeting.
  
|**Meeting attendees**|**Meeting end time**|
|:-----|:-----|
|Users have joined using the Teams app or have dialed in to the meeting.  <br/> |The meeting ends if there are no changes to the attendee list after 24 hours.  <br/> |
|All of the users are dialed in to the meeting but someone has used a PIN to enter the meeting.  <br/> |The meeting ends after 24 hours.  <br/> |
|All of the users are dialed in to the meeting but there wasn't anyone who used a PIN to enter the meeting.  <br/> | If anonymous users are allowed to start meetings, the meeting ends after four hours. If anonymous users aren't allowed to start meetings and all authenticated participants have left the meeting, the meeting ends 90 minutes after the last authenticated participant left. <br/> |

## How many total phone participants can I have in meetings?

See [Limits and Specifications](limits-specifications-teams.md) for total number of attendees allowed in meetings.

To find out about meeting limits, see [Meetings and calls](limits-specifications-teams.md#meetings-and-calls).
  
## Why did users start receiving emails with their Audio Conferencing information?

We added a new feature that allows you, the [admin](https://support.office.com/article/eac4d046-1afd-4f1a-85fc-8219c79e1504), to send and update Audio Conferencing information and PIN in email. To learn more about it, including how to disable it, see [Enable or disable sending emails when Audio Conferencing settings change in Microsoft Teams](enable-or-disable-sending-emails-when-their-settings-change-in-teams.md).
  
## Can a user get a personal conference ID?

Teams users will be randomly assigned conferencing IDs. Users can't reserve or set a static conference ID that only they can use.
  
## Can a user get operator assistance during a meeting?

No, a user can't get any operator assistance or support by pressing *0 during the meeting. If there are issues with Audio Conferencing, an administrator for an organization can contact [Microsoft support for Office 365](https://support.office.com/article/Microsoft-support-for-Office-365-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b).
  
## How does a user access or change their conference ID?

Teams users can find the conference ID assigned to them by scheduling a meeting in Outlook and Outlook on the web. Also, users can find the conference ID in the email that will be sent to them after they are set up.
  
> [!NOTE]
> Users won't be able to reset their conference ID. The conference ID can only be reset by you, the [admin](https://support.office.com/article/admin-eac4d046-1afd-4f1a-85fc-8219c79e1504), for the organization.
  
We're working on a solution that will let the user access and reset a conference ID without help from an organization's admin.

## How do users access or change their PIN?

Teams users can find the PIN in an email that will be sent to them once they are set up.

> [!NOTE]
> Teams users can change their pin. There is a link at the bottom of the meeting invite to reset their pin.
  
We are working on a solution that will let the user access and reset a PIN without help from an organization's administrator.
  
## What in-meeting dial-pad commands are supported?

For meeting participants and organizers:

| Command Name    | Command Keys | Description                                                                 |
|--------------   |--------------|-----------------------------------------------------------------------------|
| Command menu    | \*1          | Press \*1 to play the descriptions of dial-pad commands that are available. |
| Raise/lower hand| \*5          | Press \*5 to raise or lower hand.                                           |  
| Mute/unmute     | \*6          | Press \*6 to mute or unmute themselves.                                     |

For meeting organizers only:

| Command Name                   | Command Keys | Description                                                 |
|--------------------------------|--------------|-------------------------------------------------------------|
| Admit all                      | \*21         | Press \*21 to admit all participants waiting in the lobby.  |
| Mute all                       | \*22         | Press \*22 to mute all participants (except the organizer). |
| Toggle Enter/Exit Announcement | \*23         | Press \*23 to enable or disable Enter/Exit Announcement.    |

## Can attendees dial out to international phone numbers when they are in a Teams meeting?

Yes, attendees can dial out internationally and invite other callers into a Teams meeting. See [Dialing out from a Microsoft Teams meeting so other people can join it](dialing-out-from-a-teams-meeting-so-other-people-can-join-it.md).
  
## How does a Teams user schedule a meeting with Audio Conferencing meeting details?

When a user is assigned an **Audio Conferencing** license and the user creates a new Teams meeting in Outlook or Outlook on the web, the dial-in phone numbers and conferencing IDs are added automatically to the meeting invite.
  
## How does a user schedule and start a meeting when all attendees will be using a phone to dial in?

Scheduling a meeting that will be joined by all attendees using a phone to dial in is not different from scheduling a regular online meeting. However, there are two ways to start a meeting on which all of the participants use a phone to dial in:

- **Option #1**: By default, if the meeting organizer and all participants are joining a meeting using a phone, the meeting organizer needs to input her Audio Conferencing PIN to start it. Callers get asked if they want to authenticate as the organizer of a given meeting when they dial the phone number of an online meeting. All participants that join the meeting via dial-in before the organizer starts will be placed in the lobby and will listen to music on hold. For Teams meetings, the participants will join the meeting according to the value of the automatically admit people setting in the organizer's meeting policy.

- **Option #2**: The “Allow unauthenticated callers to be the first people in a meeting“ setting is disabled by default. If the setting is enabled for a given organizer, then all meetings scheduled by that organizer can be started before the organizer inputs the Audio Conferencing PIN. When this setting is enabled, the meeting will start as soon as the first participant joins it via a dial-in phone number, and the first participant won't be put in the lobby. For more information, see, [Manage Audio Conferencing settings for a user in Microsoft Teams](manage-the-audio-conferencing-settings-for-a-user-in-teams.md).

## Related topics

[Phone numbers for Audio Conferencing in Microsoft Teams](phone-numbers-for-audio-conferencing-in-teams.md)
