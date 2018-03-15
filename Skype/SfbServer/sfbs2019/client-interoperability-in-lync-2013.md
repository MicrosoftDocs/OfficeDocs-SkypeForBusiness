---
title: "Client interoperability in Lync 2013"
ms.author: crowe
author: CarolynRowe
manager: laurawi
ms.date: 3/4/2016
ms.audience: End User
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 0f126571-91a2-45d5-855c-1e4ddb45fc04
description: "In this articleServer and Client CompatibilityInteroperability among ClientsScheduling Add-in SupportSupport for Joining Meetings"
---

# Client interoperability in Lync 2013
[]
 **In this article**
  
[Server and Client Compatibility](#sectionSection0)
  
[Interoperability among Clients](#sectionSection1)
  
[Scheduling Add-in Support](#sectionSection2)
  
[Support for Joining Meetings](#sectionSection3)
  
This topic discusses the ability of Microsoft Lync Server 2013 clients to coexist and interact with clients from earlier versions of Lync Server and Office Communications Server. 
  
## Server and Client Compatibility
<a name="sectionSection0"> </a>

The following table shows the supported combinations of client versions and server versions. This table indicates whether sign-in is supported when the client attempts to connect to the server indicated. Lync Server 2013 supports the previous client version. Also, unlike previous releases, Lync Server 2010 supports the new Lync 2013 clients. This allows organizations who are upgrading from Lync Server 2010 to roll out new clients independent of Lync Server upgrades.
  
|**Client**|**Lync Server 2013**|**Lync Server 2010**|**Office Communications Server 2007 R2**|
|:-----|:-----|:-----|:-----|
|Lync 2013  <br/> |Supported  <br/> |Supported<sup>5</sup> <br/> |Not Supported  <br/> |
|Lync 2013 Basic  <br/> |Supported  <br/> |Supported  <br/> |Not Supported  <br/> |
|Lync Web App 2013  <br/> |Supported  <br/> |Not Supported  <br/> |Not Supported  <br/> |
|Lync 2010  <br/> |Supported  <br/> |Supported  <br/> |Not Supported  <br/> |
|Lync 2010 Attendant  <br/> |Supported  <br/> |Supported  <br/> |Not Supported  <br/> |
|Lync 2010 Group Chat  <br/> |Supported<sup>1</sup> <br/> |Supported<sup>2</sup> <br/> |Not Applicable  <br/> |
|Lync Web App 2010  <br/> |Not Supported  <br/> |Supported  <br/> |Not Supported  <br/> |
|Lync 2010 Attendee  <br/> |Not Supported<sup>3</sup> <br/> |Supported  <br/> |Not Supported  <br/> |
|Office Communicator 2007 R2  <br/> |Interoperable<sup>4</sup> <br/> |Supported  <br/> |Supported  <br/> |
|Microsoft Office Communications Server 2007 R2 Attendant  <br/> |Not Supported  <br/> |Supported  <br/> |Supported  <br/> |
|Office Communicator 2007  <br/> |Not Supported  <br/> |Supported  <br/> |Supported  <br/> |
|Office Live Meeting 2007  <br/> |Not Supported  <br/> |Supported  <br/> |Supported  <br/> |
|Lync Windows Store app  <br/> |Supported  <br/> |Supported  <br/> |Not Supported  <br/> |
   
<sup>1</sup>For details, see [Migration from Lync Server 2010, Group Chat or Office Communications Server 2007 R2 Group Chat to Lync Server 2013, Persistent Chat Server](migration-from-lync-server-2010-group-chat-or-office-communications-server-2007.md).
  
<sup>2</sup>In Microsoft Lync Server 2010, group chat functionality was available with Group Chat Server, a third-party trusted application for Lync Server 2010. Lync 2013 clients are not compatible with Lync Server 2010, Group Chat.
  
<sup>3</sup>Lync Web App 2013 now provides a full in-meeting experience, including computer audio and video, and is considered the replacement for Lync 2010 Attendee. Lync 2010 Attendee will connect to Lync Server 2013 only when you are using an unsupported browser (Internet Explorer 6 or Internet Explorer 7) and Windows XP.
  
<sup>4</sup>The presence and IM features in Office Communicator 2007 R2 are compatible with Lync Server 2013, but conferencing features are not. During migration from Office Communications Server 2007 R2, Office Communicator 2007 R2 is suitable for presence and IM interoperability, but users should use Lync Web App 2013 to join Lync Server 2013 meetings. 
  
<sup>5</sup> For limitations, see "Conferencing Feature Support for Lync 2013 Clients in Lync Server 2010 Meetings" later in this topic. 
  
## Interoperability among Clients
<a name="sectionSection1"> </a>

With the Lync Server 2013 release, various client versions can interact seamlessly in both peer-to-peer and conferencing scenarios. This section discusses feature availability when users interact with other users who are using different versions of clients and servers.
  
### Peer-to-Peer Feature Support

Peer-to-peer features are supported for users who are homed on different versions of the server and who are using different client versions. The end-user experience and available features are consistent with the capabilities of the user's client and the version of the server the user is signed in to. In other words: 
  
- If a user is signed in to Lync Server 2013 with an older client, the user will have the same experience he or she is used to. None of the new features introduced in Lync Server 2013 will be available until the user's client is upgraded. Examples include video gallery view, HD video, updated PowerPoint sharing, and the option to mute all attendee audio and video upon meeting entry. The new features are outlined in [New conferencing features in Lync Server 2013](new-conferencing-features.md) and [What's new for clients in Lync Server 2013](what-s-new-for-clients.md).
    
- If a user is signed in to Lync Server 2010 with a Lync 2013 client, any new features not supported by Lync Server 2010 will be unavailable until the user is moved to Lync Server 2013.
    
The following table compares feature availability in peer-to-peer sessions where the client is signed in to either Lync Server 2013 or Lync Server 2010. 
  
> [!NOTE]
> Lync Web App and Lync 2010 Attendee are meeting-only clients and aren't included in this table. 
  
|**Client**|**Instant Messaging**|**Presence**|**Voice**|**Video**|**Application Sharing**|**File Transfer**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|Lync 2013  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|Lync 2013 Basic  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|Lync 2010  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|Lync 2010 Attendant  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> ||||
|Lync 2010 Mobile  <br/> |Yes  <br/> |Yes  <br/> |||||
|Lync Phone Edition  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> ||||
|Office Communicator 2007 R2  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes<sup>1</sup> <br/> |Yes  <br/> |
|Public IM (AOL, Yahoo!)  <br/> |Yes  <br/> |Yes  <br/> |||||
|Public IM (MSN, Windows Live Messenger)  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |||
   
> [!IMPORTANT]
>  As of September 1st, 2012, the Microsoft Lync Public IM Connectivity User Subscription License (PIC USL) is no longer available for the purchase for new or renewing agreements. Customers with active licenses will be able to continue to federate with Yahoo! Messenger until the service shutdown date. An end of life date of June 2014 for AOL and Yahoo! has been announced. For details, see [Support for public instant messenger connectivity in Lync Server 2013](support-for-public-instant-messenger-connectivity.md).. >  The PIC USL is a per-user, per-month subscription license that is required for Lync Server or Office Communications Server to federate with Yahoo! Messenger. Microsoft's ability to provide this service has been contingent upon support from Yahoo!, the underlying agreement for which will not be renewed. >  More than ever, Lync is a powerful tool for connecting across organizations and with individuals around the world. Federation with Windows Live Messenger requires no additional user/device licenses beyond the Lync Standard CAL. Skype federation will be added to this list, enabling Lync users to reach hundreds of millions of people through IM and voice. 
  
<sup>1</sup> In Office Communicator 2007 R2, only desktop sharing (and not program sharing) is available. 
  
> [!NOTE]
> Desktop sharing between Office Communicator 2007 R2 and Skype for Business 2015 cannot be initiated from the newer client when the Skype for Business 2015 client user interface is enforced. 
  
### Conferencing Feature Support for Lync 2013 Clients in Lync Server 2010 Meetings

When users join Lync Server 2010 meetings with a Lync 2013 client, they have access to Lync 2013 client features with the following exceptions:
  
- In the **Participants** management options, which are accessible by pointing to the people icon in the meeting window, the **No Meeting IM** option does not function. 
    
- Gallery View does not function in video conferences. The user sees only the active speaker instead of all speakers. In the list of **Pick a Layout** options, **Gallery View** is unavailable 
    
- The participant list displays by default in video conferences.
    
- When right-clicking a user in the participants list, the **Lock the Video Spotlight** and **Pin to Gallery** participant management options are unavailable. 
    
### Conferencing Feature Support in Lync Server 2013 Meetings

Lync Server 2013 provides new conferencing features that become available to users after their accounts are moved to Lync Server 2013 and they sign in with the Lync 2013 client. Examples include video gallery view, HD video, PowerPoint sharing, and the option to mute all attendee audio and video upon meeting entry. The new features are outlined in [New conferencing features in Lync Server 2013](new-conferencing-features.md) and [What's new for clients in Lync Server 2013](what-s-new-for-clients.md).
  
In Lync Server 2013 meetings, certain conferencing features are supported for users who are homed on different versions of the server and who are using different clients and client versions. When clients join a Lync Server 2013 meeting, users have access to the features and capabilities shown in this table.
  
|**Client**|**Peer-to-peer IM**|**Voice**|**Video**|**Application Sharing**|**PowerPoint**|**File Transfer**|**Whiteboard**|**Polling**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|Lync 2013  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|Lync 2013 Basic  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|Lync Web App  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes<sup>2</sup> <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|Lync 2010  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes<sup>3</sup> <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|Office Communicator 2007 R2 <sup>4</sup> <br/> |Yes  <br/> ||||||||
   
<sup>1</sup> In Office Communicator 2007 R2, only desktop sharing (and not program sharing) is available. 
  
<sup>2</sup> Lync Server 2013 uses an updated mechanism for uploading PowerPoint files. Lync Web App users who join a meeting that was originally scheduled on Lync Server 2010 can view and navigate PowerPoint presentations, but cannot upload PowerPoint files. 
  
<sup>3</sup> If the meeting was scheduled on Lync Server 2013 and PowerPoint slides were uploaded by a Lync 2013 client, Lync 2010 users have view-only access to the slides. Conversely, if the PowerPoint slides were uploaded by a Lync 2010 user, Lync Server 2013 users will be able to view and slides and, if Office Web Apps Server is configured, access new capabilities such as higher resolution display, animations, slide transitions, and embedded video. For more information, see [Configuring integration with Office Web Apps Server and Lync Server 2013](enabling-office-web-apps-server-and-lync-server-2013.md).
  
<sup>4</sup>The presence and IM features in Office Communicator 2007 R2 are compatible with Lync Server 2013, but conferencing features are not. During migration from Office Communications Server 2007 R2, Office Communicator 2007 R2 is suitable for presence and IM interoperability, but users should use Lync Web App 2013 to join Lync Server 2013 meetings. 
  
## Scheduling Add-in Support
<a name="sectionSection2"> </a>

Server support for the various scheduling add-ins is consistent with server and client version compatibility. In general, the following scheduling add-ins are supported on Lync Server 2013. However, previous versions of add-ins do not provide new Lync 2013 add-in features, such as the option to mute all attendee audio and video upon meeting entry. 
  
- **Online Meeting Add-in for Lync 2013** Provides the same features as the Online Meeting Add-in for Lync 2010, with the addition of attendee mute controls, which allow meeting organizers to schedule conferences that have attendee audio and video muted by default. Administrators can also customize the organization's meeting invitations by adding a custom logo, a support URL, a legal disclaimer URL, or custom footer text. 
    
- **Online Meeting Add-in for Lync 2010** Provides scheduling for Lync meetings and removes the capability to schedule Office Live Meeting conferences. 
    
- **Office Communicator 2007 R2 Conferencing Add-in** Provides scheduling for both Office Live Meeting conferences and Office Communicator 2007 R2 conferences. 
    
> [!NOTE]
> Live Meeting conferences cannot be scheduled on Lync Server 2013. 
  
|**Scheduling Client**|**Lync Server 2013**|**Lync Server 2010**|**Office Communications Server 2007 R2**|
|:-----|:-----|:-----|:-----|
|Online Meeting Add-in for Lync 2013 (can be used with Office 2013, Outlook 2010, and Outlook 2007)  <br/> |Supported  <br/> |Supported (new add-in features not available)  <br/> |Not Supported  <br/> |
|Lync 2013 Web Scheduler  <br/> |Supported  <br/> |Not Supported  <br/> |Not Supported  <br/> |
|Online Meeting Add-in for Lync 2010  <br/> |Supported  <br/> |Supported  <br/> |Not Supported  <br/> |
|Office Communicator 2007 R2 Conferencing Add-in  <br/> |Not Supported  <br/> |Supported  <br/> |Supported  <br/> |
   
## Support for Joining Meetings
<a name="sectionSection3"> </a>

All of the clients that Lync Server 2013 supports are allowed to join Lync 2013 meetings. Because Lync Web App is a web component of the server, in cases where Lync Web App is used to join a Lync Server 2013 meeting, the newer version of Lync Web App is always used.
  
Lync 2013 clients can join meetings hosted on Lync 2010 and Office Communications Server 2007 R2 with scaled-down functionality. In-meeting features are limited by the version of the server on which the meeting is hosted. 
  
## See also
<a name="sectionSection3"> </a>

#### 

[Lync Windows Store app requirements for Lync Server 2013](lync-windows-store-app-requirements.md)
  
[New conferencing features in Lync Server 2013](new-conferencing-features.md)
  
[What's new for clients in Lync Server 2013](what-s-new-for-clients.md)

