---
title: Lync Server 2013 clients
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Clients for Lync Server
ms:assetid: e143ce9b-3624-4066-942d-6c86ad99be91
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398996(v=OCS.15)
ms:contentKeyID: 48185530
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Clients for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-01-23_

Lync Server 2013 supports several types of client software that you can deploy to your organization’s users, including computer-installed client software, web-based clients, and mobile devices. This topic outlines the clients that you can use. For a detailed comparison of the features provided by Lync Server 2013 clients, see [Client comparison tables for Lync Server 2013](lync-server-2013-desktop-client-comparison-tables.md).

<div>

## Lync 2013

Lync 2013 is the full-featured client for Lync Server. The Lync 2013 user interface has been fully redesigned and includes newly integrated features, such as Persistent Chat (Lync 2010 had a separate client for chat functionality), tabbed conversations, video preview, and multiparty video. For a summary of changes, see [What's new for clients in Lync Server 2013](lync-server-2013-what-s-new-for-clients.md).

Lync 2013 client setup is part of the Office setup program on the installation media.

</div>

<div>

## Online Meeting Add-in for Lync 2013

The Online Meeting Add-in for Lync 2013 supports meeting management from within Microsoft Outlook messaging and collaboration client. The Online Meeting Add-in for Lync 2013 software installs automatically with Lync 2013.

</div>

<div>

## Lync Web Scheduler

Lync Web Scheduler is a web-based meeting scheduling and management tool for users who don’t have access to Microsoft Outlook, or who are on an operating system not based on Windows. With Lync Web Scheduler, users can create new meetings, modify existing meetings, and send invitations using their preferred email program.

</div>

<div>

## Lync Web App

Lync Web App is the web-based conferencing client for Lync Server 2013 meetings. In this release, the addition of computer audio and video to Lync Web App provides a complete in-meeting experience for anyone who does not have a Lync client installed locally. Meeting participants have access to all collaboration and sharing features and presenter meeting controls.

If Lync 2013 is not installed on a user’s computer and the user clicks a meeting link in a meeting request, Lync Web App opens. You can also configure the Meeting Join page to allow users to join meetings by using previous versions of clients; see [Configuring the meeting join page in Lync Server 2013](lync-server-2013-configuring-the-meeting-join-page.md) in the Deployment documentation.

Because of the enhancements to Lync Web App, an updated version of Microsoft Lync 2010 Attendee is not available for Lync Server 2013. Lync Web App is the client of choice for participants outside your organization. With Lync Web App, no local client installation is required, although audio, video, and sharing features require installation of a plug-in during first use.

</div>

<div>

## Lync 2013 Basic

Lync 2013 Basic is a downloadable client for customers who have a licensed, on-premises Lync Server 2013 deployment and customers who subscribe to a Microsoft Office 365 plan that does not include the full Lync 2013 client. The Lync Basic client includes enhanced presence, contacts, instant messaging (IM), Lync meetings, and basic voice functionality. Features not supported in Lync Basic include multiparty video, OneNote integration, virtual desktop infrastructure (VDI) support, skill search, recording, Enterprise Voice features, and advanced call handling (for example, call forwarding and Team Call). For details, see [Client comparison tables for Lync Server 2013](lync-server-2013-desktop-client-comparison-tables.md).

</div>

<div>

## Lync Windows Store App

The Lync Windows Store app is a touch-optimized Lync app designed specifically for Windows 8.1, Windows 8, and Windows RT. Users can download the app through the Windows Store by searching for "Lync." For more information, see [Client comparison tables for Lync Server 2013](lync-server-2013-desktop-client-comparison-tables.md), [Lync Windows Store app requirements for Lync Server 2013](lync-server-2013-lync-windows-store-app-requirements.md), and [Deploying Lync Windows Store app in Lync Server 2013](lync-server-2013-deploying-lync-windows-store-app.md).

</div>

<div>

## Lync 2013 for Mobile Devices

Lync 2013 mobile apps now include voice over IP (VoIP) and video over IP capabilities, in addition to contacts, presence, and IM features. Mobile users can choose to communicate with others through IM, voice calls, or video calls by using either Wi-Fi or their cellular data connection. With a single click of the meeting link in a calendar item, mobile users can join voice and video meetings. For more information about Lync 2013 mobile apps, see [Planning for mobile clients in Lync Server 2013](lync-server-2013-planning-for-mobile-clients.md).

</div>

<div>

## Supported Clients from Previous Releases

Lync Server 2013 supports the following clients from previous server releases. You can make certain previous clients available to users when they join meetings. For details, see [Configuring the meeting join page in Lync Server 2013](lync-server-2013-configuring-the-meeting-join-page.md) in the Deployment documentation.

  - **Lync 2010**   Lync 2010 provides a full desktop experience, including IM, enhanced presence, voice, video, sharing, and telephony. However, none of the new features introduced in Lync Server 2013 will be available until the user’s client is upgraded to Lync 2013.

  - **Lync 2010 Mobile**   Lync Server 2013 supports all of the Microsoft Lync 2010 Mobile mobile apps. Microsoft Lync 2010 Mobile provides IM, enhanced presence, and telephony for users in your organization who are connecting from a smartphone or a phone running a Professional edition of Windows Mobile. You can instruct your users to install Microsoft Lync 2010 Mobile by directing them to the app marketplace for their mobile phone. For details, see “Planning for Mobile Clients” in the Lync Server 2010 documentation at [http://go.microsoft.com/fwlink/p/?LinkID=235955](http://go.microsoft.com/fwlink/p/?linkid=235955).

  - **Lync Phone Edition**   Lync Phone Edition software for intelligent IP phones (for example, USB-attached phones) has not been updated for Lync Server 2013. Lync Phone Edition continues to be supported in for placing and receiving calls, enhanced presence, and client audio capabilities for conferences.

  - **Lync 2010 Attendant**   The Microsoft Lync 2010 Attendant integrated call-management program enables a receptionist to manage multiple conversations at the same time through rapid call handling, IM, and onscreen routing.

</div>

<div>

## See Also


[Client interoperability in Lync 2013](lync-server-2013-client-interoperability-in-lync-2013.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

