---
title: Plan for Teams meetings
ms.reviewer: bryanyce
ms.date: 10/11/2023
ms.topic: article
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.service: msteams
ms.subservice: meetings
ms.custom: intro-overview
audience: admin
f1.keywords:
- NOCSH
ms.collection: 
- M365-collaboration
- remotework
- m365initiative-meetings
- m365initiative-meetings-enabler
- enabler-strategic
- highpri
ms.localizationpriority: medium
search.appverid: MET150
appliesto: 
  - Microsoft Teams
description: Learn how to plan for meetings in Microsoft Teams.
---

# Plan for Teams meetings

**APPLIES TO:** ✔️Meetings ✖️Webinars ✖️Town halls ✔️Calls

Meetings in Teams include audio, video, and screen sharing for up to 1,000 people and view-only capabilities for participants over 1,000. Participants can be users in your organization or - if you allow it - people outside your organization. Meeting organizers can control which features are available in a given meeting and you can control the availability and default value for many of these features by using meeting policies.

The following types of meetings are available:
- Private meetings - meetings that individual users schedule with specific people
- Channel meetings - meetings that are visible to everyone in a channel
- Instant meetings - a method of starting an unscheduled meeting with people in a chat

To specify which users in your organization can start or schedule meetings, see [Manage who can start instant meetings and schedule meetings](manage-who-can-schedule-meetings.md).

## Meetings and calls

Your users might use meetings and calls interchangeably depending on their needs at a given time. Meeting policies and calling policies have separate settings for starting the meeting or call, recording, transcribing, and using closed captions. We recommend that you plan both sets of settings together in order to give your users a consistent experience as they use both calls and meetings.

The following table shows the policy settings that are similar between meetings and calls.

|User intent|Meeting policies|Calling policies|
|:------|:--------------|:---------------|
|Meet with someone by starting a call or instant meeting|[Private meeting scheduling](manage-who-can-schedule-meetings.md)|Make private calls|
|Record a meeting or call|[Meeting recording](meeting-recording.md)|Cloud recording for calling|
|Transcribe a meeting or call|[Transcription](meeting-transcription-captions.md)|Transcription|
|See closed captions in a meeting or call|[Live captions](meeting-transcription-captions.md)|Real-time captions in Teams calls|

For information about calling policies, see [Calling policies in Teams](teams-calling-policy.md).

## Recordings

You can specify which meeting organizers and attendees can record meetings. For someone to record a meeting, admin policies must allow both the person who starts the recording and the meeting organizer to record.

Organizers can't disable recording for a meeting if admin policies permit it, but they can limit recording to organizers and co-organizers if they have a Teams Premium license.

You can set meeting recordings to expire after a specified time. Managing the expiration date can help save storage space in organizations where many meetings are recorded. When a recording expires, it's moved to the recycle bin, and the file owner is notified. They can restore the recording if they need to.

Recording files are saved to OneDrive (for private meetings) or SharePoint (for channel meetings). Users who attended the meeting have permissions to view the recording by default. You can [block the download of meeting recording files](block-download-meeting-recording.md) if you need to.

To learn more about meeting recording and expiration and to configure recording policies for your organization, see [Teams meeting recording](meeting-recording.md).

If you have compliance requirements around meeting recordings, see [Manage Microsoft Teams meeting recording options for sensitive meetings](manage-meeting-recording-options.md).

## Meeting options for guests and external participants

People outside your organization can attend meetings hosted by your organizations as guests, people from trusted organization, or anonymous participants. You can configure each of these access methods separately.

#### Guest access for meetings

As long as guest access is turned on in Teams, guests in your organization can attend meetings. Several meeting features, including screen sharing options and the ability to start instant meetings, can be controlled separately for guests. For details, see [Turn guest access in Microsoft Teams on or off](set-up-guests.md).

Lobby settings affect how people outside your organization join meetings. You can set the following lobby settings by using meeting policies:

- Who can bypass the lobby
- Whether anonymous participants can start a meeting
- Whether people dialing in can bypass the lobby

The meeting organizer can change the settings for who can bypass the lobby, including people dialing in by phone

For complete details about the meeting lobby, see [IT Admins - Control who can bypass the meeting lobby in Microsoft Teams](who-can-bypass-meeting-lobby.md).

Meeting participants who can't be validated can attend meetings as anonymous participants. Depending on your business rules or compliance requirements, you might want to allow or prevent anonymous participants accessing meetings. See [Manage anonymous participant access to Teams meetings (IT admins)](anonymous-users-in-meetings.md) for information on how to configure anonymous access for meetings.

People from other trusted Microsoft 365 organizations can attend meetings without having to sign in to your organization. Both organizations must trust each other and users must be enabled for external access. For more information, see [Manage external meetings and chat with people and organizations using Microsoft identities](trusted-organizations-external-meetings-chat.md).

## Attendee limits and streaming options

Up to 10,000 attendees can join a Teams meeting, however, after 1,000 users enter a meeting, extra attendees will join with a view-only streaming experience. Streaming attendees don't have access to the meeting chat or be able to share content or video.

You can allow or prevent the streaming experience for meetings with more than 1,000 attendees. If you disable the streaming experience, meeting attendance is limited to the first 1,000 attendees.

For more information about the meeting view-only streaming experience, see [Teams view-only meeting experience](view-only-meeting-experience.md).

