---
title: Plan for Teams meetings
ms.reviewer: 
ms.date: 07/01/2023
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

**APPLIES TO:** ![yes](media/yes.png)Meetings ![no](media/no.png)Webinars ![no](media/no.png)Town halls ![yes](media/yes.png)Calls


## Meetings and calls

Your users may use meetings and calls interchangeably depending on their needs at a given time. Meeting policies and calling policies have separate settings for starting the meeting or call, recording, transcribing, and using closed captions. We recommend that you plan both set of settings together in order to give your users a consistent experience as the use both calls and meetings.

The following table show the policy settings that are similar between meetings and calls.

|User intent|Meeting polices|Calling policies|
|:------|:--------------|:---------------|
|Meet with someone by starting a call or instant meeting|Private meeting scheduling|Make private calls|
|Record a meeting or call|Meeting recording|Cloud recording for calling|
|Transcribe a meeting or call|Transcription|Transcription|
|See closed captions in a meeting or call|Live captions|Real-time captions in Teams calls|

For information about calling policies, see [Calling policies in Teams](teams-calling-policy.md).

## Recordings

[Teams meeting recording](meeting-recording.md)

[Manage Microsoft Teams meeting recording options for sensitive meetings](manage-meeting-recording-options.md)

[Block the download of Teams meeting recording files from SharePoint or OneDrive](block-download-meeting-recording.md)

## Compliance features

[Configure Teams meetings with three tiers of protection](configure-meetings-three-tiers-protection.md)

Many of the meeting organizer controls can also be set by administrators by using the meeting templates and sensitivity labels that are available in Teams Premium.


[Use Teams meeting templates, sensitivity labels, and admin policies together for sensitive meetings](meeting-templates-sensitivity-labels-policies.md)

## Attendee limits and streaming options

Up to 10,000 attendees can join a Teams meeting, however, after 1000 users enter a meeting, additional attendees will join with a view-only streaming experience. Streaming attendees won't have access to the meeting chat or be able to share content or video.

You can allow or prevent the streaming experience for meetings with more than 1,000 attendees. If you disable the streaming experience, meeting attendance will be limited to the first 1,000 attendees.

For more information about the meeting view-only streaming experience, see [Teams view-only meeting experience](view-only-meeting-experience.md).

## Admin and meeting organizer meeting options

Some meeting features can be controlled by Teams administrators while others are controlled by the meeting organizer. The following table lists the types of features available for meetings and how the admin and organizer controls interact.

|Feature|Admins|Organizers|
|:------|:-----|:---------|
|[Attendance reports](/microsoftteams/teams-analytics-and-reports/meeting-attendance-report)|Can enforce on or off or allow organizer to choose|Can turn on or off if allowed by admin|
|[Audio and video](meeting-policies-audio-and-video)|Can set audio and video modes and network settings|Can allow or prevent attendee mic and cameras|
|[Chat](manage-meeting-chat.md) and [Q&A](manage-qna-for-teams.md)|Can choose if chat and Q&A are available|Can use chat and Q&A if allowed by admin|
|Collaboration features|Can control the availability of PowerPoint Live, whiteboard, and shared notes|No control|
|[Content sharing](meeting-policies-content-sharing.md)|Can control sharing mode and who can request control and can set a default for who can present|Can control who can present|
|[End-to-end encryption](end-to-end-encrypted-meetings.md) (Teams Premium)|Can allow or prevent end-to-end encryption|Can enforce end-to-end encryption if allowed by the admin|
|[Green room](https://support.microsoft.com/office/5b744652-789f-42da-ad56-78a68e8460d5) (Teams Premium)|No control|Can choose if green room is used for a meeting|
|[Meeting join and lobby](who-can-bypass-meeting-lobby.md)|Can set the defaults for new meetings|Can choose meeting join and lobby settings for each meeting|
|[Recording](meeting-recording.md)|Can allow or prevent meeting recording and set recording expiration time|If recording is enabled by admin, can set who can record and automatic recording|
|[Registration](set-up-meeting-registration.md)|Can allow or prevent meeting registration|Can require meeting registration if allowed by admin|
|[Scheduling](manage-who-can-schedule-meetings.md)|Can define who can schedule private and channel meetings|Can schedule meetings if allowed by admin|
|[Streaming](view-only-meeting-experience.md)|Can allow or prevent streaming experience for attendees over 1,000|No control|
|[Theme](meeting-themes.md) (Teams Premium)|Can define meeting themes, including colors, images, and logo|Can turn on or off the admin-defined theme|
|[Transcription and captions](meeting-transcription-captions.md)|Can allow or prevent transcription and closed captions for attendees|Can enable CART captions|
|[Translation](https://support.microsoft.com/office/4be2d304-f675-4b57-8347-cbd000a21260) (Teams Premium)|No control|Can enable live translated captions|
|[Watermarks](watermark-meeting-content-video.md) (Teams Premium)|Can allow or prevent watermarks for attendee video and shared content|Can enforce watermarks if allowed by the admin|

For information about how meeting organizers can set meeting options, see [Participant settings for a Teams meeting](https://support.microsoft.com/office/53261366-dbd5-45f9-aae9-a70e6354f88e).