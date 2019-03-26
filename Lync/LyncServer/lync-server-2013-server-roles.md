---
title: Lync Server 2013 server roles
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Server roles
ms:assetid: 7137fc06-fca2-4e5f-9db5-10c7c29a788c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398536(v=OCS.15)
ms:contentKeyID: 48184456
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Server roles in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-10-07_

Each server running Lync Server runs one or more *server roles*. A server role is a defined set of Lync Server functionalities provided by that server. You do not need to deploy all available server roles in your network. Install only the server roles that contain the functionality that you want.

Even if you are not familiar with server roles in Lync Server, the Planning Tool can guide you to the best solution for the servers that you need to deploy, based on the features that you want. This section provides a brief overview of the server roles and the general features that they provide:

  - Standard Edition Server

  - Front End Server and Back End Server

  - Edge Server

  - Mediation Server

  - Director

  - Persistent Chat Front End Server

  - Persistent Chat Store (Persistent Chat Back End Server)

  - Persistent Chat Compliance Store (Persistent Chat Compliance Back End Server)

For most server roles, for scalability and high availability you can deploy *pools* of multiple servers all running the same server role. Each server in a pool must run an identical server role or roles. For most types of pools in Lync Server, you must deploy a load balancer to spread traffic between the various servers in the pool. Lync Server supports both Domain Name System (DNS) load balancing and hardware load balancers.

<div>

## Standard Edition Server

The Standard Edition server is designed for small organizations, and for pilot projects of large organizations. It enables many of the features of Lync Server, including the necessary databases, to run on a single server. This enables you to have Lync Server functionality for a lower cost, but does not provide a true high-availability solution.

Standard Edition server enables you to use instant messaging (IM), presence, conferencing, and Enterprise Voice, all running on one server.

For a high-availability solution, use Lync Server Enterprise Edition.

</div>

<div>

## Front End Server and Back End Server

In Lync Server Enterprise Edition, the Front End Server is the core server role, and runs many basic Lync Server functions. The Front End Server, along with the Back End Servers, are the only server roles required to be in any Lync Server Enterprise Edition deployment.

A *Front End pool* is a set of Front End Servers, configured identically, that work together to provide services for a common group of users. A pool of multiple servers running the same role provides scalability and failover capability.

The Front End Server includes the following:

  - User authentication and registration

  - Presence information and contact card exchange

  - Address book services and distribution list expansion

  - IM functionality, including multiparty IM conferences

  - Web conferencing, PSTN Dial-in conferencing and A/V conferencing (if deployed)

  - Application hosting, for both applications included with Lync Server (for example, Conferencing Attendant and Response Group application), and third-party applications

  - Optionally, Monitoring, to collect usage information in the form of call detail records (CDRs) and call error records (CERs). This information provides metrics about the quality of the media (audio and video) traversing your network for both Enterprise Voice calls and A/V conferences.

  - Web components to supported web-based tasks such as web scheduler and join launcher.

  - Optionally, Archiving, to archive IM communications and meeting content for compliance reasons. For details, see [Planning for Archiving in Lync Server 2013](lync-server-2013-planning-for-archiving.md) in the Planning documentation.
    
    In Lync Server 2010 and prior versions, Monitoring and Archiving were separate server roles, not collocated on Front End Server.

  - Optionally, if Persistent chat is enabled, Persistent Chat Web Services for Chat Room Management and Persistent Chat Web Services for File Upload/Download.

Front End Pools are also the primary store for user and conference data. Information about each user is replicated among three Front End Servers in the pool, and backed up on the Back End Servers.

Additionally, one Front End pool in the deployment also runs the *Central Management Server*, which manages and deploys basic configuration data to all servers running Lync Server. The Central Management Server also provides Lync Server Management Shell and file transfer capabilities.

The Back End Servers are database servers running Microsoft SQL Server that provide the database services for the Front End pool. The Back End Servers serve as backup stores for the pool’s user and conference data, and are the primary stores for other databases such as the Response Group database. You can have a single Back End Server, but a solution that uses SQL Server mirroring is recommended for failover. Back End Servers do not run any Lync Server software.

<div>


> [!IMPORTANT]  
> We do not recommend collocating Lync Server databases with other databases. If you do so, availability and performance may be affected.



</div>

Information stored in the Back End Server databases includes presence information, users' Contacts lists, conferencing data, including persistent data about the state of all current conferences, and conference scheduling data.

</div>

<div>

## Edge Server

