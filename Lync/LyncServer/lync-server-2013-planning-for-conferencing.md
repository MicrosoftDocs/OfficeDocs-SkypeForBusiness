---
title: 'Lync Server 2013: Planning for conferencing'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Planning for conferencing
ms:assetid: 983a272a-e1b3-4d70-8f84-836b092fe526
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398781(v=OCS.15)
ms:contentKeyID: 48184937
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Planning for conferencing in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-01-29_

Lync Server 2013 offers a rich set of conferencing capabilities:

  - Web conferencing, which includes document collaboration, application sharing, and desktop sharing. Lync Server 2013 uses Office Web Apps and the Office Web Apps Server to handle sharing and rendering of PowerPoint presentations. For details about installing and configuring the Office Web Apps Server, see [Configuring integration with Office Web Apps Server and Lync Server 2013](lync-server-2013-enabling-office-web-apps-server-and-lync-server-2013.md).

  - Audio/video (A/V) conferencing, which enables users to have real-time audio or video conferences without the need for external services such as the Microsoft Live Meeting service or a third-party audio bridge.

  - Dial-in conferencing, which allows users to join the audio portion of a Lync Server 2013 conference by using a public switched telephone network (PSTN) phone without requiring a third-party audio conferencing provider.

  - Instant messaging (IM) conferencing, in which more than two parties communicate in a single IM session. For details about IM conferencing, see [Planning for Front End Servers, instant messaging, and presence in Lync Server 2013](lync-server-2013-planning-for-front-end-servers-instant-messaging-and-presence.md).

Lync Server 2013 supports both scheduled conferences and impromptu conferences.

When you deploy Lync Server 2013, Front End Server, you can choose whether to also deploy the web conferencing, A/V conferencing, and dial-in conferencing capabilities. IM conferencing capabilities are always automatically deployed along with IM conversation capabilities on Lync Server 2013 Front End Servers.

<div>


> [!NOTE]  
> If your deployment includes meetings organized using Office Communicator 2007 R2 clients (including the Live Meeting console or Conferencing Add-in for Microsoft Office Outlook), the meetings will have the following limitations after they are migrated to Lync Server 2013: 
> <UL>
> <LI>
> <P>Users in the meeting will not be able to use data collaboration features, including document collaboration, application sharing, and desktop sharing.</P>
> <LI>
> <P>Stability issues may arise since Office Communicator 2007 R2 clients are not supported with Lync Server 2013.</P></LI></UL>To avoid these issues, reschedule any meeting organized using Office Communicator 2007 R2 clients with Outlook 2010 or Outlook 2013 using either the Online Meeting Add-in for Lync 2010 or Online Meeting Add-in for Lync 2013.



</div>

The following sections describe what is required to deploy the various types of conferencing capabilities, including the planning process, components, hardware and software requirements, and the deployment process.

<div>

## In This Section

  - [Overview of conferencing in Lync Server 2013](lync-server-2013-overview-of-conferencing.md)

  - [Defining your requirements for conferencing in Lync Server 2013](lync-server-2013-defining-your-requirements-for-conferencing.md)

  - [Components and topologies for conferencing in Lync Server 2013](lync-server-2013-components-and-topologies-for-conferencing.md)

  - [Technical requirements for conferencing in Lync Server 2013](lync-server-2013-technical-requirements-for-conferencing.md)

  - [Deployment checklist for conferencing in Lync Server 2013](lync-server-2013-deployment-checklist-for-conferencing.md)

  - [Support for large meetings in Lync Server 2013](lync-server-2013-support-for-large-meetings.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

