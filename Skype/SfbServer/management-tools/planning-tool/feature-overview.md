---
title: "Feature Overview (Planning Tool)"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 4/6/2016
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.plan.FeatureOverview
- ms.lync.plan.FeatureOverview
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 44783b37-c87f-41f2-9de1-39176f1856ab
description: "Skype for Business Server 2015 Planning Tool"
---

# Feature Overview (Planning Tool)
 
Skype for Business Server 2015 Planning Tool
  
You can use the **Central Sites** page of the Planning Tool to design the Skype for Business Server deployment. You can create two either a centralized or distributed deployment. A centralized deployment only has one central site, which homes all Skype for Business users in your organization. A distributed deployment has more than one central site. If you deploy Skype for Business Server at multiple central sites, then you will enter the number of users at each central site in the Planning Tool.
  
To complete the definition of the central site, you first need to provide the following information:
  
- **Site Name** Enter the name of the Central Site.
    
- **Number of Users** Enter the number of users, including users at branch sites who are homed into the central site.
    
- **Cloud Homed Users** Enter the number of users that are homed into the central site from Skype for Business Online.
    
> [!NOTE]
> This tool will not be updated for Skype for Business Server 2019.

## UI Elements

The remaining elements have either been populated with the answers you provided to the questions presented in the **Get Started** wizard, or, if you skipped the wizard, automatically populated by the planning tool.
  
### Online Collaboration

 **Online Collaboration** contains the following options:
  
- **IM and Presence**
    
    Instant Messaging (IM) enables users to communicate with each other in real time on their computers using text-based messages. Both two-party and multiparty IM sessions are supported. Presence provides information to users about the status of others on the network. A user's presence status provides information to help others determine whether the user is online and how to best contact the user. For example, a user who is in a meeting is best contacted by email.
    
- **Audio and Video Conferencing**
    
    Audio/Video (A/V) conferencing enables real-time audio and video conferences.
    
- **Dial-in Conferencing**
    
    Dial-in conferencing enables users to join an A/V from a telephone on the PSTN. Dial-in conferencing requires that you deploy the Conferencing Attendant and Conferencing Announcement Service applications.
    
- **Web Conferencing**
    
    Web conferencing enables enterprise users inside and outside of the firewall to create and join real-time conferences that are hosted on your internal servers.
    
- **Persistent Chat**
    
    Persistent Chat enables multiple users to participate in conversations in which they post and access content about specific topics, including text, links, and files. Although users can communicate in real time during a session, the content of each session is persistent, which means it continues to be available after a session ends.
    
### Users

 **Users** contains the following options:
  
- **Internal organization**
    
- **Federation with other organizations**
    
- **Federation with previous versions**
    
- **Federation with public IM services providers** Allows users in your organization to establish communication with public instant messaging service providers such as MSN, Yahoo!, and AOL. A separate license is required to establish federation with public instant messaging networks.
    
- **Federation with XMPP-based service provider**
    
    Skype for Business Server 2015 introduces a fully integrated XMPP proxy (deployed on the Edge Servers) and an XMPP gateway deployed on your Front End Servers. You can deploy Adding and configuring the XMPP proxy and XMPP gateway will allow your Skype for Business Server 2015 users to add contacts from XMPP-based partners for instant messaging (IM) and presence.

> [!NOTE]
> XMPP Gateways and proxies are available in Skype for Business Server 2015 but are no longer supported in Skype for Business Server 2019. See [Migrating XMPP federation](../../../SfBServer2019/migration/migrating-xmpp-federation.md) for more information.
    
- **Mobility**
    
    When you deploy the Skype for Business Server 2015 Mobility Service, users can use supported Apple iOS, Android, Windows Phone, or Nokia mobile devices to perform such activities as sending and receiving instant messages, viewing contacts, and viewing presence.
    
- **W15 Exchange mailbox**
    
    Skype for Business Server 2015 enables you to have voicemail messages stored in Exchange Unified Messaging (UM); those voicemail messages will then appear as email messages in your users' Inboxes.
    
### Voice

 **Voice** contains the following options:
  
- **Enterprise Voice**
    
    Enterprise voice is Microsft's software-powered VoIP solution. Enterprise voice enables users to use Skype for Business to place a phone call from their computer.
    
- **Exchange Unified Messaging**
    
    Exchange Unified Messaging (UM) combines voice mail and email into a single messaging infrastructure. Skype for Business Server 2015 uses Exchange UM to provide call answering, subscriber access, call notification, and auto attendant services. If you use these services, you will need to integrate Exchange UM and Skype for Business Server in a shared Active Directory topology.
    
### Additional Deployment Options

 **Additional Deployment Options** contains the following options:
  
- **High Availability**
    
    High availability enables standby servers for failover support.
    
- **Disaster Recovery**
    
    Disaster recovery measures enable you to pair Front End pools located in two datacenters.
    
- **Monitoring**
    
    Monitoring captures call detail records related to communication sessions. It also collects metrics from audio and video sessions at the participant endpoints. Monitoring Server provides usage statistics, trends, and media quality statistics.
    
- **Archiving**
    
    Archiving stores instant messaging conversations and conferences.
    
- **Exchange Archiving Integration**
    
    If you have users who are homed on Exchange 2013 and their mailboxes have been put on In-Place Hold, you can select the option to integrate Skype for Business Server 2015 storage with Exchange storage.
    
- **IPv4**
    
    IPv4 addresses are 32-bit addresses that allow a computer to communicate over the Internet. Due to the increasing number of devices worldwide, the available IPv4 addresses have run out. Because of this, many new devices are moving to using IPv6 addresses.
    
- **IPv6**
    
    IPv6 addresses perform the same function as IPv4 addresses (with some additional features), but instead of using only 32-bits, IPv6 addresses use 128-bits. This provides not only a new set of addresses, but also a much larger number of them.
    
- **Device Update Web service**
    
    The Device Update Web service provides an automated way to update all devices, such as Skype for Business for Windows Phone, that are deployed outside of your organization.
    
### Server Applications

 **Server Applications** contains the following options:
  
- **Response Group**
    
    The Response Group application automatically answers and distributes calls to an available helpdesk agent.
    
- **Announcement**
    
    If you plan to deploy Enterprise Voice, you might want to be able to configure how phone calls are handled if the dialed number is valid but not assigned to a user common area. Administrators can configure Announcement Service so that these calls transfer to a predetermined destination (phone number or SIP URI) or play an audio announcement or both. Using Announcement Service avoids the situation in which a caller misdials and hears a busy tone or the SIP client receives an error message. Announcement Service functionality is a typical PBX feature. 
    
- **Call Park**
    
    Call Park application enables an Enterprise Voice user to put a call on hold from one telephone, and then receive the call from another telephone without tying up resources on the phone that received the call. Call Park application is useful when a user needs to transfer a call, but the specific recipient is unknown. 
    
- **Conference Attendant**
    
    Conferencing Attendant application provides audio conferencing capabilities to phone users without the service of a third-party audio conferencing provider.
    
- **Conferencing Announcement**
    
    Conferencing Announcement application produces tones that signal when users enter or leave a conference, as well as notifications to phone users when they are muted or unmuted.
    
- **Call Admission Control**
    
    Call Admission Control (CAC), also known as WAN bandwidth management, helps to prevent poor quality of experience for users on congested networks by determining, based on available bandwidth, whether to allow and new real-time communications sessions to be established. 
    
    > [!NOTE]
    > CAC only controls real-time traffic and does not affect data traffic. 
  
    If a new voice or video session exceeds the bandwidth limits that you have allocated on a WAN, the session is either blocked or (for phone calls only) rerouted to the PSTN.
    

