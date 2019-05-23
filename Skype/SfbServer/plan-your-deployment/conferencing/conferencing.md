---
title: "Plan for conferencing in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 10add1ea-d693-406c-9dc9-853df0ab05da
description: "Summary: Read this topic to learn about conferencing features and capabilities in Skype for Business Server."
---

# Plan for conferencing in Skype for Business Server
 
**Summary:** Read this topic to learn about conferencing features and capabilities in Skype for Business Server.
  
Conferencing in Skype for Business Server allows users to meet and hold conferences online using their Skype for Business client instead of everyone getting together in the same room. Meeting participants can connect to a meeting with their Skype for Business client for a full audio and video experience, or dial in to a conference using a phone. Conferences also support instant messaging, desktop and application sharing, and interactive white boards.
  
This topic includes the following sections:
  
- Conferencing features and capabilities
    
- Conferencing components
    
- Conferencing policies
    
- Support for large meetings
    
- Determine your organization's needs
    
## Conferencing features and capabilities

There are four types of conferencing available in Skype for Business Server: web conferencing, audio and video (A/V) conferencing, dial-in conferencing, and instant message (IM) conferencing. 
  
You can choose to enable all conferencing types, or to use only one type, depending on your needs. For example, you could enable all types, including dial-in conferencing, to allow users who are not able to join a conference with a Skype for Business client to call in and participate in the meeting audio from a telephone. When you deploy Skype for Business Server, IM conferencing capabilities are automatically deployed; you specify whether to deploy web, A/V, and dial-in conferencing by using the Topology Builder. For more information, see [Deploy conferencing in Skype for Business Server](../../deploy/deploy-conferencing/deploy-conferencing.md). 
  
The following subsections describe the features and capabilities of each conferencing type.
  
### Web conferencing

Web conferencing allows meeting attendees to collaborate on documents shared during the meeting, and for the meeting presenter to share applications through the Skype for Business client. Web conferencing provides the following features: 
  
- **Whiteboard and Annotations.** A whiteboard is a blank canvas that can be used for collaboration, with text, ink, drawings and images. Annotations made on whiteboards can be seen by all meeting participants. The whiteboard feature enhances collaboration by enabling meeting participants to discuss ideas, brainstorm, take notes, and so on.
    
- **Polling.** The polling feature enhances collaboration by enabling presenters to quickly determine participants' preferences. During online meetings and conversations, presenters can use polling to gather anonymous responses from participants. All presenters can see the results and can either hide the results or show them to all attendees.
    
- **Application sharing and Desktop sharing.** During a conference, the meeting presenter can share their entire desktop, an individual application, or individual monitors in a multi-monitor environment. Aside from just viewing the content, other participants in the conference can request control of the presenter's screen and, with permission, interact with the content (including scrolling and editing). Meeting participants can also take over as presenter and start sharing content during the meeting.
    
- **PowerPoint Sharing.** Allows users to share PowerPoint presentations in the meeting through an Office Web Apps server, which allows for:
    
  - High-resolution displays and support for PowerPoint capabilities, such as animations, slide transitions, and embedded video.
    
  - Mobile devices can access these presentations.
    
  - Users with the appropriate permissions can scroll through a PowerPoint presentation independent of the presentation itself. For example, while Ken is presenting his slide show, Heidi can look at any slide she wants to without affecting Ken's presentation.
    
### Audio and video conferencing

Audio and video conferencing allows for audio and video in the meeting. Audio allows attendees to talk to each other as though they were in the same room. Video enables video display in the Skype for Business client of any attendees or presenters that join the meeting with a web cam or conferencing device that supports video.
  
 Skype for Business Server provides several features that users can use to configure the audio conferencing experience for the user, including the following:
  
- **Audience mute.** The presenter can use this setting to mute all the audio participants in the conference and put the conference in a state where non-presenters cannot unmute themselves.
    
