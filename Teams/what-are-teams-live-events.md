---
title: What are Teams live events?
author: TonySmith
ms.author: tonysmit
manager: serdars
ms.date: 7/10/2018
ms.topic: article
ms.service: msteams
ms.reviwer: tonysmit
description: Learn how Live events enable users to broadcast video and content to large online audience in Microsoft Teams, Yammer, and Microsoft Stream.   
appliesto: 
- Microsoft Teams
---

# What are Teams live events?
**Summary**: Learn how Live events enable users to broadcast video and content to large online audience in Microsoft Teams, Yammer, and Microsoft Stream.

## Overview
Microsoft Teams delivers chat-based collaboration, calling, meetings and with live events, you can expand the audience of your meetings.  Microsoft Teams live events is an extension of Teams meetings, enabling users to broadcast video, content and meeting to a large online audience.   These are meant for one to many communications where the host of the event is leading the interactions and the audience participation is primarily to view the content shared by host.  The attendees can watch the live or recorded event in Yammer, Teams and/or Microsoft Stream, and can interact with the presenters via moderated Q & A or Yammer conversation. 

Teams live events is considered the next version of Skype Meeting Broadcast and will eventually replace the capabilities provided in Skype Meeting Broadcast.  For the public preview release of live events, Microsoft will continue to support Skype Meeting Broadcast, with no disruption in service for new or future events. We encourage you to try out live event in Teams to leverage new features including screen sharing, real-time attendee count and support for external hardware/software encoders.  Further information on the transition plan for Skype Meeting Broadcast will be shared in later half of calendar year 2018.  

