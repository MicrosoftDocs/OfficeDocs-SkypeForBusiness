---
title: Plan for Teams town halls
ms.reviewer: sachung
ms.date: 10/12/2023
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

## Turn town halls on or off

Town halls are enabled by default. If you'd like to disable or manage town halls for users in your organization, see [Manage who can schedule town halls](set-up-town-halls.md).

## Get your network ready for town halls

There are four steps you must follow to ensure your network is set up to support town halls.

1. **Ensure your teams environment is set up to connect to our services.**<br>
Filler text description
2. **Ensure your devices are optimized to connect to our services.**<br>
Filler text description
3. **Special considerations for events in VPN environments.**<br>
Filler text description
4. **Optimize your Internal network via eCDN.**<br>
An Enterprise Content Delivery Network (eCDN) takes the video content from the internet and distributes the content throughout your enterprise without impacting network performance. If organizers in your organization have a Teams Premium subscription, they use the Microsoft first-party eCDN solution with town halls by default. For organizers with all other Teams subscriptions, you can enable them to use the Microsoft first-party eCDN solution or, alternatively, one of the following certified eCDN partners to optimize your network for town halls held within your organization:

- [Hive](https://www.hivestreaming.com/partners/integration-partners/microsoft/)
- [Kollective](https://kollective.com/ecdn-solutions/microsoft-live-events/)
- [Ramp](https://rampecdn.com/)

For more information about the Microsoft eCDN, see [Introduction to Microsoft eCDN](/ecdn/intro) and [Enterprise content delivery networks for streaming Microsoft Teams events](streaming-ecdn-enterprise-content-delivery-network.md).

For more information about the dimensions and measurements visible through CQD for town halls, search for the word "events" in [Dimensions and measurements available in Call Quality Dashboard (CQD)](dimensions-and-measures-available-in-call-quality-dashboard.md).

> [!NOTE]
> The Microsoft first-party eCDN solution is the default and only option for Premium users.

## Understand your policies

A combination of admin meeting and event policies with organizer and attendee settings manage town halls.

If you'd like to get familiar with how policies work for Teams meetings and events, see [Manage meeting and event policies in Microsoft Teams](meeting-policies-overview.md).

For a full list of admin policies and organizer settings for town halls, see the [Town hall control comparison](#town-hall-control-comparison) section in this article.

## In-org vs public town halls

When managing the event access type for town halls to decide whether organizers can schedule public town halls, consider the following points:

- External attendees can only join a town hall if the organizer sets the event to public.
- In town halls, guests are considered in-org.
- Town halls don't support external presenters.
- Attendees who aren't in your org(this includes anonymous and external access users) can't join private town halls.

## Premium town halls

With a Teams premium license, your users have access to extended capabilities. The following table shows a capability comparison:

|Capability|Town halls|Premium town halls|
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
|Organizer level real time monitoring|No|Yes|
|Essential emails|Yes|Yes|
|Email editing|No|Yes|

For more information on Teams premium, see [Teams Premium licensing](/microsoftteams/teams-add-on-licensing/licensing-enhance-teams).

## Monitor town halls in your organization

### Real time monitoring

You can use real-time data telemetry to monitor town halls and troubleshoot technical issues.

There are two types of real time monitoring for town halls.

1. **Real time monitoring of the presenter and organizer experience**<br>
You can view scheduled town halls and see audio, video, content sharing, and network-related issues. As an admin, you can use this telemetry to investigate any issues presenters and organizers experience during the town hall and troubleshoot in real time.<br>
To learn more about real time monitoring of presenters and organizers, see [Use real-time telemetry to troubleshoot poor meeting quality.](use-real-time-telemetry-to-troubleshoot-poor-meeting-quality.md)
1. **Real time monitoring of the attendee experience (Teams Premium)**<br>
 With a Teams premium license, you can use the analytics dashboard for performance analysis and network troubleshooting of the attendee experience during town halls.<br>
To learn more about real time monitoring of attendees, see [eCDN analytics.](/ecdn/technical-documentation/analytics)

### Call Quality Dashboard

You can use the Call Quality Dashboard(CQD) to monitor town hall quality at the org-wide level and optimize your network to drive performance quality.

To learn more about using CQD for town halls in your org, see [What is Call Quality Dashboard (CQD).](CQD-what-is-call-quality-dashboard.md)

### Town hall insights for organizers

With a Teams Premium license, during a town hall, organizers and co-organizers can see real-time event analytics like viewer count, attendees’ country/region, and more. The analytics consist of several data widgets, including charts and graphs, breakdowns tables, and a viewing experience timeline.

For more information on how organizers in your org can use insights for their town halls, see [Town hall insights in Microsoft Teams.](https://support.microsoft.com/office/town-hall-insights-in-microsoft-teams-def99575-61bf-4ea2-ad0e-c6e75dce7741)

For town hall organizers that don't have a Teams Premium license, they can check to see if their third party providers offer insights during town halls.

## Town hall control comparison

Teams admins and organizers have different policies and settings to control the town hall experience. The following table lists the types of features available for town halls and how the admin and organizer controls interact.

|Feature|Admins|Organizers|
|:------|:-----|:---------|
|[Attendance reports](/teams-analytics-and-reports/meeting-attendance-report)|Can enforce on or off or allow organizer to choose.|Can turn on or off if allowed by admin.|
|[Audio and video](meeting-policies-audio-and-video.md)|Can manage the availability and use of audio and video for presenters and organizers.| Only presenters and organizers can use their audio and video. Attendees can't share their audio or video, but interact through Q&A.|
|[Chat](manage-meeting-chat.md)|Can manage whether organizers, presenters, and co-organizers can read and write messages to each other during town halls.|Can chat amongst presenters and co-organizers. Attendees don't use chat during town halls.|
|[Content sharing](meeting-policies-content-sharing.md)|Can control sharing mode, who can request control, and can set a default for who can present.|Can control who can present amongst presenters, organizers, and co-organizers. Attendees can't share content in town halls.|
|[eCDN](streaming-ecdn-enterprise-content-delivery-network.md)|Can manage and configure the availability of eCDN for organizers.|No control.|
|[Email communications (Teams Premium)](manage-email-communications.md)|Can control if event organizers and co-organizers can edit email templates for their town halls.|Can edit email templates  before they're sent out.|
|[Green room](https://support.microsoft.com/office/green-room-for-teams-meetings-5b744652-789f-42da-ad56-78a68e8460d5) |No control.|Can choose if green room is used for a town hall.|
|[Live translated transcription](https://support.microsoft.com/office/view-live-transcription-in-microsoft-teams-meetings-dc1a8f23-2e20-4684-885e-2152e06a4a8b) |No control. |Can enable live translated transcription for themselves; attendees can always turn on live translated transcription. |
[Manage what attendees see](https://support.microsoft.com/office/manage-what-attendees-see-in-teams-meetings-19bfd690-8122-49f4-bc04-c2c5f69b4e16) |No control. |Can decide whose avatars or video feeds to spotlight during the town hall. |
|[Manage who can schedule town halls](set-up-town-halls.md)|Can disable town halls for users and groups, control which organizers can schedule town halls,  and decide whether organizers can schedule public town halls.|Can schedule town halls if allowed by admin.|
[Publishing](manage-vod-publishing.md) |Can manage the types of recordings organizers can publish. |Can publish and modify town hall recordings. |
|[Q&A](manage-qna-for-teams.md)|Can manage if organizers can use Q&A in town halls.|Can decide if Q&A is available for their town halls if allowed by admins. Q&A is the only way attendees can interact and engage with presenters and organizers.|
|[Recording](meeting-recording.md)|Can allow or prevent town hall recording. |Recordings start automatically for town halls, but organizers can turn this off. |
|[Recording expiration](meeting-recording.md)|Can manage whether recordings automatically expire. |By default, published recordings expire after 30 days. Organizers can extend the expiration date to 60 days. After the new date passes, they must reupload and republish the file to keep sharing.|
|[RTMP-In](meetings-rtmp-in.md)|Can control whether organizers can use RTMP-In for their town halls. |Can produce their Teams events directly from an external hardware or software-based encoder to integrate different types of media into the event. To start streaming from the encoder, organizers can choose RTMP-In from their meeting options and then access the RTMP link and key. |
|[Shared notes](meeting-policies-content-sharing.md)|Can manage whether organizers and co-organizers can use shared notes amongst other during town halls. |Can use shared notes with co-organizers during town halls |
|[Speaker coach](meeting-speaker-coach.md)|Can manage whether organizers, presenters, and co-organizers can us speaker coach during town halls. |Can use speaker coach for private real-time feedback and suggestions for improvement of themselves, co-organizers, and presenters. |
|[Transcription and captions](meeting-transcription-captions.md)|Can allow or prevent transcription and closed captions for attendees.| Only AI generated captions are available at this time. |

## Need help with your town hall?

Whether you and your organizers new to hosting town halls or just need some extra help, the Microsoft 365 Live Event Assistance Program (LEAP) can help you get more familiar with setting up and running town halls. The LEAP program is also available during the event to help if any questions or issues come up. For more information on the LEAP program, see [Microsoft 365 Live Event Assistance Program.](https://adoption.microsoft.com/virtual-event-guidance/assistance)
