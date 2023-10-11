---
title: Plan for Teams town halls
ms.reviewer: sachung
ms.date: 10/01/2023
ms.author: wlibebe
author: wlibebe
ms.topic: article
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
description: Learn what is a town hall in Microsoft Teams. Understand how to plan for town halls in Microsoft Teams for IT Admins.
---

# Plan for Teams town halls

**APPLIES TO:** ✖️Meetings ✖️Webinars ✔️Town halls

 Microsoft Teams town halls bring interactive video streaming to a new level. Town halls are meant for one-to-many communications where the presenters, organizers, and co-organizers are leading the interactions. The audience participation is primarily to view and react to the content being shared.

## Recordings and publishing

For town hall recordings, organizers have the ability to:

- Quickly publish a recording with all the right permissions set
- Modify the published recording

By default, recordings start once the town hall begins. Your users can change this setting in their meeting options for town halls.

As an admin, you control which types of town halls can have their recordings published.

## Turning off town halls

Town halls are enabled by default. If you'd like to disable town halls for users in your organization, see [Set up town halls](set-up-town-halls.md).

## eCDN

An Enterprise Content Delivery Network (eCDN) takes the video content from the internet and distributes the content throughout your enterprise without impacting network performance. If organizers in your organization have a Teams Premium subscription, they must use the Microsoft first-party eCDN solution with town halls. For organizers with all other Teams subscriptions, you can enable them to use the Microsoft first-party eCDN solution or, alternatively, one of the following certified eCDN partners to optimize your network for town halls held within your organization:

- [Hive](https://www.hivestreaming.com/partners/integration-partners/microsoft/)
- [Kollective](https://kollective.com/ecdn-solutions/microsoft-live-events/)
- [Ramp](https://rampecdn.com/)

For more information about the Microsoft eCDN, see [Introduction to Microsoft eCDN](/ecdn/intro).

> [!NOTE]
> The Microsoft first-party eCDN solution is the default and only option for Premium users.

## Attendee interaction

Attendees don't use their cameras or microphones during town halls. Instead, attendees interact and engage through **Q&A**. As an admin, you can manage which organizers can turn on Q&A for meetings and town halls.

## External participants

External attendees can join a town hall if the organizer sets the event to public.

## Advanced town halls

With a Teams premium license, your users have access to extended capabilities. The following table shows a comparison of capabilities between town halls and advanced town halls.

|Capability|Town halls|Advanced town halls|
|:------|:-----|:---------|
|Broadcast capacity|10k|20k|
|Attendee reporting|Yes|Yes|
|eCDN|3rd and 1st party|1st party|
|Duration|30 hours|30 hours|
|RTMP-in|Yes|Yes|
|Producer UX|Manage what attendees see |Manage what attendees see |
|Default audio and video off|Yes|Yes|
|Layouts|Focused curated view|Focused curated view|
|Green room|Yes|Yes|
|Manage what attendees see|Yes|Yes|
|AI generated captions|Yes|Yes|
|Q&A capacity|10k|20k|
|VOD|Yes|Yes|
|Organizer level|No|Yes|
|Essential emails|Yes|Yes|
|Email editing|No|Yes|

For more information on Teams premium, see [Teams Premium licensing](/microsoftteams/teams-add-on-licensing/licensing-enhance-teams).

## Town hall control comparison

|Feature|Admins|Organizers|
|:------|:-----|:---------|
|Attendance reports|Can enforce on or off or allow organizer to choose|Can turn on or off if allowed by admin|
|Audio and video|Attendees can't share their audio or video.|Attendees can't share their audio or video.|
|[Content sharing](meeting-policies-content-sharing.md)|Can control sharing mode and who can request control and can set a default for who can present|Can control who can present|
|[Green room](https://support.microsoft.com/office/green-room-for-teams-meetings-5b744652-789f-42da-ad56-78a68e8460d5) |No control|Can choose if green room is used for a town hall|
|[Live translated transcription](https://support.microsoft.com/en-us/office/view-live-transcription-in-microsoft-teams-meetings-dc1a8f23-2e20-4684-885e-2152e06a4a8b) |No control. |Can enable live translated transcription for themselves; attendees can always turn on live translated transcription. |
|[Q&A](manage-qna-for-teams.md)|Can choose if Q&A is available|Can use Q&A if allowed by admin|
|[Town hall  join and lobby](who-can-bypass-meeting-lobby.md)|Can set the defaults for new meetings and town halls. |The organizer can choose their settings while creating a town hall but can't change the settings after. |
|[Recording](meeting-recording.md)|Can allow or prevent town hall recording. |Recordings start automatically for town halls, but organizers can turn this off. |
|[Transcription and captions](meeting-transcription-captions.md)|Can allow or prevent transcription and closed captions for attendees| Only AI generated captions are available at this time. |
|[VOD](manage-vod-publishing.md) |Can manage the types of recordings organizers can publish. |Can publish town hall recordings.|