Edge Server enables your users to communicate and collaborate with users outside the organization’s firewalls. These external users can include the organization’s own users who are currently working offsite, users from federated partner organizations, and outside users who have been invited to join conferences hosted on your Lync Server deployment. Edge Server also enables connectivity to public IM connectivity services, including Windows Live, AOL, Yahoo\!, and Google Talk.

<div>


> [!IMPORTANT]  
> <UL>
> <LI>
> <P>As of September 1st, 2012, the Microsoft Lync Public IM Connectivity User Subscription License (“PIC USL”) is no longer available for purchase for new or renewing agreements. Customers with active licenses will be able to continue to federate with Yahoo! Messenger until the service shut down date. An end of life date of June 2014 for AOL and Yahoo! has been announced. For details, see <A href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Support for public instant messenger connectivity in Lync Server 2013</A>.</P>
> <LI>
> <P>The PIC USL is a per-user per-month subscription license that is required for Lync Server or Office Communications Server to federate with Yahoo! Messenger. Microsoft’s ability to provide this service has been contingent upon support from Yahoo!, the underlying agreement for which is winding down.</P>
> <LI>
> <P>More than ever, Lync is a powerful tool for connecting across organizations and with individuals around the world. Federation with Windows Live Messenger requires no additional user/device licenses beyond the Lync Standard CAL. Skype federation will be added to this list, enabling Lync users to reach hundreds of millions of people with IM and voice.</P></LI></UL>



</div>

Deploying Edge Server also enables mobility services, which supports Lync functionality on mobile devices. Users can use supported Apple iOS, Android, Windows Phone, or Nokia mobile devices to perform activities such as sending and receiving instant messages, viewing contacts, and viewing presence. In addition, mobile devices support some Enterprise Voice features, such as click to join a conference, Call via Work, single number reach, voice mail, and missed calls. The mobility feature also supports *push notifications* for mobile devices that do not support applications running in the background. A push notification is a notification that is sent to a mobile device about an event that occurs while a mobile application is inactive.

Edge Servers also include a fully-integrated Extensible Messaging and Presence Protocol (XMPP) proxy, with an XMPP gateway included on Front End Servers. You can configure these XMPP components to enable your Lync Server 2013 users to add contacts from XMPP-based partners (such as Google Talk) for instant messaging and presence.

For details, see [Planning for external user access in Lync Server 2013](lync-server-2013-planning-for-external-user-access.md) in the Planning documentation.

</div>

<div>

## Mediation Server

Mediation Server is a necessary component for implementing Enterprise Voice and dial-in conferencing. Mediation Server translates signaling, and, in some configurations, media between your internal Lync Server infrastructure and a public switched telephone network (PSTN) gateway, IP-PBX, or a Session Initiation Protocol (SIP) trunk. You can run Mediation Server collocated on the same server as Front End Server, or separated into a stand-alone Mediation Server pool.

For details, see [Mediation Server component in Lync Server 2013](lync-server-2013-mediation-server-component.md) in the Planning documentation.

</div>

<div>

## Director

Directors can authenticate Lync Server user requests, but they do not home user accounts or provide presence or conferencing services. Directors are most useful to enhance security in deployments that enable external user access. The Director can authenticate requests before sending them on to internal servers. In the case of a denial-of-service attack, the attack ends with the Director and does not reach the Front End servers. For details, see [Scenarios for the Director in Lync Server 2013](lync-server-2013-scenarios-for-the-director.md) in the Planning documentation.

</div>

<div>

## Persistent Chat Server Roles

Persistent chat enables users to participate in multiparty, topic-based conversations that persist over time. The Persistent Chat Front End Server runs the persistent chat service. The Persistent Chat Back End Server stores the chat history data, and information about categories and chat rooms. The optional Persistent Chat Compliance Back End Server can store the chat content and compliance events for the purpose of compliance.

Servers running Lync Server Standard Edition can also run Persistent chat collocated on the same server. You cannot collocate the Persistent Chat Front End Server with Enterprise Edition Front End Server.

For details, see [Planning for Persistent Chat Server in Lync Server 2013](lync-server-2013-planning-for-persistent-chat-server.md).

</div>

<div>

## See Also


[Mediation Server component in Lync Server 2013](lync-server-2013-mediation-server-component.md)  


[Planning for Archiving in Lync Server 2013](lync-server-2013-planning-for-archiving.md)  
[Planning for external user access in Lync Server 2013](lync-server-2013-planning-for-external-user-access.md)  
[Scenarios for the Director in Lync Server 2013](lync-server-2013-scenarios-for-the-director.md)  
[Planning for Persistent Chat Server in Lync Server 2013](lync-server-2013-planning-for-persistent-chat-server.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

