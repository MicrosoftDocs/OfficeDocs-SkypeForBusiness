---
title: Overview of meetings, webinars, and town halls
ms.reviewer: 
ms.date: 10/01/2023
ms.topic: article
ms.author: wlibebe
author: wlibebe
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
description: A guide for administrators to roll out and configure meetings, webinars, and town halls in Microsoft Teams.
---

# Overview of meetings, webinars, and town halls

**APPLIES TO:** ✔️Meetings ✔️Webinars ✔️Town halls

There are multiple ways to meet in Microsoft Teams:

- Meetings
- Webinars
- Town halls
- Calls

This article, intended for administrators and IT Pros, describes the differences between meetings, webinars, and town halls. You can use this information as a first step in planning for these types of virtual meetings and events.

The sections below include further information for planning and configuring these features, as well as links to information for your end users.

The following table shows the main features that are different between meetings, webinars, and town halls. You can use this information to help determine which is best for the use cases in your organization. For a detailed look at the features available in each, see [Meetings, webinars, and town halls feature comparison](meeting-webinar-town-hall-feature-comparison.md).

|Feature|Meetings|Webinars|Town halls|
|:------|:-------|:-------|:---------|
|Lobby|✔️|✔️|✖️|
|Attendee mic and camera|✔️|✔️|✖️|
|End-to-end encryption|Premium|✖️|✖️|
|Watermarks|Premium|✖️|✖️|
|Theme|Premium|✔️|✔️|
|Streaming|Optional|Optional|Required|
|Registration|Optional|✔️|✖️|
|Interactive participants|1,000 (Enterprise plans)<br>300 (Business plans)|1,000|✖️|
|Streaming participants|10,000* (Enterprise plans only)|✖️|10,000*|
|Yammer integration|✖️|✖️|✔️|
|Breakout rooms|✔️|✔️|✖️|

*The usual 10,000 is increased to 20,000 through December 30, 2023.

## RTMP

RTMP-In allows organizers to produce their Teams meetings and events directly from an external hardware or software-based encoder using Real-Time Messaging Protocol (RTMP). RTMP-In must be turned on for the meeting organizer via a Teams meeting policy.

Meeting organizers who are enabled for RTMP-In can choose the option in meeting options and can access the RTMP link and key that they can use to start streaming from the encoder.

For details, see [Manage RTMP-In for Teams meetings](meetings-rtmp-in.md).

## eCDN

Teams streaming events can use enterprise content delivery networks (eCDNs), including the Microsoft eCDN and eCDNs from Microsoft partners. Teams streaming events include:

- Town halls
- Meetings with more than 1,000 participants

eCDN solutions include self-managing delivery technologies, real-time monitoring, and in-depth network analytics. Organizations monitor, scale, and optimize the distribution of video streams (and sometimes other content types) across your enterprise network.

Teams Premium features require the Microsoft eCDN, so streaming events organized by people with a Teams Premium license always use the Microsoft eCDN.

For details, see [Enterprise content delivery networks for streaming Microsoft Teams events](streaming-ecdn-enterprise-content-delivery-network.md)

## Manage who can create meetings, webinars, and town halls

You can manage which of your users can create meetings, webinars, and town halls by using meeting and event policies. For example, you might want to allow all of your users to create meetings, but only people in marketing to create webinars, and only executives to create town halls. Anyone invited can attend these types of meetings, but only those you specify can create them.

For details, see:
- [Manage who can start instant meetings and schedule meetings](manage-who-can-schedule-meetings.md)
- [Manage who can schedule webinars](set-up-webinars.md)
- [Manage who can schedule town halls](set-up-town-halls.md)


## Meetings

Meetings in Teams include audio, video, and screen sharing for up to 1,000 people and a view-only streaming experience for participants over 1,000. Participants don't need to be a member of an organization (or have a Teams account) to join a Teams meeting. They can join directly from the calendar invitation via the Join meeting link or call in via audio if available.

In addition to regularly scheduled meetings, your users can create channel meetings. With channel meetings, everybody in a team can see there's a meeting, join the meeting, and use the meeting chat.

Meetings are generally best for situations where participants need to interact with each other via voice or chat and where multiple people may be presenting.

