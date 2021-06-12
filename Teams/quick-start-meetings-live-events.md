---
title: Quick start - Meetings, live events, and webinars in Microsoft Teams
ms.reviewer: 
description: A quick start guide for administrators to get licenses for, roll out, and configure online meetings and live events in Microsoft Teams.
ms.topic: article
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.service: msteams
audience: admin
f1.keywords:
- NOCSH
ms.collection: 
- M365-collaboration
- remotework
- m365initiative-meetings
- m365initiative-meetings-enabler
- enabler-strategic
localization_priority: Priority
search.appverid: MET150
appliesto: 
  - Microsoft Teams
---


# Quick start - Meetings, webinars, and live events in Microsoft Teams

There are multiple ways to meet in Microsoft Teams: meetings, webinars, and live events. 

This article briefly describes the main differences in types of meetings and how to quickly roll out and configure meetings, webinars, and live events for your organization.

> [!Note]
> For details about quickly configuring Teams meetings and events on different platforms, see [Teams features by platform](https://support.microsoft.com/office/teams-features-by-platform-debe7ff4-7db4-4138-b7d0-fcc276f392d3).

## Types of meetings

Meetings, webinars, and live events are all types of meetings, but webinars and live events are a type of structured meeting that provide additional control for the organizer over the conversation and participants. While webinars provide for more participant interaction than live events, both have limited interaction compared to an unstructured meeting. The different types of meetings also have different participant limits and participant capabilities.


 - **Meetings** in Teams include audio, video, and screen sharing for up to 1000 people. They're one of the key ways to collaborate in Teams. And particpants don't need to be a member of an organization (or even have a Teams account) to join a Teams meeting--all they need to do is look in the invitation for instructions about calling in.

 - **Webinars** are structured meetings where instructors and participants have clear roles, often used for training purposes or sales and marketing presentation scenarios. A key difference is that webinars require registration. After setting up webinars in your organization, your users can schedule webinars and open registration to attendees. For more information about how to set up webinars, see [Set up webinars in Teams](set-up-webinars.md). With webinars, you can configure your meeting to be interactive to the first 1000 users, but view only for the remaining users up to 20,000.

 - **Live events** are structured meetings that enable you to schedule and produce events that stream to large online audiences - up to 20,000 people. If you need a meeting with broadcast capabilities only for more than 1000 people, use a live event. With live events, audience participation is limited to posting questions.

 The following table briefly summarizes the three types of events, the number of recommended participants, and how participants can interact in the event.

 | Type of event | Number of participants | Interaction | Registration required |
|----------|--------|--------|-----|
| Meetings | Up to 1000 | Interactive chat with multiple presenters | No |
| Webinars | Up to 20,000* |-Interactive up to 1000 <br> -View only from 1000-20,000 <br> -Interaction configurable, but limited| Yes |
| Live events | 1001 to 20,000** |- Broadcast to large audiences <br>- Audience interaction limited to posting questions | No |
||||

*The usual 10,000 had increased to 20,000 during COVID.<br>
**This number reflects Live Events in Teams. The usual 10,000 has increased to 20,000 during COVID. Note that you can schedule even greater numbers with Live Events through Yammer and/or Microsoft Stream. For more information, see...  


## License requirements for meetings, webinars, and live events

Anyone can attend a Teams meeting, webinar, or public live event for free - no license is required. 

For the people who will organize, schedule, and host meetings, webinars, or live events, they'll need one of the Microsoft 365 licenses listed in the table below. If you're already using Teams, you probably have the license you need for organizing and hosting meetings, webinars, and live events.

Meeting audio is part of a Teams meeting, but if you want people to be able to dial in to a meeting by phone, you'll need to provide a dial-in number, which requires setting up audio conferencing. For more information about audio conferencing, see [Audio conferencing in Teams](deploy-audio-conferencing-teams-landing-page.md).


| Action | License(s) required | Notes | 
|----------|--------|--------|
| Join a meeting | No license required | Any email address can participate| 
| Join a meeting using a dial-in phone number | No license required | Any phone number can dial into a meeting provided the meeting organizer has set up audio conferencing<sup>1</sup>  |
| Join a live event | No license required
| Join a webinar | No license required
| Create a Teams meeting | An F3, E1, E3, or E5 license |  |
| Create a Teams meeting with dial-in phone number | An F3, E1, E3, or E5 license plus Audio Conferencing add-on license<sup>1</sup>
| Create a Teams live event | E1, E3, E5 license | |
| Create a Teams webinar | | 
| Dial out from a meeting to add someone at their **Call me at** number | An F3, E1, E3, or E5 license plus Audio Conferencing add-on license<sup>2</sup> | | 
|||

> <sup>1</sup>  Meeting organizers need to have an [Audio Conferencing add-on license](teams-add-on-licensing/microsoft-teams-add-on-licensing.md) to send an invite that includes dial-in conferencing.
>
> <sup>2</sup>  Meeting dial out to a [**Call me at** number](set-up-the-call-me-feature-for-your-users.md) requires organizers to have an E5 or [Audio Conference add-in license](teams-add-on-licensing/microsoft-teams-add-on-licensing.md). A [dial plan](what-are-dial-plans.md) may also be needed.

To learn more about licensing, read [Microsoft Teams service description](/office365/servicedescriptions/teams-service-description).

## Make sure your network's ready

If you already prepared your network when you rolled out Microsoft 365, you're probably all set. In any case - and especially if you're rolling out Teams quickly as your first Microsoft 365 workload to support **remote workers** - read [Prepare your organization's network for Teams](prepare-network.md) to be sure you're ready.

## Meetings and conferencing

- As the admin, you'll configure [meeting settings](meeting-settings-in-teams.md) for everyone. Then you'll use [meeting policies](meeting-policies-in-teams.md) to control what meeting features are (and aren't) available for your users.

- To learn about managing meeting recording, read [Teams cloud meeting recording](cloud-recording.md).

- If your users are new to Teams meetings, share the [Manage meetings](https://support.office.com/article/join-a-teams-meeting-078e9868-f1aa-4414-8bb9-ee88e9236ee4) training with them. Check out our instructor-led online class, [Run effective meetings with Teams](https://microsoftteams.eventbuilder.com/MaximizingTeamsMeetings).

- To learn about managing meeting options, read [Change participant settings for a Teams meeting](https://support.microsoft.com/article/change-participant-settings-for-a-teams-meeting-53261366-dbd5-45f9-aae9-a70e6354f88e).

- Don't forget about [managing your users' devices](./devices/device-management.md) - phones, headsets, cameras. To get the latest and up-to-date information on Teams certified devices, go to [Teams devices](https://office.com/teamsdevices).

## Live events

- Similar to meetings, you - the admin - [configure live events](teams-live-events/configure-teams-live-events.md) for everyone. Then set up (and assign) [live event policies](teams-live-events/set-up-for-teams-live-events.md) to control what your users can (and can't) do.

- Make sure your live event producers and organizers are trained - send them to [Get started with live events](https://support.office.com/article/get-started-with-microsoft-teams-live-events-d077fec2-a058-483e-9ab5-1494afda578a).

- If you're new to live events, check out [What are Teams live events?](teams-live-events/what-are-teams-live-events.md) and [Plan for Teams live events](teams-live-events/plan-for-teams-live-events.md).

## Related topics

[Meetings and conferencing in Teams](deploy-meetings-microsoft-teams-landing-page.md)

[Audio conferencing in Teams](deploy-audio-conferencing-teams-landing-page.md)

[Live events in Teams](teams-live-events/what-are-teams-live-events.md)

[Limits and specifications for Teams](limits-specifications-teams.md)

[Microsoft Technical Community: Live events in Microsoft 365](https://resources.techcommunity.microsoft.com/live-events/)
