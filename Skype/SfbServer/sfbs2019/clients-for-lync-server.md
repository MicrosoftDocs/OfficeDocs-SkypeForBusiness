---
title: "Clients for Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: End User
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: e143ce9b-3624-4066-942d-6c86ad99be91
description: "In this articleLync 2013Online Meeting Add-in for Lync 2013Lync Web SchedulerLync Web AppLync 2013 BasicLync Windows Store AppLync 2013 for Mobile DevicesSupported Clients from Previous Releases"
---

# Clients for Lync Server 2013
[]
 **In this article**
  
[Lync 2013](#sectionSection0)
  
[Online Meeting Add-in for Lync 2013](#sectionSection1)
  
[Lync Web Scheduler](#sectionSection2)
  
[Lync Web App](#sectionSection3)
  
[Lync 2013 Basic](#sectionSection4)
  
[Lync Windows Store App](#sectionSection5)
  
[Lync 2013 for Mobile Devices](#sectionSection6)
  
[Supported Clients from Previous Releases](#sectionSection7)
  
Lync Server 2013 supports several types of client software that you can deploy to your organization's users, including computer-installed client software, web-based clients, and mobile devices. This topic outlines the clients that you can use. For a detailed comparison of the features provided by Lync Server 2013 clients, see [Desktop client comparison tables for Lync Server 2013](desktop-client-comparison-tables.md).
  
## Lync 2013
<a name="sectionSection0"> </a>

Lync 2013 is the full-featured client for Lync Server. The Lync 2013 user interface has been fully redesigned and includes newly integrated features, such as Persistent Chat (Lync 2010 had a separate client for chat functionality), tabbed conversations, video preview, and multiparty video. For a summary of changes, see [What's new for clients in Lync Server 2013](what-s-new-for-clients.md).
  
Lync 2013 client setup is part of the Office setup program on the installation media.
  
## Online Meeting Add-in for Lync 2013
<a name="sectionSection1"> </a>

The Online Meeting Add-in for Lync 2013 supports meeting management from within Microsoft Outlook messaging and collaboration client. The Online Meeting Add-in for Lync 2013 software installs automatically with Lync 2013.
  
## Lync Web Scheduler
<a name="sectionSection2"> </a>

Lync Web Scheduler is a web-based meeting scheduling and management tool for users who don't have access to Microsoft Outlook, or who are on an operating system not based on Windows. With Lync Web Scheduler, users can create new meetings, modify existing meetings, and send invitations using their preferred email program.
  
## Lync Web App
<a name="sectionSection3"> </a>

Lync Web App is the web-based conferencing client for Lync Server 2013 meetings. In this release, the addition of computer audio and video to Lync Web App provides a complete in-meeting experience for anyone who does not have a Lync client installed locally. Meeting participants have access to all collaboration and sharing features and presenter meeting controls. 
  
 If Lync 2013 is not installed on a user's computer and the user clicks a meeting link in a meeting request, Lync Web App opens. You can also configure the Meeting Join page to allow users to join meetings by using previous versions of clients; see [Configuring the meeting join page in Lync Server 2013](configuring-the-meeting-join-page.md) in the Deployment documentation. 
  
Because of the enhancements to Lync Web App, an updated version of Microsoft Lync 2010 Attendee is not available for Lync Server 2013. Lync Web App is the client of choice for participants outside your organization. With Lync Web App, no local client installation is required, although audio, video, and sharing features require installation of a plug-in during first use.
  
## Lync 2013 Basic
<a name="sectionSection4"> </a>

Lync 2013 Basic is a downloadable client for customers who have a licensed, on-premises Lync Server 2013 deployment and customers who subscribe to a Microsoft Office 365 plan that does not include the full Lync 2013 client. The Lync Basic client includes enhanced presence, contacts, instant messaging (IM), Lync meetings, and basic voice functionality. Features not supported in Lync Basic include multiparty video, OneNote integration, virtual desktop infrastructure (VDI) support, skill search, recording, Enterprise Voice features, and advanced call handling (for example, call forwarding and Team Call). For details, see [Desktop client comparison tables for Lync Server 2013](desktop-client-comparison-tables.md).
  
## Lync Windows Store App
<a name="sectionSection5"> </a>

The Lync Windows Store app is a touch-optimized Lync app designed specifically for Windows 8.1, Windows 8, and Windows RT. Users can download the app through the Windows Store by searching for "Lync." For more information, see [Desktop client comparison tables for Lync Server 2013](desktop-client-comparison-tables.md), [Lync Windows Store app requirements for Lync Server 2013](lync-windows-store-app-requirements.md), and [Deploying Lync Windows Store app in Lync Server 2013](deploying-lync-windows-store-app.md).
  
## Lync 2013 for Mobile Devices
<a name="sectionSection6"> </a>

Lync 2013 mobile apps now include voice over IP (VoIP) and video over IP capabilities, in addition to contacts, presence, and IM features. Mobile users can choose to communicate with others through IM, voice calls, or video calls by using either Wi-Fi or their cellular data connection. With a single click of the meeting link in a calendar item, mobile users can join voice and video meetings. For more information about Lync 2013 mobile apps, see [Planning for mobile clients in Lync Server 2013](planning-for-mobile-clients.md).
  
## Supported Clients from Previous Releases
<a name="sectionSection7"> </a>

Lync Server 2013 supports the following clients from previous server releases. You can make certain previous clients available to users when they join meetings. For details, see [Configuring the meeting join page in Lync Server 2013](configuring-the-meeting-join-page.md) in the Deployment documentation. 
  
- **Lync 2010** Lync 2010 provides a full desktop experience, including IM, enhanced presence, voice, video, sharing, and telephony. However, none of the new features introduced in Lync Server 2013 will be available until the user's client is upgraded to Lync 2013. 
    
- **Lync 2010 Mobile** Lync Server 2013 supports all of the Microsoft Lync 2010 Mobile mobile apps. Microsoft Lync 2010 Mobile provides IM, enhanced presence, and telephony for users in your organization who are connecting from a smartphone or a phone running a Professional edition of Windows Mobile. You can instruct your users to install Microsoft Lync 2010 Mobile by directing them to the app marketplace for their mobile phone. For details, see "Planning for Mobile Clients" in the Lync Server 2010 documentation at [https://go.microsoft.com/fwlink/p/?LinkID=235955](https://go.microsoft.com/fwlink/p/?LinkID=235955).
    
- **Lync Phone Edition** Lync Phone Edition software for intelligent IP phones (for example, USB-attached phones) has not been updated for Lync Server 2013. Lync Phone Edition continues to be supported in for placing and receiving calls, enhanced presence, and client audio capabilities for conferences. 
    
- **Lync 2010 Attendant** The Microsoft Lync 2010 Attendant integrated call-management program enables a receptionist to manage multiple conversations at the same time through rapid call handling, IM, and onscreen routing. 
    
## See also
<a name="sectionSection7"> </a>

#### 

[Client interoperability in Lync 2013](client-interoperability-in-lync-2013.md)

