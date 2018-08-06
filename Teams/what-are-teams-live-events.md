---
title: What are Teams live events?
author: tonysmith
ms.author: tonysmit
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviwer: tonysmit
description: Learn how Live events enable users to broadcast video and content to large online audiences in Microsoft Teams, Yammer, and Microsoft Stream.  
appliesto: 
- Microsoft Teams
---

# What are Teams live events?
> [!INCLUDE [Preview customer token](includes/preview-feature.md)]

Learn how live events enable users to broadcast video and content to large online audiences in Microsoft Teams, Yammer, and Microsoft Stream.  

## Overview
Live events in Microsoft 365 enable users to broadcast video and content to large online audiences.  Microsoft 365 live events bring live video streaming to a new level, encouraging connection throughout the entire engagement lifecycle with attendees before, during, and after live events. You can create a live event wherever your audience, team, or community resides, using Microsoft Stream, Microsoft Teams or Yammer.  

Microsoft Teams delivers chat-based collaboration, calling, meetings and with live events, you can expand the audience of your meetings. Microsoft Teams live events is an extension of Teams meetings, enabling users to broadcast video and meeting content to a large online audience. These are meant for one-to-many communications where the host of the event is leading the interactions and the audience participation is primarily to view the content shared by host. The attendees can watch the live or recorded event in Yammer, Teams, and/or Microsoft Stream, and can interact with the presenters via moderated Q & A or Yammer conversation. 

Teams live events is considered the next version of Skype Meeting Broadcast and will eventually replace the capabilities provided in Skype Meeting Broadcast. For the public preview release of live events, Microsoft will continue to support Skype Meeting Broadcast, with no disruption in service for new or future events. We encourage you to try out live events in Teams to leverage new features including screen sharing, attendee count, and support for external hardware/software encoders. 

## Key components
The following diagram shows high level components involved in Microsoft 365 live events. 

![Teams live events](media/teams-live-events.png)

### Scheduling
Teams provides the ability for the organizers to create an event with the appropriate attendee permissions, designate event team members, select production method invite attendees. If the live event was created from within a Yammer group, the live event attendees will be able to use Yammer conversation for interacting with the event team. 

### Production
The live events in Microsoft 365 support a spectrum of production scenarios, include a quick start event using web cams or an external encoder event using studio quality equipment. The video input is the foundation of the live events and it can vary from a single webcam to a multi-camera professional video production. Customers can choose these options depending on their project requirements and budget. 
- **Quick start**: The quick start method allows users to produce their live events using Teams meetings. This option is best if you want to use the audio and video devices connected to the PC and/or are inviting remote presenters / panelists for participating in the event. This option allows users to easily use their web cams and share their screen as input into the broadcast. 
- **External encoder**: External encoders allow users to produce their live events directly from an external hardware or software-based encoder with Microsoft Stream. This option is best if you already have studio quality equipment (e.g. media mixers) which support streaming to an RTMP service. This option is typically used in large scale events such as executive town halls – where a single stream from a media mixer is broadcast to the audience. 

### Streaming platform
This is made up of the following pieces:

