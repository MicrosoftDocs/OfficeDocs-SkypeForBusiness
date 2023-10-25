---
title: Plan for Teams town halls
ms.reviewer: sachung
ms.date: 10/17/2023
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

There are five steps you must follow to ensure your network is set up to support town halls.

1. **Ensure your teams environment is set up to connect to our services**<br>
Ensure that your network connectivity to Microsoft 365 follows our network connectivity principles outlined in [Microsoft 365 network connectivity principles](/microsoft-365/enterprise/microsoft-365-network-connectivity-principles). The network connectivity principles are standard principles to follow for all Microsoft 365 services, and not just specific to Teams town hall.
2. **Ensure your devices are optimized to connect to our services**<br>
As part of the network connectivity principles, ensure that the Microsoft 365 endpoints are reachable as defined in [Office 365 URLs and IP address ranges](/microsoft-365/enterprise/urls-and-ip-address-ranges).
3. **Understand special considerations for events in VPN environments**<br>
If your organization is using VPN connectivity for remote participants, review the guidance published in [Special considerations for Stream and Teams events in VPN environments](/microsoft-365/enterprise/microsoft-365-vpn-stream-and-live-events). This article details how to optimize the attendee traffic for direct connectivity (also known as split tunneling) to the service.
4. **Plan for bandwidth considerations for town halls**<br>
Follow the bandwidth requirements documented in [Prepare your organization's network for Teams](/MicrosoftTeams/prepare-network#bandwidth-requirements) for your organizers, co-organizers, presenters.<br>
Each attendee stream consumes approximately 1.5 Mbps of bandwidth; attendee connectivity  utilizes HTTPS. Physical locations that have a large/densely populated attendee profile should explore using an eCDN to optimize bandwidth usage.

5. **Optimize your Internal network via eCDN**<br>
An Enterprise Content Delivery Network (eCDN) takes the video content from the internet and distributes the content throughout your enterprise without impacting network performance. If organizers in your organization have a Teams Premium subscription, they use the Microsoft  eCDN solution with town halls by default. For organizers with all other Teams subscriptions, you can enable them to use the Microsoft eCDN solution or, alternatively, one of the following certified eCDN partner solutions to optimize your network for town halls held within your organization:

- [Hive](https://www.hivestreaming.com/partners/integration-partners/microsoft/)
- [Kollective](https://kollective.com/ecdn-solutions/microsoft-live-events/)
- [Ramp](https://rampecdn.com/)

For more information about the Microsoft eCDN, see [Introduction to Microsoft eCDN](/ecdn/intro) and [Enterprise content delivery networks for streaming Microsoft Teams events](streaming-ecdn-enterprise-content-delivery-network.md).

> [!NOTE]
> The Microsoft eCDN is required for Teams Premium users and is used automatically.

## Understand your policies

A combination of admin meeting and event policies with organizer and attendee settings manage town halls.

If you'd like to get familiar with how policies work for Teams meetings and events, see [Manage meeting and event policies in Microsoft Teams](meeting-policies-overview.md).

For a full list of admin policies and organizer settings for town halls, see the [Town hall control comparison](#town-hall-control-comparison) section in this article.

## In-org vs public town halls

When managing the event access type for town halls to decide whether organizers can schedule public town halls, consider the following points:

- External attendees can only join a town hall if the organizer sets the event to public.
- In town halls, guests are considered in-org.
- Attendees who aren't in your org (including anonymous and external access users) can't join in-org town halls.

## Premium town halls and live events

Live events will be deprecated on September 30, 2024. If you've been using live events for your organization, you might want to understand the differences and similarities between live events, town halls, and Premium town halls. With a Teams premium license, your users have access to extended town hall capabilities. The following table is a comparison of live events, town hall, and Premium town hall features:

|Capability|Live Events|Town halls|Premium town halls|
|:------| :---: | :---: | :---: |
|Broadcast capacity|10k|10k|20k|
|Concurrent events|15|15|50|
|Attendee reporting|✔️| ✔️|✔️|
|eCDN|Microsoft and partner providers|Microsoft and partner providers|Microsoft|
|Duration|4 hours|30 hours|30 hours|
|RTMP-in|✔️|✔️|✔️|
|Producer UX|✔️ |Manage what attendees see|Manage what attendees see |
|Default audio and video off|✔️|✔️|✔️|
|Layouts|Single Video, Video + Content​​|Dynamic focused curated view|Dynamic focused curated view|
|Green room|✔️|✔️|✔️|
|Live translated captions|✔️|6 languages|10 languages|
|Manage what attendees see|✖️|✔️|✔️|
|External presenters|✔️|✖️|✖️|
|AI generated captions|✔️|✔️|✔️|
|DVR|✔️|✖️|✖️|
|Q&A capacity|10k|10k|20k|
|VOD|✔️|✔️|✔️|
|Microsoft town hall insights|✖️|✖️|✔️|
|Essential emails|✖️|✔️|✔️|
|Email editing|✖️|✖️|✔️|

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

You can use the Call Quality Dashboard (CQD) to monitor town hall quality at the org-wide level and optimize your network to drive performance quality.

To learn more about using CQD for town halls in your org, see [What is Call Quality Dashboard (CQD).](CQD-what-is-call-quality-dashboard.md)

For more information about the dimensions and measurements visible through CQD for town halls, search for the word "events" in [Dimensions and measurements available in Call Quality Dashboard (CQD)](dimensions-and-measures-available-in-call-quality-dashboard.md).

### Town hall insights for organizers

With a Teams Premium license, during a town hall, organizers and co-organizers can see real-time event analytics like viewer count, attendees’ country/region, and more. The analytics consist of several data widgets, including charts and graphs, breakdowns tables, and a viewing experience timeline.

For more information on how organizers in your org can use insights for their town halls, see [Town hall insights in Microsoft Teams.](https://support.microsoft.com/office/town-hall-insights-in-microsoft-teams-def99575-61bf-4ea2-ad0e-c6e75dce7741)

For town hall organizers that don't have a Teams Premium license, you can check to see if your eCDN provider offers insights during town halls.

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
|[Live translated transcription (Teams Premium)](meeting-transcription-captions.md) |Can control whether organizers with a Premium license can have live translated transcription for their town halls. |Can enable live translated transcription for themselves; attendees can always turn on live translated transcription. |
[Manage what attendees see](https://support.microsoft.com/office/manage-what-attendees-see-in-teams-meetings-19bfd690-8122-49f4-bc04-c2c5f69b4e16) |No control. |Can decide whose avatars or video feeds to spotlight during the town hall. |
|[Manage who can schedule town halls](set-up-town-halls.md)|Can disable town halls for users and groups, control which organizers can schedule town halls,  and decide whether organizers can schedule public town halls.|Can schedule town halls if allowed by admin.|
[Publishing](manage-vod-publishing.md) |Can manage the types of recordings organizers can publish. |Can publish and modify town hall recordings. |
|[Q&A](manage-qna-for-teams.md)|Can manage if organizers can use Q&A in town halls.|Can decide if Q&A is available for their town halls if allowed by admins. Q&A is the only way attendees can interact and engage with presenters and organizers.|
|[Recording](meeting-recording.md)|Can allow or prevent town hall recording. |Recordings start automatically for town halls, but organizers can turn this off. |
|[Recording expiration](meeting-recording.md)|Can manage whether recordings automatically expire. |By default, published recordings expire after 30 days. Organizers can extend the expiration date to 60 days. After the new date passes, they must reupload and republish the file to keep sharing.|
|[RTMP-In](meetings-rtmp-in.md)|Can control whether organizers can use RTMP-In for their town halls. |Can produce their Teams events directly from an external hardware or software-based encoder to integrate different types of media into the event. To start streaming from the encoder, organizers can choose RTMP-In from their meeting options and then access the RTMP link and key. |
|[Shared notes](meeting-policies-content-sharing.md)|Can manage whether organizers and co-organizers can use shared notes amongst other during town halls. |Can use shared notes with co-organizers during town halls |
|[Speaker coach](meeting-speaker-coach.md)|Can manage whether organizers, presenters, and co-organizers can us speaker coach during town halls. |Can use speaker coach for private real-time feedback and suggestions for improvement of themselves, co-organizers, and presenters. |
|[Transcription and captions](meeting-transcription-captions.md)|Can allow or prevent transcription and closed captions for attendees.| Only AI generated captions are currently available. |

## Need help with your town hall?

Are you and your organizers are new to hosting town halls or just need some extra help? The Microsoft 365 Live Event Assistance Program (LEAP) can help you get more familiar with setting up and running town halls. The LEAP program is also available during the event to help if any questions or issues come up. For more information on the LEAP program, see [Microsoft 365 Live Event Assistance Program.](https://adoption.microsoft.com/virtual-event-guidance/assistance)
