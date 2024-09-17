---
title: Plan for Teams webinars
ms.reviewer: justle
ms.date: 1/16/2024
ms.topic: article
ms.author: wlibebe
author: wlibebe
manager: pamgreen
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
description: Learn how to plan for webinars in Microsoft Teams.
---

# Plan for Teams webinars

**APPLIES TO:** ✖️Meetings ✔️Webinars ✖️Town halls

A webinar is a two-way interactive virtual event where the presenters deliver information to attendees. This format provides extra control for an organizer over the conversation and participants. Common scenarios for webinars might include trainings, product demos, sales lead generation, customer events, company announcements, and showcasing products. Webinars can accommodate up to 1,000 attendees and allow organizers to gather registration data from attendees before the event.

As an admin, this article guides you through how to plan and prepare for webinars in your organization.

## Turn webinars on or off

Webinars are enabled by default. If you'd like to disable or manage webinars for users in your organization, see [Manage who can schedule webinars](set-up-webinars.md).

## Understand your policies

A combination of admin meeting and event policies with organizer and attendee settings to manage webinars.

If you'd like to get familiar with how policies work for Teams meetings and events, see [Manage meeting and event policies in Microsoft Teams](meeting-policies-overview.md).

For a full list of admin policies and organizer settings for webinars, see the [Webinar control comparison](#webinar-control-comparison) section in this article.

## Decide the types of webinars that organizers can create

There are a few key differences between in-org and public webinars. When managing the event access type for webinars to decide whether organizers can schedule public webinars, consider the information in the following table:

|Capability|In-org webinar|Public webinar|
|:----|:-----:|:-------:|
|Includes guests|✖️|✔️|
|Accessible to members of the organization that created the webinar|✔️|✔️|
|Accessible to anyone with a registration link|✖️|✔️|
|Anonymous users can register|✖️|✔️|
|Attendees type their name on the registration form when registering|✖️|✔️|
|Attendees must reenter their information after selecting the join link|✖️|✔️|
|Attendees have unique join links|✔️|✔️|
|Organizers can decide if attendees with a registration link can bypass the lobby|✔️|✔️|
|Organizers can decide if anyone who can't bypass the lobby is automatically rejected|✔️|✔️|
|Attendees can dial in to join|✖️|✖️|
|Includes external presenters|✔️|✔️|

## Webinar attendee interaction

Registered attendees join the webinar with their cameras and mics off; webinar organizers choose when to let attendees turn on their cameras or unmute.

As an admin, you can manage the following features attendees use for interaction during webinars:

- **Chat:** You can set chat to be on for everyone, off for everyone, or on for everyone but anonymous users. When chat is set to **On for everyone**, all meeting and webinar participants can read and write chat messages; the organizer's **Meeting chat** settings control the chat experience.

- **Q&A**: You can manage which organizers can turn on Q&A for meetings and webinars.
- **Reactions and hand raise**: You can manage which organizers have reactions available for attendees to use during their meetings and webinars.

## Premium webinars

A Teams Premium subscription includes the following features for webinars:

- Create a webinar wait list.
- Limit the day and time when people can register.
- Manage attendees’ view.
- Manually approve registrants.
- Use RTMP-in.
- Send reminder emails to registrants.
- Set up a green room for webinar presenters.

## Webinar control comparison

Teams admins and organizers have different policies and settings to control the webinar experience. The following table lists the types of features available for webinars and how the admin and organizer controls interact.

|Feature|Admins|Organizers|
|:------|:-----|:---------|
|[Attendance and engagement reports](/microsoftteams/teams-analytics-and-reports/meeting-attendance-report)|Can enforce on or off or allow organizer to choose.|Can turn on or off if allowed by admin.|
|[Audio and video](meeting-policies-audio-and-video.md)|Can set audio and video modes and network settings.|Can allow or prevent attendee mic and cameras.|
|[Chat](manage-meeting-chat.md)|Can manage whether organizers, presenters, and co-organizers, and attendees can read and write chat messages.|Can manage whether chat is available for their webinars.|
|[Collaboration features](meeting-policies-content-sharing.md)|Can control the availability of PowerPoint Live, whiteboard, and shared notes.|No control.|
|[Content sharing](meeting-who-present-request-control.md)|Can control sharing mode and who can request control and can set a default for who can present.|Can control who can present.|
|[Email communications (Teams Premium)](manage-email-communications.md)|Can control if event organizers and co-organizers can edit email templates for their webinars.|Can edit email templates  before they're sent out.|
|[External presenters](https://support.microsoft.com/office/schedule-a-webinar-in-microsoft-teams-0719a9bd-07a0-47fd-8415-6c576860f36a)|No control.|Can invite presenters from outside  of your organization. External presenters have a unique join link to join the webinar without waiting in the lobby.|
|[Green room](https://support.microsoft.com/office/green-room-for-teams-meetings-5b744652-789f-42da-ad56-78a68e8460d5)|No control.|Can choose if green room is used for a webinar.|
|[Hide attendee names (Teams Premium)](hide-attendee-names.md) |Can control whether organizers with a Premium license can hide the names and photos of attendees from other attendees in the stage, roster, and chat. | Can hide attendee names during webinars to protect identities and privacy. |
|[Limit presenter role permissions](presenter-role-reduction.md) |Can limit presenter role permissions for the tenant. |No control.|
|[Live translated transcription (Teams Premium)](meeting-transcription-captions.md) |Can control whether organizers with a Premium license can have live translated transcription for their webinars. |Can enable live translated transcription for themselves; attendees can always turn on live translated transcription. |
|[Manage what attendees see (Teams Premium)](https://support.microsoft.com/office/manage-what-attendees-see-in-teams-meetings-19bfd690-8122-49f4-bc04-c2c5f69b4e16)|No control|Can decide whose avatars or video feeds to spotlight during a Teams meeting. Others are hidden from view.|
|[Manage who can schedule webinars](set-up-webinars.md)|Can disable webinars for users and groups, control which organizers can schedule webinars,  and decide whether organizers can schedule public webinars.|Can schedule webinars if allowed by admin.|
|[Microsoft 365 Copilot in Teams meetings and events](copilot-teams-transcription.md)|Can control the default values and enforce specific values for Microsoft 365 Copilot in Teams meetings and events in organizers’ meeting options.|Can control whether Microsoft 365 Copilot in Teams meetings and events is used **Only during the meeting**, **During and after the meeting**, or **Off** during their webinars. Attendees can use Copilot if they have a Copilot Microsoft 365 Copilot license.|
|[Q&A](manage-qna-for-teams.md)|Can manage if organizers can use Q&A in webinars.|Can decide if Q&A is available for their webinars if allowed by admins. Webinar organizers and co-organizers can export the event's questions and answers to a CSV file.|
|[Reactions](manage-reactions-meetings.md)| Manage whether organizers with this policy can use reactions in their webinars. |Can control whether reactions can be used in their webinars. |
|[Recording](meeting-recording.md)| Can allow or prevent webinar recording. |If the admin enables recording, organizers can set who can record and automatic recording. |
|[Registration](set-up-webinars.md)| Can manage who can register for webinars. |Registration is required for attendees to attend webinars. Organizers can decide how many people can register for a webinar. With a Teams Premium license, they can also require manual registration approval, enable a waitlist, and limit registration start and end time.  |
|[Registration form](manage-registration-form-webinars.md)| Can manage the types of questions an organizer can require attendees to answer when registering for webinars. | Can edit the registration form depending on admin settings.|
|[RTMP-in (Premium)](meetings-rtmp-in.md)| Can allow or disable RTMP-in for organizers. | Can produce their Teams webinar directly from an external hardware or software-based encoder using Real-Time Messaging Protocol (RTMP).|
|[Theming](https://support.microsoft.com/office/customize-a-webinar-in-microsoft-teams-20491c28-863f-479b-8f61-85046d124f10) |No control.|Can customize their webinar's theme.|
|[Transcription and captions](meeting-transcription-captions.md)|Can allow or prevent transcription and closed captions for attendees.|Can enable captions.|
|[VOD publishing](manage-vod-publishing.md) |Can manage the types of recordings organizers can publish. |Can publish and modify webinar recordings. |
|[Voice isolation](voice-isolation.md)|Can control whether users can use voice isolation in webinars.|Can enable voice isolation.|
|[Webinar join and lobby](who-can-bypass-meeting-lobby.md)|Can set the defaults for new meetings and webinars.|Can choose meeting join and lobby settings for each webinar.|
|[Webinar usage report](/microsoftteams/teams-analytics-and-reports/teams-webinar-usage-report)|View activity and usage trends for all webinars created in your organization.|No control.|

## Need help with your webinar?

Are you and your organizers new to hosting webinars or just need some extra help? The Microsoft 365 Live Event Assistance Program (LEAP) can help you get more familiar with setting up and running webinars. The LEAP program is also available during the event to help if any questions or issues come up. For more information on the LEAP program, see [Microsoft 365 Live Event Assistance Program.](https://adoption.microsoft.com/virtual-event-guidance/assistance).
