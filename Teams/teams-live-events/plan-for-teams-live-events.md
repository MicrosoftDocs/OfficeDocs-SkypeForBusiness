---
title: Plan for live events in Microsoft Teams
author: lanachin
ms.author: v-lanac
manager: serdars
ms.date: 08/19/2019
ms.topic: article
ms.service: msteams
audience: admin
ms.reviewer: sonua
f1.keywords:
- NOCSH
localization_priority: Priority
ms.collection: 
  - M365-collaboration
search.appverid: MET150
description: In this article, you will learn about the factors to consider before you set up live events in Microsoft Teams.
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---

# Plan for live events in Microsoft Teams

When you're planning Teams live events to hold large meetings in your organization, there are several factors that you need to consider before starting to set it all up.

## Who can attend, create, and schedule live events

Anyone can attend a live event without a license. Read [Admin quick start - Meetings and live events](../quick-start-meetings-live-events.md).

The following prerequisites are required for the user to schedule a Teams live event.

Here are the licenses that must be assigned to produce or present a Teams live event:  

- A Microsoft or Office 365 Enterprise E1, E3, or E5 license or an Office 365 Education A3 or A5 license.
- A Microsoft Teams license. - this is included in the licenses above. 
- A Microsoft Stream license - is required if you are planning to share the content to an external app or device; see [Microsoft Stream licensing](https://docs.microsoft.com/stream/license-overview). 

  Users won't need a Microsoft Stream license assigned if you want users to only record and download the recordings. This will mean that the recordings aren't stored in Microsoft Stream but are instead stored in Azure Media Services (AMS) with a 30-day limit before it's deleted. It's not something at this point that an admin can control or manage including the ability to delete it.

> [!NOTE]
> At this time there aren't any Microsoft 365 Small Business plans that can be used to create and hold Teams live events.

It's important to know that a Microsoft 365 or Office 365 license is required to participate in a live event as an authenticated user, but this requirement depends on the production method used:

- **For events produced in Teams**  The user must be assigned a Teams license.
- **For events produced with an external app or device** The user must be assigned a Stream license.

> [!NOTE]
> Teams live events is now available for US Government Cloud Community (GCC) organizations.

For more information about licensing, see [Microsoft Teams add-on licensing](../teams-add-on-licensing/microsoft-teams-add-on-licensing.md).

The user must have:

- Private meeting scheduling in Teams enabled (*The TeamsMeetingPolicy -AllowPrivateMeetingScheduling parameter = True*).
- Video sharing enabled in Teams meetings (*The TeamsMeetingPolicy -AllowIPVideo parameter = True*).
- Screen sharing enabled in Teams meetings (*The TeamsMeetingPolicy -ScreenSharingMode parameter = EntireScreen*).
- Live event scheduling in Teams enabled (*The TeamsMeetingBroadcastPolicy -AllowBroadcastScheduling parameter = True*).
- Permissions to create live events in Stream (for external app or device production).
- Coexistence mode configured to be able to schedule Teams meetings (*Islands, Meeting First, or Teams Only*).

> [!IMPORTANT]
> Non-authenticated anonymous users can't be invited as producers or presenters in Teams live events.

For a guest to present in a live event, do the following:

1. [Add the user as a guest to a team](https://support.office.com/article/add-guests-to-a-team-fccb4fa6-f864-4508-bdde-256e7384a14f).
2. Have the user accept the guest invitation and join the team.
3. [Schedule the live event and add the guest to your event group](https://support.microsoft.com/article/schedule-a-teams-live-event-7a9ce97c-e1cd-470f-acaf-e6dfc179a0e2).

As a best practice, we recommend that you create a channel for producers and presenters of the live event so they can chat and share information before the event. Guests who don't have Microsoft 365 credentials won't see the Calendar in Teams. To make it easy for them to join the event, producers can post the event link to the channel. Presenters can then open Teams, go to the channel, and then click the link to join the event. 

## Who can watch live events

|**Attendee visibility**       |**Teams production**  |**External app or device production**  |
|------------------------------|-----------------|----------------------|
|Public (anonymous users)      |  Yes            |  No                  |
|Guest users                   |  Yes            |  No                  |
|Everyone in external access (federation) company |  Yes<sup>1</sup>|  No                  |
|Everyone in company           |  Yes            |  Yes                 |
|Specific groups / people      |  Yes            |  Yes                 |

<sup>1</sup> External access (federation) attendees can only be invited through People & Group <br>

## Teams live events and Skype Meeting Broadcast

The following table highlights core capabilities and features offered in live events and how they differ from Skype Meeting Broadcast.

> [!IMPORTANT]
> **Microsoft 365 live event limit increases**
> 
> To help customers meet rapidly changing communication needs, Microsoft 365 live events will temporarily raise default limits until October 1, 2020, for live events hosted in Teams. The following increases are being rolled out in late April 2020:
> - Attendee limit: events can support up to 20,000 attendees
> - Concurrent events: 50 events can be hosted simultaneously across a tenant
> - Event duration: event length has been increased to 16 hours per broadcast

|**Capability**   |**Skype Meeting Broadcast** |**Events produced in Teams** |**Events produced in external app or device** |
|---------|---------|---------|---------|
|Maximum audience size |10,000 attendees |10,000 attendees<sup>1</sup> |10,000 attendees<sup>1</sup> |
|Maximum duration of live event |4 hours |4 hours |4 hours |
|Maximum number of presenters and producers in a live event |10 <sup>2</sup> |10 <sup>2</sup> |10 <sup>2</sup> |
|Maximum number of concurrent live events per Microsoft 365 or Office 365 organization |15  | 15  | 15  |
|Live event creation |   Skype Meeting Broadcast Portal |Teams, Yammer via Teams | Teams, Yammer via Teams, Stream |
|Audience engagement – Yammer |&#x2714; |&#x2714; (integrated experience) |&#x2714; (integrated experience) |
|Audience engagement – Moderated Q & A |&#x2714;  |&#x2714; |&#x2714; |
|Producer client on Windows |&#x2714; (Skype for Business) |&#x2714; (Teams) |&#x2714; (Stream, Teams via Stream Embed) |
|Producer client on Mac |&#x274C;  | &#x2714; (Teams) |&#x2714; (Stream, Teams via Stream Embed) |
|Attendee count in Producer UI |&#x274C;  |&#x2714; (Teams) |&#x2714; (Stream, Teams via Stream Embed) |
|Allows multiple presenters |&#x2714; (Skype for Business) |&#x2714; (Teams) |N/A  |
|Invite a presenter during the meeting |&#x2714; (Skype for Business) |&#x274C; |N/A |
|Presenter join on Web and Mobile |&#x2714; (Skype for Business)  |&#x274C; |N/A |
|External access (federation) & Guest presenters/attendees |&#x2714; (Skype for Business)  |  &#x2714; (Teams) |N/A |
|Presenter – PSTN access |&#x274C; |&#x2714; (Teams) |N/A |
|Present a screen |&#x274C; |&#x2714; (Teams) |N/A |
|Share system audio on Windows (available only when screen sharing)|&#x274C; |&#x2714; (Teams) |&#x2714; |
|Present a PowerPoint (PPT sharing) |&#x2714; |&#x274C; (mitigated via screen sharing) |N/A |
|Cloud based meeting recording |&#x2714; |&#x2714; |&#x2714; |
|Auto publish recording to Stream |&#x274C; |&#x274C; |&#x2714; |
|Live captions and subtitles |&#x2714; |&#x2714; |&#x274C; |
|Captions in live event recordings |&#x2714; |&#x2714; |&#x2714; |
|Attendee DVR controls (pause, rewind) |&#x2714; |&#x2714; |&#x2714; |
|Partner eCDN Support |&#x2714; (Kollective, Hive) |&#x2714; (Kollective, Hive) |&#x2714; (Hive, Kollective, Ramp) |
|Post-broadcast attendance report for Producers |&#x2714; |&#x2714; |&#x274C; |
|Audience Sentiment Analysis – Live voting & polls |&#x2714; (Microsoft Pulse) |&#x274C; |&#x274C; |

<sup>1</sup> The limits that are set might be changed. Check [Limits and specifications for Teams](../limits-specifications-teams.md).<br/>
<sup>2</sup> You can have up to 250 presenters and producers in a live event, but only the last 10 who spoke show up in the list.

## Regional availability

You can use Teams live events in multiple regions across the world. The following information shows availability for event team members and attendees.

> [!IMPORTANT]
> The region for the event is automatically selected depending on the organizer and the Microsoft 365 tenant location.

**Available in these regional data centers**

- North America
- Central America
- South America
- Asia Pacific
- Europe/Africa

**Data location for these countries/regions (supported)**
- Australia
- Canada
- India
- Japan
- United Kingdom

**These countries/regions and clouds aren't supported**
- Germany
- France
- Norway
- South Africa
- South Korea
- Switzerland
- UAE
- Government Community Cloud (GCC)-H
- DOD

**Exclusions and considerations**

- **Data location:** Teams data locations, outside of the ones listed above, are not currently supported.
- **China:** Event team members and attendees will not be able to use Teams live events because Azure CDN is not accessible in China. A workaround is to use a company VPN connection, which gets the client connected to CDN via the customer's corporate network.

## Next steps

Go to [Set up for Teams live events](set-up-for-teams-live-events.md).

### Related topics

- [What are Teams live events?](what-are-teams-live-events.md)
- [Set up for Teams live events](set-up-for-teams-live-events.md)
- [Configure live events settings in Teams](configure-teams-live-events.md)