#### Azure Media Services
[Azure Media Services](https://docs.microsoft.com/en-us/azure/media-services/previous/) gives you broadcast-quality video streaming services to reach larger audiences on today’s most popular mobile devices. Media Services enhances accessibility, distribution, and scalability, and makes it easy and cost-effective to stream content to your local and worldwide audiences — all while protecting your content.

#### Azure Content Delivery Network (CDN)
Once your stream goes live, it is delivered through the [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/en-us/azure/cdn/). Azure Media Services provides integrated CDN for streaming-endpoints. This allows for your streams to be viewed worldwide with no buffering. 

### Enterprise Content Delivery Network (eCDN) 
The goal of eCDN is to take the video content from the internet and distribute the content throughout the enterprise without impacting the network performance. You can use the following certified partners to optimize your network for live events: 
- Hive
- Kollective
- Ramp (coming soon to Quick Start)

### Attendee Experience
The attendee experience is the most important aspect of live events and it is critical that the attendees can participate in the live event without issues. The attendee experience uses Azure Media Player and works across desktop, browser, and mobile (iOS, Android). Office 365 provides Yammer and Teams as two collaboration hubs and the live attendee experience is integrated into these collaboration tools. The external encoder based live events can also be accessed by attendees in the Microsoft Stream portal.

## Prerequisites

### Who can create live events
The following prerequisites are required for the user to schedule a live event in the Preview timeframe:  
- User has an Office 365 Enterprise E3 or E5 license. 
- User is enabled for Microsoft Teams, Skype for Business Online, and Microsoft Stream.
- User is enabled for private meeting scheduling in Teams (TeamsMeetingPolicy-AllowPrivateMeetingScheduling is set to True).
- User is enabled for live event scheduling in Teams (TeamsMeetingBroadcastPolicy-AllowBroadcastScheduling is set to True).
- User has permissions to create live events in Microsoft Stream (for external encoder production).

> [!NOTE]
> Office 365 guests, federated, and anonymous users cannot be invited as producers or presenters in Teams live events. 
 
### Who can watch live event
Review the table below to see who can participate in a live event. 

|**Attendee visibility**           |**Quick start** |**External encoder**  |
|------------------------------|-------------|------------------|
|Public (anonymous users)      |  Yes        |  No              |
|Guest users*                   |  No         |  No              |
|Everyone in federated company* |  No         |  No              |
|Everyone in company           |  Yes        |  Yes             |
|Specific groups / people      |  Yes        |  Yes             |
*Guest and federated users can join as anonymous live event attendees.

An Office 365 license is required to participate in a live event as an authenticated user, depending on the production method.

- **For Quick start production**: The user must be a Teams user.
- **For External encoder production**: The user must be a Stream user.
 
## Capabilities
The following table highlights core capabilities offered in live events and how they differ from Skype Meeting Broadcast. 

|Capability   |Skype Meeting Broadcast |Teams live events (Quick start) |Teams live events (External encoder) |
|---------|---------|---------|---------|
|Maximum audience size |10,000 attendees |10,000 attendees* |10,000 attendees* |
|Live event creation |   Skype Meeting Broadcast Portal |Teams, Yammer via Teams | Teams, Yammer via Teams, Stream |
|Audience engagement – Yammer |&#x2714; |&#x2714; (integrated experience) |&#x2714; (integrated experience) |
|Audience engagement – Moderated Q & A |&#x2714;  |&#x2714; |&#x2714; |
|Producer client on Windows |&#x2714; (Skype for Business) |&#x2714; (Teams) |&#x2714; (Stream, Teams via Stream Embed) |
|Producer client on Mac |X  | &#x2714; (Teams) |&#x2714; (Stream, Teams via Stream Embed) |
|Attendee count in Producer UI |X  |&#x2714; (Teams) |&#x2714; (Stream, Teams via Stream Embed) |
|Allows multiple presenters |&#x2714; (Skype for Business) |&#x2714; (Teams) |N/A  |
Invite a presenter during the meeting |&#x2714; (Skype for Business) |X |N/A |
|Presenter join on Web and Mobile |&#x2714; (Skype for Business)  |X |N/A |
|Presenter – PSTN access |X |&#x2714; (Teams) |N/A |
|Present a screen |X |&#x2714; (Teams) |N/A |
|Present a PowerPoint (PPT Sharing) |&#x2714; |X (mitigated via screen sharing) |N/A |
|Cloud based meeting recording |&#x2714; |&#x2714; |&#x2714; |
|Auto Publish Recording to Microsoft Stream |X |X |&#x2714; |
|Real Time Captions and Translation |&#x2714; |&#x2714; (coming soon) |X |
|Captions in live event recordings |&#x2714; |&#x2714; (coming soon) |&#x2714; |
|Attendee DVR controls (pause, rewind) |&#x2714; |&#x2714; |&#x2714; |
|Partner eCDN Support |&#x2714; (Hive, Kollective, Ramp) |&#x2714; (coming soon) |&#x2714; (Hive, Kollective, Ramp) |
|Post-broadcast attendance report for Producers |&#x2714; |&#x2714; (coming soon) |X |
|Audience Sentiment Analysis – Live voting & polls |&#x2714; (Microsoft Pulse) |X |X |

*The limits are during preview and subject to change 

## Planning & Setup
This article explains how you can setup users with Teams live events in your organization.

1. Check [regional availability for Teams live events](#configure-live-events) to understand the regions live events are currently available in.
2. If you haven’t done so already, set up [Skype for Business Online](https://docs.microsoft.com/en-us/SkypeForBusiness/set-up-skype-for-business-online/set-up-skype-for-business-online?redirectSourcePath=%252fen-us%252farticle%252fset-up-skype-for-business-online-40296968-e779-4259-980b-c2de1c044c6e) for your organization.
3. If you have attendees joining from within the corporate network, consider onboarding and [setting up a Microsoft-recommended eCDN provider](#set-up-ecdn-provider-for-teams-live-events) to optimize your network bandwidth. 
4. Ensure you have correct license assignments for [who can create live events](#who-can-create-live-events) and [who can watch live events](#who-can-watch-live-event). 
5. [Enable live event scheduling](#enable-live-event-scheduling-for-the-user) for the users who should be able to create live events in your company. This is required for both quick start & external encoder events. 
6. For external encoder events, [enable users for live events creation in Microsoft Stream Admin Portal](#enable-microsoft-stream-for-users-in-the-organization).  

### Regional availability for Teams live events
You can use Teams live events in multiple regions. The following information shows availability for event team members and attendees. The region for the event is automatically selected depending on the organizer and the Office 365 tenant.

#### Regions available
- Americas
- Europe/Africa
- Asia Pacific

#### Exclusions
- Go Locals
  - UK, India, and other Microsoft Teams Go Locals are not currently supported.
- Go Local - Canada 
  - In Preview, customers can create events but their data will be homed in North America region.
- China
  - Event team members and attendees will not be able to use Teams live events because Azure CDN is not accessible in China. A workaround is to use a company VPN connection, which gets the client connected to CDN via the customer's corporate network.

### Set up your network for live events in Microsoft Teams
The quick start live events require you to [prepare your organization's network for Microsoft Teams](https://docs.microsoft.com/en-us/microsoftteams/prepare-network).  

For both quick start and external encoder live events, go to [Office 365 URLs and IP address ranges](https://docs.microsoft.com/en-us/microsoftteams/office-365-urls-ip-address-ranges) for a detailed and up-to-date list of the URLs, IP addresses, ports, and protocols that must be correctly configured for Teams and Stream. Microsoft is continuously improving the Office 365 service and adding new functionality, which means the required ports, URLs, and IP addresses may change over time. We recommend that you subscribe via RSS to receive notifications when this information is updated or changed.

### Set up eCDN provider for live events in Microsoft Teams 
Playback of live event videos uses adaptive bitrate streaming (ABR) but it is a unicast stream, meaning every viewer is getting their own video stream from the internet. For live events or videos sent out to large portions of your organization, there could be a significant amount of internet bandwidth consumed by viewers.  For organizations that want to reduce this internet traffic for live events, live events solutions are integrated with Microsoft's trusted video delivery partners offering software defined networks (SDNs) or enterprise content delivery networks (eCDNs). These SDN / eCDN platforms enable organizations to optimize network bandwidth without sacrificing end user viewing experiences. Our partners can help enable a more scalable and efficient video distribution across your enterprise network.

#### Purchase & setup your solution outside of Microsoft Teams
Get expert help with scaling video delivery by leveraging Microsoft’s trusted video delivery partners.  Before you can enable a video delivery provider to be used with Microsoft Teams you must purchase and setup the SDN/eCDN solution outside and separate from Microsoft Teams.

The following SDN/eCDN solutions are pre-integrated and can be setup to be used with Microsoft Stream. See information from the providers below:

Hive Streaming provides a simple and powerful solution for live and on-demand enterprise video distribution. Hive is a software-based solution that requires no additional hardware or bandwidth and provides a secure way to enable thousands of simultaneous video viewers without impact to your network. For customers looking to understand the impact video is having on their network prior to purchasing an SDN/eCDN solution, Hive Streaming also provides a browser-based analytics solution for Microsoft customers. [Learn more](https://www.hivestreaming.com/partners/integration-partners/microsoft/)
 
Kollective's cloud-based, smart peering distribution platform leverages your existing network infrastructure to deliver content, in many forms, (live streaming video, on-demand video, software updates, security patches, etc.) faster, more reliably and with less bandwidth. Our secure platform is trusted by the world’s largest financial institutions and with no additional hardware, setup and maintenance are easy. [Learn more](http://www.kollective.com)
 
Ramp OmniCache provides next-generation network distribution and ensures seamless delivery of video content across global WANs, helping event producers optimize network bandwidth and support successful live event broadcasts and on-demand streaming. The support for Ramp OmniCache for quick start live events is coming soon.  [Learn more](http://www.ramp.com) 
 
[!NOTE] Your chosen eCDN solution is subject to the selected 3rd party provider’s terms of service and privacy policy, which will govern your use of the eCDN provider’s solution. Your use of the eCDN provider’s solution will not be subject to the Microsoft volume licensing terms or Online Services Terms. If you do not agree to the 3rd party provider’s terms, then do not enable the eCDN solution in Microsoft Teams. 

#### Configure eCDN for "Quick start" live events 
You can configure eCDN provider for live events in Microsoft Teams via PowerShell. Note: only a single eCDN provider can be configured for the tenant at any given time. 

**Configure Hive eCDN provider** 

You can use [Set-CsTeamsMeetingBroadcastConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/set-csteamsmeetingbroadcastconfiguration?view=skype-ps) PowerShell cmdlet to configure eCDN provider. 
1. Obtain license ID and API template URL from your Hive contact. 
2. Run the following PowerShell cmdlet
```
Set-CsTeamsMeetingBroadcastConfiguration -AllowSdnProviderForBroadcastMeeting $True -SdnProviderName hive -SdnLicenseId {license ID GUID provided by Hive} -SdnApiTemplateUrl “{API template URL provided by Hive}”
```

**Configure Kollective eCDN provider** 

You can use [Set-CsTeamsMeetingBroadcastConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/set-csteamsmeetingbroadcastconfiguration?view=skype-ps) PowerShell cmdlet to configure eCDN provider. 
1. Obtain API token and API template URL from your Kollective contact. 
2. Run the following PowerShell cmdlet
```
Set-CsTeamsMeetingBroadcastConfiguration -AllowSdnProviderForBroadcastMeeting $True -SdnProviderName kollective -SdnApiTemplateUrl "{API template URL provided by Kollective}" -SdnApiToken {API token GUID provided by Kollective}
```

#### Configure eCDN for "External encoder" live events 
If you plan to create live events that use external encoders, you will need to [configure your eCDN provider with Microsoft Stream](https://docs.microsoft.com/stream/network-caching) as well. 

### Enable live event scheduling for the user
The live event scheduling is enabled by default for a Teams user.  

Use the setting AllowBroadcastScheduling in TeamsMeetingBroadcastPolicy in Teams PowerShell to control whether the user can create live events in Teams or not. You can learn more about managing TeamsMeetingBroadcastPolicy with Office 365 PowerShell [here](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell).

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

### Enable creation of external encoder-based live events for users

#### Enable Microsoft Stream for users in the organization
Microsoft Stream is available as part of eligible Office 365 subscriptions or as a standalone service. See [Stream licensing overview](https://docs.microsoft.com/en-us/stream/license-overview) for more details. Note Microsoft Stream is not included in Business Essentials or Business Premium plans.  

Learn more about how you can [assign licenses to users in Office 365](https://support.office.com/article/Assign-licenses-to-users-in-Office-365-for-business-997596B5-4173-4627-B915-36ABAC6786DC) so that users can access Microsoft Stream. Ensure Microsoft Stream is not blocked for the users as defined in [this article](https://docs.microsoft.com/en-us/stream/disable-user-organization).

#### Ensure users have live event creation permission in Microsoft Stream
By default, everyone in the company can create content in Stream, once Stream is enabled and a license is assigned to the user. Microsoft Stream administrator can [restrict employees for creating content](https://docs.microsoft.com/en-us/stream/restrict-uploaders) in Stream. The users who are in this restricted list will not be able to record meetings.

#### Ensure live event organizers have consented to the company policy set by Stream admin
If a Microsoft Stream administrator has [set up a company guidelines policy](https://docs.microsoft.com/en-us/stream/company-policy-and-consent) and requires employees to accept this policy before saving content, then users must do so before creating a live event (with External Encoder production) in Microsoft Teams. Before you rollout the live events feature in the organization, make sure users who will be creating these live events have consented to the policy. 

## Configure live events

### Set up event support link (coming soon)
This is the link that will be shown to the live event attendees. 

PowerShell

In Windows PowerShell, run the following cmdlet:
```
Set-CsTeamsMeetingBroadcastConfiguration -SupportURL “{your URL}” 
```
### Configure attendee visibility options
This allows live event organizers to create events with appropriate attendee visibility.

|**Values**  |**Behavior**  |
|---------|---------|
|Everyone     |The user has an option to create live events with the following attendee visibility: Public, Everyone in company, and Specific people. |
|EveryoneInCompany     |The user has an option to create live events with the following attendee visibility: Everyone in company and Specific people. The user cannot create live events that can be attended by anonymous users.|
|InvitedUsers |The user can only create live events that are limited to specific people as entered by the event organizer. The user cannot create live events with Public and Everyone in company authentication. |

PowerShell

Use the setting BroadcastAttendeeVisibility in TeamsMeetingBroadcastPolicy in PowerShell to control whether the users can schedule broadcast events that can be watched by anonymous attendees. You can learn more about managing TeamsMeetingBroadcastPolicy with Office 365 PowerShell here.  

Unless you have assigned a custom policy to the users, the users get Global policy, which has default set to EveryoneInCompany. 
 
In Windows PowerShell, run the following cmdlet to allow users to create anonymous events in the global policy:
```
Set-CsTeamsMeetingBroadcastPolicy -Identity Global -BroadcastAttendeeVisibility Everyone  
```
### Configure recording options
> [!NOTE]
> This option is applicable to events that use Quick start production method only.

This allows admins to control whether the live events are always recorded, never recorded or whether the event organizer can decide to record the event or not.  

|**Values**  |**Behavior**  |
|---------|---------|
|Always enabled |The live events organized by this user are always recorded. User doesn’t have an option to override. If the live event is recorded, the event team members are able to download the recording after the event and the attendees can watch the event after the event is over. |
|AlwaysDisabled |The live events organized by this user are never recorded. User doesn’t have an option to override. If the live event is recorded, no recording is created for the event team members and the attendees cannot watch the event after it is over. |
|UserOverride |User can decide whether the live event is recorded so a recording file can be created for the event team members and attendees can watch the event after the event is over. |

PowerShell

Use the setting BroadcastRecordingMode in TeamsMeetingBroadcastPolicy in PowerShell to control recording options of the live events created by the live event organizer.

In Windows PowerShell, run the following cmdlet to update recording mode in the global policy:
```
Set-CsTeamsMeetingBroadcastPolicy -Identity Global -BroadcastRecordingMode AlwaysDisabled 
```
### Configure real-time transcription and translation in Teams live events (coming soon)
> [!NOTE]
> This option is applicable to events that use Quick start production method only.

This allows live event organizers to turn on real-time captions and translation for the live event attendees. 

PowerShell

Use the setting AllowBroadcastTranscription in TeamsMeetingBroadcastPolicy in PowerShell to control whether the live event attendees will be able to see transcription and translation. You can learn more about managing TeamsMeetingBroadcastPolicy with Office 365 PowerShell here.  

Unless you have assigned a custom policy to the users, the users get Global policy, which has transcription & translation disabled by default.

In Windows PowerShell, run the following cmdlet to turn transcription and translation on for event attendees in the global policy:
```
Set-CsTeamsMeetingBroadcastPolicy -Identity Global -AllowBroadcastTranscription $true 
```
## Self-service administration tools 
Although Microsoft directly controls all Office 365 Online data centers and is responsible for overall system performance, it can control only a portion of the elements that combine to provide the total experience for Office 365 users. Organizations themselves are responsible for the network connections to the data centers, the customer’s wide area network (WAN), and the customer's local area networks (LANs). Additionally, they are in charge of user devices and their configuration. They are also responsible for maintaining the required licensing per user for any desired feature, including, but not limited to, the ability to manage these features, for as long as the user needs access to the feature.

Customers can use the following tools to manage a variety of Teams live events related tasks.
- [Microsoft Office 365 admin center](https://technet.microsoft.com/en-us/library/exchange-online-administration-and-management.aspx?f=255&MSPPError=-2147217396#BKMK_Office365admincenterl)
- [Microsoft Teams and Skype for Business Online admin center](https://technet.microsoft.com/en-us/library/exchange-online-administration-and-management.aspx?f=255&MSPPError=-2147217396#BKMK_ExchangeAdministrationCenter)
- Microsoft Stream admin center
- [Remote Windows PowerShell](https://technet.microsoft.com/en-us/library/exchange-online-administration-and-management.aspx?f=255&MSPPError=-2147217396#BKMK_RemoteWindowsPowerShell)

### Want to know more about Windows PowerShell?
- When it comes to Windows PowerShell, it's all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Office 365 and Skype for Business Online using a single point of administration that can simplify your daily work, when you have multiple tasks to do. To get started with Windows PowerShell, see these topics:
  - [An introduction to Windows PowerShell and Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525039)
  - [Why you need to use Office 365 PowerShell](https://go.microsoft.com/fwlink/?LinkId=525041)

- Windows PowerShell has many advantages in speed, simplicity, and productivity over only using the Office 365 admin center such as when you are making setting changes for many users at one time. Learn about these advantages in the following topics:
  - [Best ways to manage Office 365 with Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=525142)
  - [Using Windows PowerShell to manage Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525453)
  - [Using Windows PowerShell to do common Skype for Business Online management tasks](https://go.microsoft.com/fwlink/?LinkId=525038)


### Related topics: 

- [Live events across Microsoft 365 in Yammer, Microsoft Teams, and Microsoft Stream](https://docs.microsoft.com/stream/live-event-m365)
- [Live events in Microsoft Teams](https://support.office.com/article/microsoft-teams-live-event-overview-d077fec2-a058-483e-9ab5-1494afda578a)
- [Live events in Yammer](https://support.office.com/article/live-events-in-yammer-4ece0ee2-c268-4636-bf2a-16e454befe57)
- [Live events in Microsoft Stream](https://review.docs.microsoft.com/stream/live-event-overview)