- **Conferencing Entry/Exit Announcements.** If you have enabled dial-in conferencing, presenters can use this setting to turn entry and exit announcements on or off to minimize distractions while a conference is in progress.
    
- **Adding a user by dialing out.** Presenters and attendees that have been given permission, can add PSTN numbers to the conferences and have the conference dial-out to those numbers.
    
  Skype for Business Server provides several features that users can use to configure the video conferencing experience for the user, including the following:
  
- **Gallery View.** In video conferences that have more than two people, users automatically see everyone in the conference. If the conference has more than five participants, the video of the most active participants appear in the top row and only the photo appears for the other participants. Multiparty video is turned on by default.
    
- **Panoramic Video.** If a RoundTable video conferencing device is installed in the conferencing room, this feature provides a full 360 degree view of the conference room. The panoramic video strip is only available with RoundTable devices.
    
- **Presenter only video mode.** Presenters can configure the meeting so that only the video from the presenter is shown. This prevents distractions in large meetings when multiple video streams are available and locking to different sources. This mode also applies to video captured and provided by RoundTable devices.
    
- **Video Spotlight.** Presenters can configure the meeting so that only the video from a selected participant who is a video source is seen by the other participants in the conference. This mode also applies to video captured and provided by RoundTable devices for panoramic video.
    
### Dial-in conferencing

Dial-in conferencing allows meeting attendees to join the audio portion of a meeting by calling in to the meeting from a phone. Dial-in conferencing is a subset of audio conferencing and requires additional configuration. For more information about dial-in conferencing, see [Plan for dial-in conferencing in Skype for Business Server](dial-in-conferencing.md) and [Configure dial-in conferencing in Skype for Business Server](../../deploy/deploy-conferencing/dial-in-conferencing.md). 
  
### Instant messaging conferencing

Instant messaging (IM) conferencing allows more than two parties to communicate in a single IM session. For details about IM conferencing, see [Plan for instant messaging and presence in Skype for Business Server](../../plan-your-deployment/instant-messaging-and-presence.md).
  
## Conferencing components

The components that support conferencing features include the following:
  
- **Application service.** The Application service provides a platform for deploying, hosting, and managing unified communications (UC) applications. Dial-in conferencing uses two UC applications that require the Application service: Conferencing Attendant and Conferencing Announcement. The Application service is installed and activated by default on every Front End Server in a Front End pool. It is also installed on every Standard Edition server to enable and configure dial-in conferencing.
    
- **Conferencing Attendant application.** The Conferencing Attendant application is a unified communications application that accepts public switched telephone network (PSTN) calls, plays prompts, and joins the calls to an A/V conference. The Conferencing Attendant application is installed and activated by default when you enable dial-in conferencing.
    
- **Conferencing Announcement application.** The Conferencing Announcement application is a unified communications application that plays tones and prompts to PSTN participants on certain actions, such as when participants join or leave a conference, participants are muted or unmuted, someone enters the conference lobby, or the conference is locked or unlocked. Conferencing Announcement application also supports dual-tone multi-frequency (DTMF) commands from the phone keypad. The Conferencing Announcement application is automatically installed and activated by default when you enable dial-in conferencing.
    
- **Dial-in Conferencing Settings page.** The Dial-in Conferencing Settings page displays conference dial-in numbers with their available languages, assigned conference information (that is, for meetings that do not need to be scheduled), and in-conference DTMF controls, and supports management of personal identification number (PIN) and assigned conferencing information. The Dial-in Conferencing Settings page is automatically installed as part of Web Services.
    
- **Mediation Server and PSTN gateway.** Dial-in conferencing requires a Mediation Server to translate signaling (and media in some configurations) between Skype for Business Server and the PSTN gateway, and a PSTN gateway to translate signaling and media between the Mediation Server and the PSTN gateway. For dial-in conferencing, you must deploy at least one Mediation Server and at least one of the following:
    
  - PSTN gateway
    
  - IP-PBX
    
  - Session Border Controller (SBC) (for an Internet telephony service provider to which you connect by configuring a SIP trunk)
    
  > [!NOTE]
  > If you are also deploying Enterprise Voice, Mediation Server and PSTN gateways are part of the Enterprise Voice deployment. If you are not deploying Enterprise Voice, you need to deploy at least one Mediation Server and at least one PSTN gateway, IP-PBX, or SBC for dial-in conferencing. 
  