Related: [Microsoft Teams live events overview](https://support.office.com/en-us/article/microsoft-teams-live-event-overview-d077fec2-a058-483e-9ab5-1494afda578a?ui=en-US&rs=en-US&ad=US)

## Key components
The following diagram shows high level components involved in Microsoft 365 live events. 

### Scheduling
Teams provides ability for the organizers to create an event with the appropriate attendee permissions, designate event team members, select production method invite attendees.  If the live event was created from within a Yammer group, the live event attendees will be able to use Yammer conversation for interacting with the event team. 

### Production
The live events in Microsoft 365 support a spectrum of production scenarios, include a quick start event using web cams or an external encoder event using studio quality equipment.  The video input is the foundation of the live events and it can vary from a single webcam to a multi-camera professional video production.  Customers can choose these options depending on their project requirements and budget. 
- **Quick start**: The quick start method allows user to produce their live events using Teams meetings.   This option is best if you want to use the audio and video devices connected to the PC and/or are inviting remote presenters / panelists for participating in the event.  This option allows users to easily use their web cams and share their screen as input into the broadcast.  
- **External encoder (coming soon)**: External encoders allow users to produce their live events directly from an external hardware or software-based encoder with Microsoft Stream.  This option is best if you already have a studio quality equipment (e.g. media mixers) which supports streaming to an RTMP service.  This option is typically used in large scale events such as executive town halls – where a single stream from a media mixer is broadcasted to the audience.  

### Streaming platform
This is made up of the following pieces:

#### Microsoft Stream Live 
The Live video capabilities in Microsoft Stream enable live streaming from an external hardware or software-based encoder.  

#### Azure Media Services
[Azure Media Services](https://docs.microsoft.com/en-us/azure/media-services/previous/) gives you broadcast-quality video streaming services to reach larger audiences on today’s most popular mobile devices. Media Services enhances accessibility, distribution, and scalability, and makes it easy and cost-effective to stream content to your local and worldwide audiences—all while protecting your content.

#### Azure Content Delivery Network (CDN)
Once your stream goes live, it is delivered through the Azure Content Delivery Network (CDN).  Azure Media Services provides integrated CDN for streaming-endpoints.  This allows for your streams to be viewed worldwide with no buffering. 

### Enterprise CDN (eCDN) 
The goal of eCDN is to take the video content from the internet and distribute the content throughout the enterprise without impacting the network performance.  You can use the following certified partners to optimize your network for live events: 
- Hive
- Kollective
- Ramp

### Attendee Experience
The attendee experience is the most important aspect of live events and it is critical that the attendees can participate in the live event without issues.  The attendee experience uses Azure Media Player and works across desktop, browser and mobile (iOS, Android).   Microsoft 365 provides Yammer and Teams as two collaboration hubs and the live attendee experience is integrated into these collaboration tools.  The external encoder based live events can also be accessed by attendees in the Microsoft Stream portal.

## Prerequisites

### Who can create live events
The following prerequisites are required for the user to schedule live event in Preview timeframe:   
- User has an Office 365 Enterprise E3 or E5 license. 
- User is enabled for Microsoft Teams, Skype for Business Online & Microsoft Stream.
- User is enabled for private meeting scheduling in Teams (TeamsMeetingPolicy-AllowPrivateMeetingScheduling is set to True).
- User is enabled for live event scheduling in Teams (TeamsMeetingBroadcastPolicy-AllowBroadcastScheduling).
- User has permissions to create live events in Microsoft Stream (for external encoder production).
 
### Who can watch live event
In the initial release, the viewing of the live event is limited to the authenticated (Quick start and external encoder) and anonymous users (Quick start only). O365 guests and federated users cannot watch live events. 
- **Quick start**: Anonymous users and authenticated Office 365 users with any license that includes Teams.
- **External encoder**: Any authenticated Office 365 users with any license that includes Microsoft Stream.
 

|Attendee visibility           |Quick start  |External encoder  |
|------------------------------|-------------|------------------|
|Public                        |  Yes        |  No              |
|Guest users                   |  No         |  No              |
|Everyone in federated company |  No         |  No              |
|Everyone in company           |  Yes        |  Yes             |
|Specific groups / people      |  Yes        |  Yes             |

## Capabilities
The following table highlights core capabilities offered in Live events and how they differ from Skype Meeting Broadcast. 

|Capability   |Skype Meeting Broadcast |Teams live events (Quick start) |Teams live events (External encoder) |
|---------|---------|---------|---------|
|Maximum audience size |10,000 internal or external attendees |10,000 internal or external attendees |10,000 internal or external attendees |
|Live event creation |   Skype Meeting Broadcast Portal |Teams, Yammer via Teams | Teams, Yammer via Teams, Stream |
|Audience engagement – Yammer |&#x2714 |&#x2714 (integrated experience) |&#x2714 (integrated experience) |
|Audience engagement – Moderated Q & A |&#x2714  |&#x2714 |&#x2714 |
|Producer client on Windows |&#x2714 (Skype for Business) |&#x2714 (Teams) |&#x2714 (Stream, Teams via Stream Embed) |
|Producer client on Mac |X  | &#x2714 (Teams) |&#x2714 (Stream, Teams via Stream Embed) |
|Live attendee count in Producer UI |X  |&#x2714 (Teams) |&#x2714 (Stream, Teams via Stream Embed) |
|Allows multiple presenters |&#x2714 (Skype for Business) |&#x2714 (Teams) |N/A  |
Invite a presenter during the meeting |&#x2714 (Skype for Business) |X |N/A |
|Presenter join on Web and Mobile |&#x2714 (Skype for Business)  |X |N/A |
|Presenter – PSTN access |X |&#x2714 (Teams) |N/A |
|Present a screen |X |&#x2714 (Teams) |N/A |
|Present a PowerPoint (PPT Sharing) |&#x2714 |X (mitigated via screen sharing) |N/A |
|Cloud based meeting recording |&#x2714 |&#x2714 |&#x2714 |
|Auto Publish Recording to Microsoft Stream |X |X |&#x2714 |
|Real Time Captions and Translation |&#x2714 |&#x2714 (coming soon) |X |
|Captions in live event recordings |&#x2714 |&#x2714 |&#x2714 |
|Attendee DVR controls (pause, rewind) |&#x2714 |&#x2714 |&#x2714 |
|Partner eCDN Support |(Hive, Kollective, Ramp) |(Hive, Kollective, Ramp) |(Hive, Kollective, Ramp) |
|Post-broadcast attendance report for Producers |&#x2714 |&#x2714 |X |
|Audience Sentiment Analysis – Live voting & polls |&#x2714 (Microsoft Pulse) |X |X |

## Planning & Setup
This article explains how you can setup users with Teams live events in your organization.

### Regional availability for Teams live events
Same as Skype Meeting Broadcast – minus Canada. 

### Set up your network for Teams live events 
Keep the content you have in [Set up your network for Teams live events](https://review.docs.microsoft.com/en-us/MicrosoftTeams/teams-live-events-set-up-your-network?branch=teams-live-events). 

### Set up eCDN provider
TBD

#### Integrate with Hive

#### Integrate with Kollective

#### Integrate with Ramp

### Enable live event scheduling for the user
The live event scheduling is enabled by default for a Teams user.  

Use the setting AllowBroadcastScheduling in TeamsMeetingBroadcastPolicy in Teams PowerShell to control whether the user can create live events in Teams or not.  You can learn more about managing TeamsMeetingBroadcastPolicy with Office 365 PowerShell [here](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell).

 Unless you have assigned a custom policy to the users, the users get Global policy, which has recording enabled by default. 

 For a user to fallback to Global policy, use the following cmdlet to remove a specific policy assignment for a user.
```
Grant-CsTeamsMeetingBroadcastPolicy -Identity {user} -PolicyName $null -Verbose
```
To change value of AllowBroadcastScheduling in Global policy, use the following cmdlet:
```
Set-CsTeamsMeetingBroadcastPolicy -Identity Global -AllowBroadcastScheduling $false
```
#### Scenarios
**I want all users in my company to be able to create live events.**
1. Confirm Global CsTeamsMeetingBroadcastPolicy has AllowBroadcastScheduling = True.
2. Confirm all users have the Global CsTeamsMeetingBroadcastPolicy OR one of the CsTeamsMeetingBroadcastPolicy policies with AllowBroadcastScheduling = True.

**I want the majority of my users to be able to create live events, but I want to selectively disable specific users who are not allowed to.**
1. Confirm Global CsTeamsMeetingBroadcastPolicy has AllowBroadcastScheduling = True.
2. Confirm majority of users have the Global CsTeamsMeetingBroadcastPolicy OR one of the CsTeamsMeetingBroadcastPolicy policies with AllowBroadcastScheduling = True.
3. Confirm all other users have been granted one of the CsTeamsMeetingBroadcastPolicy policies with AllowBroadcastScheduling = False.

**I want live event scheduling to be 100% disabled.**
1. Confirm Global CsTeamsMeetingBroadcastPolicy has AllowBroadcastScheduling = False.
2. Confirm all users have been granted the Global CsTeamsMeetingBroadcastPolicy OR one of the CsTeamsMeetingBroadcastPolicy policies with AllowBroadcastScheduling = False.

**I want live events to be disabled for majority of the users, but selectively enable specific users for live events.** 
1. Confirm Global CsTeamsMeetingBroadcastPolicy has AllowBroadcastScheduling = False.
2. Confirm the majority of users have been granted the Global CsTeamsMeetingBroadcastPolicy OR one of the CsTeamsMeetingBroadcastPolicy policies with AllowBroadcastScheduling = False.
3. Confirm all other users have been granted one of the CsTeamsMeetingBroadcastPolicy policies with AllowBroadcastScheduling = True.

### Enable Microsoft Stream for users in the organization
Microsoft Stream is available as part of eligible Office 365 subscriptions or as a standalone services. See [Stream licensing overview](https://docs.microsoft.com/en-us/stream/license-overview) for more details. Note Microsoft Stream is not included in Business Essentials or Business Premium plans.  

Learn more about how you can [assign licenses to users in Office 365](https://support.office.com/article/Assign-licenses-to-users-in-Office-365-for-business-997596B5-4173-4627-B915-36ABAC6786DC) so that users can access Microsoft Stream.  Ensure Microsoft Stream is not blocked for the users as defined in this article.

### Ensure users have upload video permissions in Microsoft Stream
By default, everyone in the company can create content in Stream, once Stream is enabled and license is assigned to the user. Microsoft Stream administrator can [restrict employees for creating content](https://docs.microsoft.com/en-us/stream/restrict-uploaders) in Stream. The users who are in this restricted list will not be able to record meetings.

If a Microsoft Stream administrator has a [setup company guideline policy](https://docs.microsoft.com/en-us/stream/company-policy-and-consent) and requires employees to accept this policy before saving content, then users must do so before creating a live event (with External Encoder production) in Microsoft Teams. Before you rollout live events feature in the organization, make sure users who will be creating these live events have consented to the policy. 

## Configure live events

### Setup event support link
This is the link that will be shown to the live event attendees. 
In Windows PowerShell, run the following cmdlet:
```
Set-CsTeamsMeetingBroadcastConfiguration -SupportURL “{your URL}” 
```
### Enable anonymous access in Teams live events
> [!NOTE]
> This option is applicable to events that use Quick start production method only.

This allows live event organizers to create events with external anonymous participants.   

PowerShell
Use the setting BroadcastAttendeeVisibility in TeamsMeetingBroadcastPolicy in PowerShell to control whether the users can schedule broadcast events that can be watched by anonymous attendees.  You can learn more about managing TeamsMeetingBroadcastPolicy with Office 365 PowerShell here.

Unless you have assigned a custom policy to the users, the users get Global policy, which has anonymous access disabled by default.

### Configure recording options
> [!NOTE]
> This option is applicable to events that use Quick start production method only.

This allows admins to control whether the live events are always recorded, never recorded or whether event organizer can decide to record the event or not.  

|Values  |Behavior  |
|---------|---------|
|Always enabled |The live events organized by this user are always recorded.  User doesn’t have an option to override.  If the live event is recorded, the event team members are able to download the recording after the event and the attendees can watch the event after the event is over. |
|AlwaysDisabled |The live events organized by this user are never recorded.  User doesn’t have an option to override.  If the live event is recorded, no recording is created for the event team members and the attendees cannot watch the event after it is over. |
|UserOverride |User can decide whether the live event is recorded so a recording file can be created for the event team members and attendees can watch the event after the event is over. |

PowerShell
Use the setting BroadcastRecordingMode in TeamsMeetingBroadcastPolicy in PowerShell to control recording options of the live events created by the live event organizer.  You can learn more about managing TeamsMeetingBroadcastPolicy with Office 365 PowerShell here.  

### Enable real-time transcription and translation in Teams live events (coming soon)
> [!NOTE]
> This option is applicable to events that use Quick start production method only.

This allows live event organizers to turn real-time captions and translation for the live event attendees. 

PowerShell
Use the setting AllowBroadcastTranscription in TeamsMeetingBroadcastPolicy in PowerShell to control whether the live event attendees will be able to see   You can learn more about managing TeamsMeetingBroadcastPolicy with Office 365 PowerShell here.  

Unless you have assigned a custom policy to the users, the users get Global policy, which has transcription & translation disabled by default.

## Self-service administration tools 
Although Microsoft directly controls all Office 365 Online data centers and is responsible for overall system performance, it can control only a portion of the elements that combine to provide the total experience for Office 365 users. Organizations themselves are responsible for the network connections to the data centers, the customer’s wide area network (WAN), and the customer's local area networks (LANs). Additionally, they are in charge of user devices and their configuration.  They are also responsible for maintaining the required licensing per user for any desired feature, including, but not limited to, the ability to manage these features, for as long as the user needs access to the feature.

Customers can use the following tools to manage a variety of Teams live events related tasks.
- [Microsoft Office 365 admin center](https://technet.microsoft.com/en-us/library/exchange-online-administration-and-management.aspx?f=255&MSPPError=-2147217396#BKMK_Office365admincenterl)
- [Microsoft Teams and Skype for Business Online admin center](https://technet.microsoft.com/en-us/library/exchange-online-administration-and-management.aspx?f=255&MSPPError=-2147217396#BKMK_ExchangeAdministrationCenter)
- Microsoft Stream admin center
- [Remote Windows PowerShell](https://technet.microsoft.com/en-us/library/exchange-online-administration-and-management.aspx?f=255&MSPPError=-2147217396#BKMK_RemoteWindowsPowerShell)

### Want to know more about Windows PowerShell?
When it comes to Windows PowerShell, its all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Office 365 and Skype for Business Online using a single point of administration that can simplify your daily work, when you have multiple tasks to do. To get started with Windows PowerShell, see these topics:
- [An introduction to Windows PowerShell and Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525039)
- [Why you need to use Office 365 PowerShell](https://go.microsoft.com/fwlink/?LinkId=525041)

Windows PowerShell has many advantages in speed, simplicity, and productivity over only using the Office 365 admin center such as when you are making setting changes for many users at one time. Learn about these advantages in the following topics:
- [Best ways to manage Office 365 with Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=525142)
- [Using Windows PowerShell to manage Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525453)
- [Using Windows PowerShell to do common Skype for Business Online management tasks](https://go.microsoft.com/fwlink/?LinkId=525038)

### Manage live event resources
The live event organizer can manage the resources of the live event in Teams and Stream. 

|Live event resources  |Quickstart  |External encoder  |
|---------|---------|---------|
|Recording | Yes  | Yes  |
|Q & A Report | Yes  | Yes  |
|Attendee Report | No  | No  |
|Transcript  | Yes  | Yes  |

#### Recording
TO DO

#### Attendee Report
TO DO

#### Q & A Report
TO DO

#### Transcript
TO DO

The live event recordings are considered tenant owned content.  If the owner of the recording leaves the company, the admin can open the live event video URL in Microsoft Stream in admin mode.  The admin can delete the recording, update any recording metadata or change permissions for the recording video. Learn more about [admin capabilities in Stream](https://docs.microsoft.com/en-us/stream/manage-content-permissions).