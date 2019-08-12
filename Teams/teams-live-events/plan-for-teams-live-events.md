---
title: Plan for live events in Microsoft Teams
author: chuckedmonson
ms.author: chucked
manager: serdars
ms.date: 07/10/2019
ms.topic: article
ms.service: msteams
audience: admin
ms.reviewer: sonua
localization_priority: Normal
ms.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
search.appverid: MET150
description: Learn about the factors to consider before you set up live events in Microsoft Teams. 
appliesto: 
- Microsoft Teams
---

# Plan for live events in Microsoft Teams

When you're planning Teams live events to hold large meetings in your organization, there are several factors that you need to consider before starting to set it all up. 

## Who can create and schedule live events? 
The following prerequisites are required for the user to schedule a Teams live event.

Here are the licenses that must be assigned:  
- An Office 365 Enterprise E1, E3, or E5 license or an Office 365 A3 or A5 license
- A Microsoft Teams license
- A Microsoft Stream license

> [!IMPORTANT]
> The user creating and scheduling a live event must have an Exchange Online mailbox.

It's important to know that an Office 365 license is required to participate in a live event as an authenticated user, but this requirement depends on the production method used:

- **For events produced in Teams**  The user must be assigned a Teams license.
- **For events produced with an external app or device** The user must be assigned a Stream license.

For more information on licensing, see [Microsoft Teams add-on licensing](../teams-add-on-licensing/microsoft-teams-add-on-licensing.md).

The user must have:
- Private meeting scheduling in Teams enabled (*The TeamsMeetingPolicy -AllowPrivateMeetingScheduling parameter = True*).
- Video sharing enabled in Teams meetings (*The TeamsMeetingPolicy -AllowIPVideo parameter = True*).
- Screen sharing enabled in Teams meetings (*The TeamsMeetingPolicy -ScreenSharingMode parameter = EntireScreen*).
- Live event scheduling in Teams enabled (*The TeamsMeetingBroadcastPolicy -AllowBroadcastScheduling parameter = True*).
- Permissions to create live events in Stream (for external app or device production).

> [!IMPORTANT]
> Office 365 guests, federated, and anonymous users can't be invited as producers or presenters in Teams live events. Office 365 guests and federated users can only watch live events anonymously. 
 
## Who can watch live events?

|**Attendee visibility**       |**Teams production**  |**External app or device production**  |
|------------------------------|-----------------|----------------------|
|Public (anonymous users)      |  Yes            |  No                  |
|Guest users                   |  No<sup>1</sup> |  No                  |
|Everyone in federated company |  No<sup>2</sup> |  No                  |
|Everyone in company           |  Yes            |  Yes                 |
|Specific groups / people      |  Yes            |  Yes                 |

<sup>1</sup> Can watch live events if the live event is set up using the **Org-wide** option.<br>
<sup>2</sup> Can only watch live events as anonymous users.

 
## Teams live events and Skype Meeting Broadcast
The following table highlights core capabilities and features offered in live events and how they differ from Skype Meeting Broadcast. 

|**Capability**   |**Skype Meeting Broadcast** |**Events produced in Teams** |**Events produced in external app or device** |
|---------|---------|---------|---------|
|Maximum audience size |10,000 attendees |10,000 attendees* |10,000 attendees* |
|Maximum duration of live event |4 hours |4 hours |4 hours |
|Maximum number of concurrent live events per Office 365 tenant |15  | 15  | 15  |
|Live event creation |   Skype Meeting Broadcast Portal |Teams, Yammer via Teams | Teams, Yammer via Teams, Stream |
|Audience engagement – Yammer |&#x2714; |&#x2714; (integrated experience) |&#x2714; (integrated experience) |
|Audience engagement – Moderated Q & A |&#x2714;  |&#x2714; |&#x2714; |
|Producer client on Windows |&#x2714; (Skype for Business) |&#x2714; (Teams) |&#x2714; (Stream, Teams via Stream Embed) |
|Producer client on Mac |X  | &#x2714; (Teams) |&#x2714; (Stream, Teams via Stream Embed) |
|Attendee count in Producer UI |X  |&#x2714; (Teams) |&#x2714; (Stream, Teams via Stream Embed) |
|Allows multiple presenters |&#x2714; (Skype for Business) |&#x2714; (Teams) |N/A  |
|Invite a presenter during the meeting |&#x2714; (Skype for Business) |X |N/A |
|Presenter join on Web and Mobile |&#x2714; (Skype for Business)  |X |N/A |
|Federated & Guest presenters/attendees |&#x2714; (Skype for Business)  | (coming soon) |N/A |
|Presenter – PSTN access |X |&#x2714; (Teams) |N/A |
|Present a screen |X |&#x2714; (Teams) |N/A |
|Present a PowerPoint (PPT sharing) |&#x2714; |X (mitigated via screen sharing) |N/A |
|Cloud based meeting recording |&#x2714; |&#x2714; |&#x2714; |
|Auto publish recording to Stream |X |X |&#x2714; |
|Live captions and subtitles |&#x2714; |&#x2714; |X |
|Captions in live event recordings |&#x2714; |&#x2714; |&#x2714; |
|Attendee DVR controls (pause, rewind) |&#x2714; |&#x2714; |&#x2714; |
|Partner eCDN Support |&#x2714; (Hive, Kollective, Ramp) |&#x2714; (Hive, Kollective, Ramp) |&#x2714; (Hive, Kollective, Ramp) |
|Post-broadcast attendance report for Producers |&#x2714; |&#x2714; |X |
|Audience Sentiment Analysis – Live voting & polls |&#x2714; (Microsoft Pulse) |X |X |

> [!IMPORTANT]
> The limits that are set might be changed.

## Regional availability
You can use Teams live events in multiple regions across the world. The following information shows availability for event team members and attendees. 

> [!IMPORTANT]
> The region for the event is automatically selected depending on the organizer and the Office 365 organization.

**Available in these regions**
- Americas
- Europe/Africa
- Asia Pacific
- Go Local Canada

**Exclusions and considerations**
- **Go Locals:** United Kingdom, India, Australia, Japan, and other Teams Go Locals are not currently supported.
- **China:** Event team members and attendees will not be able to use Teams live events because Azure CDN is not accessible in China. A workaround is to use a company VPN connection, which gets the client connected to CDN via the customer's corporate network.

## Next steps
Go to [Set up for Teams live events](set-up-for-teams-live-events.md).

### Related topics
- [What are Teams live events?](what-are-teams-live-events.md)
- [Set up for Teams live events](set-up-for-teams-live-events.md)
- [Configure live events settings in Teams](configure-teams-live-events.md)