- **File store.** File store is used for recorded name audio files. File Store is a standard component in every Enterprise Edition or Standard Edition deployment.
    
- **User store.** User store is used to store user Skype for Business Server PINs. PINs are hashed. The User store is a standard component in every Enterprise Edition or Standard Edition deployment.
    
- **Office Web Apps Server.** In order to use web conferencing capabilities, administrators must install Office Web Apps Server and they must configure Skype for Business Server to communicate with Office Web Apps Server.
    
## Conferencing policies

To enforce your organization's policies and control bandwidth usage, you can set policies for the types of meetings that users can organize. You can define a wide variety of conferencing policies, and assign them to individual users and groups of users. You can also set policies that govern peer-to-peer conversations. For details about setting conferencing policies, see [Manage conferencing policies in Skype for Business Server](../../manage/conferencing/conferencing-policies.md). For details about bandwidth management, see [Plan for call admission control in Skype for Business Server](../../plan-your-deployment/enterprise-voice-solution/call-admission-control.md).
  
## Support for large meetings

The size of meetings that Skype for Business Server can support depends on whether conferencing is hosted on a shared or dedicated pool:
  
- On a shared pool, Skype for Business Server can host meetings with up to 250 users. A shared pool is a pool that hosts all Skype for Business Server workloads including instant messaging (IM) and presence, conferencing, and Enterprise Voice. 
    
- On a dedicated pool, Skype for Business Server can support meetings with up to 1000 participants using web and audio/video (A/V) conferencing, including sharing PowerPoint presentations. This support requires a dedicated pool configured to support large meetings and managed in a way that ensures hosting of only a single large meeting at a time. 
    
For more information about managing large meetings, see [Plan for large meetings in Skype for Business Server](large-meetings.md).
  
If your organization requires larger meeting capabilities, you should consider implementing a hybrid environment that takes advantage of Skype Meeting Broadcast, an online service that is part of Office 365. Skype Meeting Broadcast enables users to host and broadcast meetings to large online audiences of up to 10,000 participants. The use of Skype Meeting Broadcast requires that Skype for Business Server already be configured in a hybrid setup with a production Office 365 tenant. All users must have an online tenant established as a prerequisite. If you are interested in deploying a hybrid solution that can take advantage of Skype Meeting Broadcast, see [Configure your on-premises deployment for Skype Meeting Broadcast](../../deploy/configure-skype-meeting-broadcast.md).
  
## Determine your organizations needs

When you are determining which conferencing capabilities to deploy, you need to consider the features that you want available to your users and your network bandwidth capabilities. The following list guides you through the conferencing planning process to determine what features of conferencing you should deploy, based on your organization's requirements.
  
> [!NOTE]
> When you enable conferencing at deployment, you automatically enable both web and A/V conferencing. You can, however, disable specific features by configuring conferencing policies as described previously in this topic. 
  
- **Do you want to enable web conferencing, which includes document collaboration and application sharing?**
    
    If so, you must enable conferencing for your Front End pool by using the Planning Tool or by using Topology Builder. For more information, see [Deploy conferencing in Skype for Business Server](../../deploy/deploy-conferencing/deploy-conferencing.md).
    
    Application sharing requires and uses more network bandwidth than document collaboration. Skype for Business Server provides a throttling mechanism to control each application sharing session. By default, this is set to 1.5 KB/second for each session. If you do not want to enable application sharing but you do want document collaboration, you can enable conferencing and use conferencing policies to disable application sharing. For details about configuring conferencing policies, see [Manage conferencing policies in Skype for Business Server](../../manage/conferencing/conferencing-policies.md).
    
    To enable users to share PowerPoint presentations, you need to configure Office Web Apps Server. For details about configuring Office Web Apps Server, see [Configure integration with Office Web Apps Server in Skype for Business Server](../../deploy/deploy-conferencing/office-web-app-server.md).
    
