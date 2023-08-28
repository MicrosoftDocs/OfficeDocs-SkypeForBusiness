---
title: Meetings, webinars, and live events
ms.reviewer: 
ms.date: 04/01/2020
description: A guide for administrators to roll out and configure meetings, webinars, and live events in Microsoft Teams.
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
---

# Meetings, webinars, and live events

There are multiple ways to meet in Microsoft Teams: meetings, webinars, and live events.

This article, intended for administrators and IT Pros, describes the differences between meetings, webinars, and live events. It then provides links to the information you need to quickly roll out this functionality for your users.

[Meetings](#meetings), [webinars](#webinars), and [live events](#live-events) are all types of meetings, but webinars and live events provide additional control for the organizer over the conversation and participants. Webinars provide two-way interaction while live events provide a managed Q&A experience. 

The different types of meetings also have different participant limits and participant capabilities. 

The following table summarizes the three types of meetings, the number of recommended participants, and how participants can interact in the meeting. Sections with more information about each type of meeting follow the table. This article also includes a section on [best practices for large meetings](#best-practices-for-large-meetings).

| Type of meeting | Number of participants | Interaction | Registration supported |
|----------|--------|--------|-----|
| Meetings  | Up to 20,000* |**Microsoft 365 Business Basic, Microsoft 365 Business Standard, and Microsoft 365 Business Premium:** <br> - You can host online meetings and video calls for up to [300 people](limits-specifications-teams.md) using Microsoft Teams. <br>  <br> **Microsoft 365 E3/E5, Microsoft 365 A3/A5, and Microsoft 365 Government G3/G5 plans:** <br> - You can host online meetings and video calls for up to 1,000 people using Microsoft Teams. <br>  - Participants up to 1,000 have fully interactive equal meeting capabilities.*** <br> - Participants over 1,000 up to 20,000 have [View-only](view-only-meeting-experience.md) capabilities.  | Yes |
| Webinars | - Up to 1,000<br>- Increased limits with [View-only](view-only-meeting-experience.md) capabilities coming soon. |- Participants up to 1,000 have fully interactive capabilities.<br> - Audience interaction configurable.<br> - Can specify presenters. | Yes |
| Live events | Up to 20,000** |- Broadcast to large audiences. <br>- Moderated Q&A for audience interaction. <br> - Can specify producers and presenters, including external presenters.<br>- Supports more advanced production capabilities. | No |

**The usual 10,000 is increased to 20,000 through December 30, 2023. You can schedule even greater numbers with live events in Viva Engage and/or Microsoft Stream. For more information, see [Live events across Microsoft 365](/stream/live-event-m365).

Note that NDI is fully supported in meetings, webinars, and live events, allowing you to produce the broadcast by using tools such as OBS and Wirecast. For more information, see [Use NDI® technology in Microsoft Teams](use-ndi-in-meetings.md).

***The view-only meeting experience is only available for Microsoft 365 E3/E5, Microsoft 365 A3/A5, and Microsoft 365 Government G3/G5 plans.

> [!NOTE]
> For details about quickly configuring Teams meetings and events on different platforms, see [Teams features by platform](https://support.microsoft.com/office/teams-features-by-platform-debe7ff4-7db4-4138-b7d0-fcc276f392d3).

> [!NOTE]
> For more information and to get guidance by role for delivering online events using Microsoft Teams, see the [Virtual Event Playbook](https://aka.ms/VirtualEventPlaybook). You can also join the [Virtual Event Forum](https://aka.ms/VirtualEventForum) on the Microsoft Tech Community.


## Meetings

**Meetings** in Teams include audio, video, and screen sharing for up to 1,000 people and [view-only capabilities](view-only-meeting-experience.md) for participants over 1,000. Participants don't need to be a member of an organization (or have a Teams account) to join a Teams meeting. They can join directly from the calendar invitation via the Join meeting link or call in via audio if available.  

As the administrator, you'll configure meeting settings and control which meeting features are enabled for your organization by specifying meeting policies.  

In addition to regularly scheduled meetings, your users can create channel meetings. With channel meetings, everybody in a team can see there is a meeting, join the meeting, and use the meeting chat. Channel meetings are a way to quickly invite everyone in a team to a meeting. For more information about how end users schedule meetings, see [Schedule a meeting](https://support.microsoft.com/office/943507a9-8583-4c58-b5d2-8ec8265e04e5).

Your users can also require attendees to register for meetings. To learn more about how to manage meetings with registration, see [Set up meeting registration](set-up-meeting-registration.md)

For information about the view-only meeting experience, see [Teams view-only meeting experience](view-only-meeting-experience.md).

### Articles for administrators

The following table highlights key articles that you'll want to review:

| Article | Description |
|----------|--------|
| [Meeting policies](meeting-policies-overview.md)  | Describes how to create and manage the policies that determine which features are available to meeting participants. |
| [Manage Teams meeting recording](meeting-recording.md) | Describes how to manage meeting recordings. |
| [Manage your organization's devices](device-management.md)| Describes how to manage your organization's devices, such as phones and Teams Rooms. |
| [Use real-time telemetry to troubleshoot poor meeting quality](use-real-time-telemetry-to-troubleshoot-poor-meeting-quality.md) | Describes how to use Real-Time Analytics (RTA) to troubleshoot poor Microsoft Teams meeting quality for individual users.|
| [Set up meeting registration](set-up-meeting-registration.md)  | Describes how to allow your users to create meetings with registration. |
| [Attendance report for meetings and webinars in Microsoft Teams](/teams-analytics-and-reports/meeting-attendance-report.md) | An article that describes how to manage whether organizers can download the attendance report for their meetings, whether participants can opt out, and what information is in the attendance summary. |

### Key training for end users

The following table lists training available to the end users in your organization:

| Training | Description |
|----------|--------|
| [Manage meetings](https://support.office.com/article/join-a-teams-meeting-078e9868-f1aa-4414-8bb9-ee88e9236ee4) | A quick training video for users who are new to Teams meetings. |
| [Schedule a meeting](https://support.microsoft.com/office/schedule-a-meeting-in-teams-943507a9-8583-4c58-b5d2-8ec8265e04e5) | Article that describes how to schedule different types of meetings. |
| [Run effective meetings with Teams](https://microsoftteams.eventbuilder.com/MaximizingTeamsMeetings) | A free instructor-led class about how to make meetings more engaging, productive, and meaningful. |
| [Change participant settings for a Teams meeting](https://support.microsoft.com/article/change-participant-settings-for-a-teams-meeting-53261366-dbd5-45f9-aae9-a70e6354f88e) | Article about  managing meeting options. |
| [Schedule a Teams meeting with registration](https://support.microsoft.com/office/schedule-a-teams-meeting-with-registration-435b2b67-c1bd-411e-9be6-9ed1b4a9f04a#:~:text=Schedule%20the%20meeting%201%20In%20the%20Teams%20calendar%2C,start%20and%20end%20times%2C%20and%20a%20description.%20) | Article that describes how to require registration when creating meetings. |

## Webinars

**Webinars** are structured meetings where presenters and participants have clear roles. A key difference between webinars and Teams meetings is that webinars support robust registration management, customizable event and registration site, and event-oriented default meeting options.

In addition to the base webinar features, we offer additional webinar functionality through the Teams Premium subscription. 

Some of the base webinar features and premium webinar features are highlighted in the following table:

|                                                       | Base Webinar Features | Premium Webinar Features |
|-------------------------------------------------------|:---------------------:|:-------------------------:|
|**Allow registered users to bypass the lobby**         |X                      |X                          |
|**Assign a co-organizer**                              |X                      |X                          |
|**Limit the number of people who can register**        |X                      |X                          |
|**Require attendees to register**                      |X                      |X                          |
|**Turn on Q&A for webinars with up to 1000 attendees** |X                      |X                          |
|**View attendance reports**                            |X                      |X                          |
|**Create a webinar wait list**                         |                       |X                          |
|**Limit the day and time when people can register**    |                       |X                          |
|**Manage attendees’ view**                             |                       |X                          |
|**Manually approve registrants**                       |                       |X                          |
|**Send reminder emails to registrants**                |                       |X                          |
|**Set up a green room for webinar presenters**         |                       |X                          |
|**Use RTMP-In for webinars**                           |                       |X                          |

To learn more about advanced webinar features, see [Microsoft Teams Premium licensing.](/MicrosoftTeams/teams-add-on-licensing/licensing-enhance-teams#webinars)

For more information about functionality and how to set up webinars, see [Set up webinars](set-up-webinars.md).

### Articles for administrators 

The following table highlights key articles that you'll want to review:

| Article | Description |
|----------|--------|
| [Set up webinars](set-up-webinars.md)  | An article that describes how to allow your users to create webinars. |
| [Manage email communications for webinars](manage-email-communications.md) | An article that describes how to manage whether organizers and co-organizers can use email templates for their webinars.|
| [Manage the registration form for webinars](manage-registration-form-webinars.md) | An article that describes how to manage the types of questions an organizer can require attendees to answer when registering for webinars. |
| [Attendance report for meetings and webinars in Microsoft Teams](/teams-analytics-and-reports/meeting-attendance-report.md) | An article that describes how to manage whether organizers can download the attendance report for their webinars, whether participants can opt out, and what information is in the attendance summary. |

### Key training for end users

The following table lists training available to the end users in your organization:

| Training | Description |
|----------|--------|
| [Get started with Teams webinars](https://support.microsoft.com/office/get-started-with-teams-webinars-42f3f874-22dc-4289-b53f-bbc1a69013e3) | A quick training video for users who are new to Teams webinars. |
| [Visual quick start guide](https://adoption.microsoft.com/files/assets/TeamsWebinarsGetStartedGuide.pdf) | A downloadable visual guide that describes how to start scheduling webinars. |

## Live events

**Live events** are structured meetings that enable your organization to schedule and produce events that stream to large online audiences—up to 20,000 people. With live events, the audience interaction is a managed Q&A experience.

### Articles for administrators

The following table highlights key articles that you'll want to review:

| Article | Description |
|----------|--------|
| [What are Teams live events?](teams-live-events/what-are-teams-live-events.md)  | A quick introduction to live events. |
| [Plan for Teams live events](teams-live-events/plan-for-teams-live-events.md) | What you need to know before configuring live events. |
| [Set up for Teams live events](teams-live-events/set-up-for-teams-live-events.md) | Describes prerequisites such as network planning. |
| [Configure live events](teams-live-events/configure-teams-live-events.md) | Steps for configuring live events.|

### Key training for end users

The following table lists training available to the end users in your organization:

| Training | Description |
|:----------|:--------|
| [Get started with live events](https://support.office.com/article/d077fec2-a058-483e-9ab5-1494afda578a) | An introduction to live events and how to get started. |
| [Teams Live Events video training](https://support.microsoft.com/office/f92363a0-6d98-46d2-bdd9-f2248075e502) | Video that describes how to plan and schedule a live event.  |

To produce larger scale virtual events, review the [Virtual Event Guide](https://adoption.microsoft.com/virtual-event-guidance/), which has guidance for event organizers, technical producers, IT professionals, and content creators.

## Apps for meetings

Microsoft enables you to enhance meeting experiences by integrating and using meeting apps. For example, whiteboard integration in Teams meetings is powered by the Whiteboard web app, which lets Teams meeting participants draw, sketch, and write together on a shared digital canvas.

You can add meetings apps to your Teams deployment by using the apps provided with Teams,  using certified third-party apps and templates, and creating your own custom apps.

The following table lists articles for more information:

| Article | Description |
|----------|--------|
| [Overview of Teams apps](apps-in-teams.md) | Introduction to apps and how to deploy apps for your organization. |
| [Apps for Teams meetings](/microsoftteams/platform/apps-in-teams-meetings/teams-apps-in-meetings) | Overview of meeting app extensibility, API references, and how to enable and configure apps for meetings. |
| [Manage the Whiteboard in Teams](manage-whiteboard.md) | Describes Whiteboard functionality and how to enable and disable for your organization. |

## License requirements for meetings, webinars, and live events

Anyone can attend a Teams meeting, webinar, or Public Live Event for free—no license is required.

For the people who organize, schedule, and host meetings, webinars, or live events, they'll need one of the Microsoft 365 licenses listed in the [Microsoft Teams service description](/office365/servicedescriptions/teams-service-description). If you're already using Teams, you probably have the license you need for organizing and hosting meetings, webinars, and live events.

For information about Teams Premium licensing, see [Teams Premium licensing](teams-add-on-licensing/licensing-enhance-teams.md).

To allow people to dial in to a meeting by phone, you'll need to set up audio conferencing. For more information about audio conferencing, see [Audio conferencing in Teams](deploy-audio-conferencing-teams-landing-page.md).

## Best practices for large meetings

This section provides guidance for administrators, along with tips that administrators can share with their presenters and organizers.

To run a successful event, follow the practices outlined below:

- For the best experience in large meetings, webinars, and live events, Microsoft recommends using the latest version of the Teams desktop client or Teams mobile clients.

- Ensure that all Microsoft [Network Connectivity Principles](/microsoft-365/enterprise/microsoft-365-network-connectivity-principles) have been followed both on-premises and for remote users.
- Use [real-time data telemetry](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/introducing-microsoft-teams-real-time-call-quality-analytics/ba-p/2912146) to monitor the event and identify any possible issues and its source.
  - Designate meeting monitors to [analyze](use-real-time-telemetry-to-troubleshoot-poor-meeting-quality.md) telemetry for users facing poor experience caused by metrics exceeding thresholds.
  - Set meeting monitors as presenters to disable rogue video streams, mute accidental live mics, and remove attendees if needed.

### Guidelines for your end users

Your organizers and presenters should implement the below recommendations:

- For meetings with more than 10 participants, use [Q&A](/MicrosoftTeams/manage-qna-for-teams) to give participants the opportunity to formally ask and receive answers to questions, as well as engage in structured discussions.

- To create a smooth meeting, event organizers can set pre-defined presenters. After a meeting has started, presenters also can promote other attendees to the presenter role.

- Define a co-organizer via meeting options (Public preview)

- Pre-configure video and microphone settings to control attendees’ experiences.
  - Disable attendees’ microphones to avoid disturbances. If someone needs to interact during the meeting, allow them to un-mute when they raise their hand.
  - Disable attendees’ video to avoid visual distractions. During appropriate times in the meeting, video can be permitted for all attendees or specific individuals.

- Use polls and Q&A during the meeting.

- Use lobby controls to control meeting entry or lobby holds.

- Run the [Microsoft 365 network connectivity test](https://connectivity.office.com/) to verify network suitability several days prior to and the day of the event.

- If presenting from home, verify other devices are not consuming high bandwidth (Streaming services, online gaming, large downloads).

- Present from an endpoint with a wired connection for more reliable audio, video, and screen sharing.

- Ensure users are on the latest Teams app on a desktop or mobile device.

- When using a laptop, check for high network connectivity and sufficient power.

- Schedule a dry run prior to the event to identify device, lighting, or network issues. This will also ensure that organizers/presenters are familiar with features they’ll be using.
  - Schedule additional practice runs if issues were encountered to ensure remediation efforts were successful.
  
- Utilize features such as spotlight, PowerPoint Live, meeting recording, captions, and transcriptions to promote engagement and effectiveness.

- Presenters and participants should use the Teams desktop app to provide an optimal experience.

- Participants should turn off chat notifications during large meetings to avoid distractions.

- For more tips on hosting large meetings, see [Best practices for a large Teams meeting](https://support.microsoft.com/office/best-practices-for-a-large-teams-meeting-ce2cdb9a-0546-43a4-bb55-34ab98ab6b16).

## Related topics

[Meetings and conferencing in Teams](deploy-meetings-microsoft-teams-landing-page.md)

[Set up webinars in Teams](set-up-webinars.md)

[Live events in Teams](teams-live-events/what-are-teams-live-events.md)

[Teams view-only meeting experience](view-only-meeting-experience.md)

[Limits and specifications for Teams](limits-specifications-teams.md)
