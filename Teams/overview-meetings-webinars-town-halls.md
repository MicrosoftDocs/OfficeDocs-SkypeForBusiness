---
title: Overview of meetings, webinars, and town halls
ms.reviewer: 
ms.date: 10/13/2023
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
|Theme|Premium|Premium|Premium|
|Streaming|Above 1,000 participants|✖️|Automatic|
|Registration|Optional|✔️|✖️|
|Interactive participants|1,000 (Enterprise plans)<br>300 (Business plans)|1,000|✖️|
|Streaming participants|10,000 (Enterprise plans only)|✖️|Town halls: 10,000<br> Premium town halls: 20,000|
|Maximum total participants|11,000* (Enterprise plans only)|1,000|Town halls: 10,000<br> Premium town halls: 20,000|
|Breakout rooms|✔️|✖️|✖️|

*The usual 10,000 is increased to 20,000 through December 30, 2023. The maximum total participants for meetings is the sum of the interactive participants plus streaming participants.

For more information on limits and specifications for Teams webinars, meetings, and town halls, see [Limits and specifications for Microsoft Teams.](limits-specifications-teams.md)

## Manage who can create meetings, webinars, and town halls

You can manage which of your users can create meetings, webinars, and town halls by using meeting and event policies. For example, you might want to allow all your users to create meetings, but only people in marketing to create webinars, and only executives to create town halls. Anyone invited can attend these types of meetings, but only those you specify can create them.

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

Teams Premium offers additional webinar functionality through the Teams Premium subscription. The breakdown of features is  highlighted in the following table:

|Feature name | Webinar features | Premium webinar features |
|-------------------------------------------------------|:---------------------:|:-------------------------:|
|Allow registered users to bypass the lobby         |✔️                      |✔️                          |
|Assign a co-organizer                              |✔️                      |✔️                          |
|Limit the number of people who can register        |✔️                      |✔️                         |
|Require attendees to register                      |✔️                      |✔️                          |
|Set up a green room for webinar presenters                      |✔️                     |✔️                          |
|Turn on Q&A for webinars with up to 1,000 attendees |✔️                      |✔️                          |
|View attendance reports                            |✔️                      |✔️                          |
|Create a webinar wait list                         |                       |✔️                          |
|Limit the day and time when people can register    |                       |✔️                         |
|Manage attendees’ view                             |                       |✔️                          |
|Manually approve registrants                       |                       |✔️                          |
|Send reminder emails to registrants                |                       |✔️                          |
|Use RTMP-In for webinars                           |                       |✔️                         |

To learn more about advanced webinar features, see [Microsoft Teams Premium licensing.](/MicrosoftTeams/teams-add-on-licensing/licensing-enhance-teams#webinars)

For detailed information on how to plan for Teams webinars in your organization, see [Plan for Teams webinars](plan-webinars.md).

#### Key training for end users

The following table lists webinars training available to the end users in your organization:

| Training | Description |
|----------|--------|
| [Get started with Teams webinars](https://support.microsoft.com/office/get-started-with-teams-webinars-42f3f874-22dc-4289-b53f-bbc1a69013e3) | A quick training video for users who are new to Teams webinars. |
| [Visual quick start guide](https://adoption.microsoft.com/files/assets/TeamsWebinarsGetStartedGuide.pdf) | A downloadable visual guide that describes how to start scheduling webinars. |

## Town halls

Town halls are generally best for situations where a limited number of presenters are presenting to a large group of attendees and direct interaction via chat or voice conversation isn't needed. For these event format, attendees don't use their cameras and mics, but instead use Q&A to engage with presenters and organizers.

For detailed information on how to plan for Teams town halls, see [Plan for Teams town halls](plan-town-halls.md).

Teams Premium offers additional town hall functionality through the Teams Premium subscription. The breakdown of features is  highlighted in the following table:

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

## Best practices for large meetings

This section provides guidance for admins, along with tips that admins can share with their presenters and organizers.

To run a successful event, follow the practices outlined below:

- For the best experience in large meetings, webinars, and town halls, Microsoft recommends using the latest version of the Teams desktop client or Teams mobile clients.

- Ensure that all Microsoft [Network Connectivity Principles](/microsoft-365/enterprise/microsoft-365-network-connectivity-principles) have been followed both on-premises and for remote users. The network connectivity principles apply to meetings, webinars, and town halls.
- Use [real-time data telemetry](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/introducing-microsoft-teams-real-time-call-quality-analytics/ba-p/2912146) to monitor the event and identify any possible issues and its source.
  - Designate meeting monitors to [analyze](use-real-time-telemetry-to-troubleshoot-poor-meeting-quality.md) telemetry for users facing poor experience caused by metrics exceeding thresholds.
  - Set meeting monitors as presenters to disable rogue video streams, mute accidental live mics, and remove attendees if needed.

## Related topics

[Meetings and conferencing in Teams](deploy-meetings-microsoft-teams-landing-page.md)

[Use NDI® technology in Microsoft Teams](use-ndi-in-meetings.md)

[Teams settings and policies reference](settings-policies-reference.md)