## Compliance features

You can use Teams meeting policies to control meeting recording, the lobby, and content sharing for different groups of users in your organization. Teams Premium offers various compliance-related meeting features, including sensitivity label capability, watermarks, encryption, and meeting templates. For details, see [Configure Teams meetings with three tiers of protection](configure-meetings-three-tiers-protection.md) and [Use Teams meeting templates, sensitivity labels, and admin policies together for sensitive meetings](meeting-templates-sensitivity-labels-policies.md).

## Apps for meetings

You can enhance meeting experiences by integrating and using meeting apps. You can add meetings apps to your Teams deployment by using the apps provided with Teams, using certified third-party apps and templates, and creating your own custom apps. For details, see [Apps for Teams meetings](/microsoftteams/platform/apps-in-teams-meetings/teams-apps-in-meetings).

For information about how meeting organizers can set meeting options, see [Participant settings for a Teams meeting](https://support.microsoft.com/office/53261366-dbd5-45f9-aae9-a70e6354f88e).

## Admin and meeting organizer meeting options

Teams admins and organizers have different policies and settings to control the meeting experience. The following table lists the types of features available for meetings and how the admin and organizer controls interact.

|Feature|Admins|Organizers|
|:------|:-----|:---------|
|[Attendance and engagement reports](/microsoftteams/teams-analytics-and-reports/meeting-attendance-report)|Can enforce on or off or allow organizer to choose.|Can turn on or off if allowed by admin.|
|[Audio and video](meeting-policies-audio-and-video.md)|Can set audio and video modes and network settings.|Can allow or prevent attendee mic and cameras.|
|[Chat](manage-meeting-chat.md)|Can manage whether users in the org can read and write chat messages. Admins can also manage chat messages in Teams meetings hosted by other organizations that you don’t have a two-way trust relationship with.|Can manage whether chat is available for their meetings.|
|[Collaboration features](meeting-policies-content-sharing.md)|Can control the availability of PowerPoint Live, whiteboard, and shared notes.|No control|
|[Content sharing](meeting-who-present-request-control.md)|Can control sharing mode and who can request control and can set a default for who can present.|Can control who can present.|
|[eCDN](streaming-ecdn-enterprise-content-delivery-network.md)|Can manage and configure the availability of eCDN for meetings with over 1,000 participants. |No control.|
|[End-to-end encryption(Teams Premium)](end-to-end-encrypted-meetings.md) |Can allow or prevent end-to-end encryption.|Can enforce end-to-end encryption if allowed by the admin.|
|[Green room](https://support.microsoft.com/office/5b744652-789f-42da-ad56-78a68e8460d5)|No control.|Can choose if green room is used for a meeting.|
|[Live translated transcription (Teams Premium)](meeting-transcription-captions.md) |Can control whether organizers with a Premium license can have live translated transcription for their meetings. |Can enable live translated transcription for themselves; attendees can always turn on live translated transcription. |
[Manage what attendees see(Teams Premium)](https://support.microsoft.com/office/manage-what-attendees-see-in-teams-meetings-19bfd690-8122-49f4-bc04-c2c5f69b4e16) |No control. |Can decide whose avatars or video feeds to spotlight during the town hall. |
|[Meeting join and lobby](who-can-bypass-meeting-lobby.md)|Can set the defaults for new meetings.|Can choose meeting join and lobby settings for each meeting.|
|[Q&A](manage-qna-for-teams.md)|Can manage if organizers can use Q&A in meetings.|Can decide if Q&A is available for their meetings if allowed by admins.|
|[Reactions and hand raise](manage-reactions-meetings.md)| Manage whether reactions and hand raise can be used in meetings created by organizers with this policy. |Can control whether reactions and hand raise can be used in their meetings. |
|[Recording](meeting-recording.md)|Can allow or prevent meeting recording and set recording expiration time.|If the admin enables recording, organizers can set who can record (Teams Premium) and automatic recording.|
|[Registration](set-up-meeting-registration.md)|Can allow or prevent meeting registration.|Can require meeting registration if allowed by admin.|
|[RTMP-In(Premium)](meetings-rtmp-in.md)|Can control whether organizers can use RTMP-In for their meetings. |Can produce their Teams meetings directly from an external hardware or software-based encoder to integrate different types of media. To start streaming from the encoder, organizers can choose RTMP-In from their meeting options and then access the RTMP link and key. |
|[Scheduling](manage-who-can-schedule-meetings.md)|Can define who can schedule private and channel meetings.|Can schedule meetings if allowed by admin.|
|[Streaming](view-only-meeting-experience.md)|Can allow or prevent streaming experience for attendees over 1,000.|No control.|
|[Meeting Theme(Teams Premium)](meeting-themes.md)|Can define meeting themes, including colors, images, and logo.|Can turn the admin-defined theme on or off.|
|[Transcription and captions](meeting-transcription-captions.md)|Can allow or prevent transcription and closed captions for attendees.|Can enable captions.|
|[Watermarks(Teams Premium)](watermark-meeting-content-video.md)|Can allow or prevent watermarks for attendee video and shared content|Can enforce watermarks if allowed by the admin|

## Related topics

[Plan for Teams webinars](plan-webinars.md)

[Plan for Teams town halls](plan-town-halls.md)

[Overview of meetings, webinars, and town halls](quick-start-meetings-live-events.md)