- **Do you want to enable audio and video conferencing?**
    
    If so, you must enable conferencing for your Front End pool by using the Planning Tool or by using Topology Builder. For more information, see [Deploy conferencing in Skype for Business Server](../../deploy/deploy-conferencing/deploy-conferencing.md).
    
    Audio and video conferencing requires and uses more network bandwidth than web conferencing (which includes document collaboration and application sharing). If you do not want to enable audio and video conferencing but you do want to enable web conferencing, you can enable conferencing and use conferencing policies to disable A/V conferences.
    
    If you do want to enable audio conferences but not video conferences, you can enable A/V conferencing and use conferencing policies to prevent video conferences. Alternatively, you can enable A/V conferencing and enable only certain users to start or participate in A/V conferences. 
    
    For more information about configuring conferencing policies, see [Manage conferencing policies in Skype for Business Server](../../manage/conferencing/conferencing-policies.md).
    
    > [!NOTE]
    > Enterprise Voice is not required for you to use A/V conferencing. If you enable A/V conferencing, your users can add audio to their conferences if they have audio devices, even if you use a PBX for your telephone solution. 
  
- **Do you want to enable users to join the audio portion of conferences when using a PSTN phone?**
    
    If so, deploy and enable dial-in conferencing. Invited users, both inside and outside your organization, can then join the audio portion of conferences by using a PSTN phone.
    
    Dial-in conferencing is an optional feature that you can configure when you deploy Skype for Business Server conferencing. Although dial-in conferencing uses some of the same components that Enterprise Voice uses, you can deploy dial-in conferencing even if you do not deploy Enterprise Voice. Dial-in conferencing supports both enterprise and anonymous users. For more information about configuring dial-in conferencing for enterprise and anonymous users, see [Deploy conferencing in Skype for Business Server](../../deploy/deploy-conferencing/deploy-conferencing.md) and [Configure dial-in conferencing in Skype for Business Server](../../deploy/deploy-conferencing/dial-in-conferencing.md).
    
- **Do you want to enable external users with Skype for Business clients to join conferences?**
    
    By allowing external participation in meetings, you maximize your investment in Skype for Business Server. External users can include:
    
  - **Remote users.** Your organization's own users, when they are working outside your firewalls and are using their laptops or other Skype for Business Server devices.
    
  - **Federated Users.** Users from companies you work with who also run Skype for Business Server. To enable your users to easily contact these users, you create federated relationships with these companies.
    
  - **Anonymous Users.** Any other external users who are invited specifically by your users to join specific conferences. A meeting organizer in your company can send an email invitation for a conference to an external user. The email includes a link that the outside user can click to join the conference.
    
    If you want to allow external users, you'll need to deploy Edge Servers. Additionally, with Edge Servers deployed you can create federated relationships with other organizations--such as your customers or vendors--and users from those organizations can more easily collaborate with your users.
    
    For details about deploying Edge Servers, see Plan for Edge Servers and Deploy Edge Servers. For details about enabling external access for Office Web Apps Server, see [Configure integration with Office Web Apps Server in Skype for Business Server](../../deploy/deploy-conferencing/office-web-app-server.md).
    
- **Do you want to control the clients that can join Skype for Business Server meetings?**
    
    If so, you should configure the meeting join page so that only the client options that you want to support are available. Each time a user clicks a link to join a scheduled meeting, Skype for Business Server detects whether a client is already installed on the computer. It then starts the default client and opens the meeting join page, which contains links for alternate clients. The meeting join page always contains the option to use Skype for Business Web App. In addition to this option, you can decide whether to include links for Attendee and previous versions of Communicator. 
    