For detailed information on how to plan for Teams meetings in your organization, see [Plan for Teams meetings](plan-meetings.md).

#### Key training for end users

The following table lists meetings training available to the end users in your organization:

| Training | Description |
|----------|--------|
| [Join a Teams meeting](https://support.office.com/article/078e9868-f1aa-4414-8bb9-ee88e9236ee4) | A quick training video for users who are new to Teams meetings. |
| [Schedule a meeting in Microsoft Teams](https://support.microsoft.com/office/943507a9-8583-4c58-b5d2-8ec8265e04e5) | Article that describes how to schedule different types of meetings. |
| [Participant settings in Microsoft Teams meetings](https://support.microsoft.com/article/53261366-dbd5-45f9-aae9-a70e6354f88e) | Article about  managing meeting options. |

## Webinars

Webinars are structured meetings where presenters and participants have clear roles. A key difference between webinars and Teams meetings is that webinars support robust registration management, a customizable event and registration site, and event-oriented default meeting options.

In addition to the base webinar features, we offer additional webinar functionality through the Teams Premium subscription. Some of these functionalities include (Premium features are bolded and marked with an asterisk):

- Allow registered users to bypass the lobby
- Assign a co-organizer
- ***Create a webinar wait list**
- ***Limit the day and time when people can register**
- Limit the number of people who can register
- ***Manage attendees’ view**
- ***Manually approve registrants**
- Require attendees to register
- ***Send reminder emails to registrants**
- ***Set up a green room for webinar presenters**
- Turn on Q&A for webinars with up to 1000 attendees
- ***Use RTMP-In for webinars**
- View attendance reports

To learn more about advanced webinar features, see [Microsoft Teams Premium licensing.](/MicrosoftTeams/teams-add-on-licensing/licensing-enhance-teams#webinars)

For detailed information on how to plan for Teams webinars in your organization, see [Plan for Teams webinars](plan-webinars.md).

#### Key training for end users

The following table lists webinars training available to the end users in your organization:

| Training | Description |
|----------|--------|
| [Get started with Teams webinars](https://support.microsoft.com/office/get-started-with-teams-webinars-42f3f874-22dc-4289-b53f-bbc1a69013e3) | A quick training video for users who are new to Teams webinars. |
| [Visual quick start guide](https://adoption.microsoft.com/files/assets/TeamsWebinarsGetStartedGuide.pdf) | A downloadable visual guide that describes how to start scheduling webinars. |

## Town halls

Town halls are generally best for situations where a limited number of presenters are presenting to a large group of attendees and direct interaction via chat or voice conversation isn't needed.

Town halls are streaming events, so attendees can't use their cameras and mics. Organizers can use the Q&A feature for interaction with attendees or schedule town halls through Viva Engage.

For detailed information on how to plan for Teams town halls, see [Plan for Teams town halls](plan-town-halls.md).

#### Key training for end users

The following table lists town halls training available to the end users in your organization:

| Training | Description |
|:----------|:--------|
|||


## Best practices for large meetings

This section provides guidance for administrators, along with tips that administrators can share with their presenters and organizers.

To run a successful event, follow the practices outlined below:

- For the best experience in large meetings, webinars, and live events, Microsoft recommends using the latest version of the Teams desktop client or Teams mobile clients.

- Ensure that all Microsoft [Network Connectivity Principles](/microsoft-365/enterprise/microsoft-365-network-connectivity-principles) have been followed both on-premises and for remote users.
- Use [real-time data telemetry](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/introducing-microsoft-teams-real-time-call-quality-analytics/ba-p/2912146) to monitor the event and identify any possible issues and its source.
  - Designate meeting monitors to [analyze](use-real-time-telemetry-to-troubleshoot-poor-meeting-quality.md) telemetry for users facing poor experience caused by metrics exceeding thresholds.
  - Set meeting monitors as presenters to disable rogue video streams, mute accidental live mics, and remove attendees if needed.


## Related topics

[Meetings and conferencing in Teams](deploy-meetings-microsoft-teams-landing-page.md)

[Use NDI® technology in Microsoft Teams](use-ndi-in-meetings.md)

[Teams settings and policies reference](settings-policies-reference.md)
