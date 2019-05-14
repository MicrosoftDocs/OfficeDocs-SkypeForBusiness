---
title: Lync Server 2013 components and topologies for conferencing
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Components and topologies for conferencing
ms:assetid: eb83052a-3360-4ba1-a6a0-6ee419942809
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg399061(v=OCS.15)
ms:contentKeyID: 48185707
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Components and topologies for conferencing in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-04_

When you select conferencing in Topology Builder, conferencing is deployed as part of the Front End Server or Standard Edition server. Dial-in conferencing and PowerPoint sharing requires additional components and configuration. The following sections describe the supported components and topologies for web conferencing, A/V conferencing, and dial-in conferencing.

<div>

## Supported Components

The only components web conferencing and A/V conferencing require are your organization’s Front End Servers or Standard Edition servers. For a list of hardware and software requirements for the Front End Servers and Standard Edition servers, see [Supported hardware for Lync Server 2013](lync-server-2013-supported-hardware.md) and [Server software and infrastructure support in Lync Server 2013](lync-server-2013-server-software-and-infrastructure-support.md).

Lync Server 2013 uses Office Web Apps and the Office Web Apps Server to handle sharing and rendering of PowerPoint presentations. For details about installing and configuring the Office Web Apps Server, see [Configuring integration with Office Web Apps Server and Lync Server 2013](lync-server-2013-enabling-office-web-apps-server-and-lync-server-2013.md).

In addition to the requirements for web conferencing and A/V conferencing, dial-in conferencing uses the following Lync Server 2013 components:

  - **Application service**   Application service provides a platform for deploying, hosting, and managing unified communications (UC) applications. Dial-in conferencing uses two UC applications that require Application service: Conferencing Attendant and Conferencing Announcement. Application service is installed and activated by default on every Front End Server in a Front End pool and on every Standard Edition server when you deploy a Conferencing workload and select the dial-in conferencing option.

  - **Conferencing Attendant application**   Conferencing Attendant application is a unified communications application that accepts public switched telephone network (PSTN) calls, plays prompts, and joins the calls to an A/V conference. Conferencing Attendant application is installed and activated by default when you deploy a Conferencing workload and select the dial-in conferencing option.

  - **Conferencing Announcement application**   Conferencing Announcement application is a unified communications application that plays tones and prompts to PSTN participants on certain actions, such as when participants join or leave a conference, participants are muted or unmuted, someone enters the conference lobby, or the conference is locked or unlocked. Conferencing Announcement application also supports dual-tone multifrequency (DTMF) commands from the phone keypad. Conferencing Announcement application is automatically installed and activated by default when you deploy a Conferencing workload and select the dial-in conferencing option.

  - **Dial-in Conferencing Settings page**   The Dial-in Conferencing Settings page displays conference dial-in numbers with their available languages, assigned conference information (that is, for meetings that do not need to be scheduled), and in-conference DTMF controls, and supports management of personal identification number (PIN) and assigned conferencing information. The Dial-in Conferencing Settings page is automatically installed as part of Web Services.

  - **Lync Server 2013, Mediation Server and PSTN gateway**   Dial-in conferencing requires a Mediation Server to translate signaling (and media, in some configurations) between Lync Server 2013 and the PSTN gateway, and a PSTN gateway to translate signaling and media between the Mediation Server and the PSTN gateway. For dial-in conferencing, you must deploy at least one Mediation Server and at least one of the following:
    
      - PSTN gateway
    
      - IP-PBX
    
      - Session Border Controller (SBC) (for an Internet telephony service provider to which you connect by configuring a SIP trunk)
    
    <div>
    

    > [!NOTE]  
    > If you are also deploying Enterprise Voice, Mediation Server and PSTN gateways are part of the Enterprise Voice deployment. If you are not deploying Enterprise Voice, you need to deploy at least one Mediation Server and at least one PSTN gateway, IP-PBX, or SBC for dial-in conferencing.

    
    </div>

  - **File store**   File store is used for recorded name audio files. File Store is a standard component in every Enterprise Edition or Standard Edition deployment.

  - **User store**   User store is used to store user Lync Server 2013 PINs. PINs are hashed. The User store is a standard component in every Enterprise Edition or Standard Edition deployment.

  - **Lync Server Control Panel**   Some dial-in settings can be configured by using Lync Server Control Panel.

  - **Lync Server Management Shell**   All dial-in settings can be configured by using Lync Server Management Shell cmdlets. Lync Server Management Shell cmdlets are available for deploying, configuring, running, monitoring, and troubleshooting Conferencing Attendant application and Conferencing Announcement application. For details about specific cmdlets, see Lync Server Management Shell documentation.

</div>

<div>

## Supported Topologies

In Lync Server 2013, the server running conferencing services is always collocated with the Front End Servers or Standard Edition servers. During your initial deployment, Topology Builder gives you the option to include conferencing in your topology. You can also use Topology Builder to add conferencing to an existing deployment. For details, see [Defining and configuring the topology in Lync Server 2013](lync-server-2013-defining-and-configuring-the-topology.md).

<div>

## Dial in Conferencing Toplogies

You can deploy dial-in conferencing in the following topologies and configurations:

  - Lync Server 2013 Standard Edition

  - Lync Server 2013 Enterprise Edition

  - With or without Enterprise Voice

You can deploy Application service, Conferencing Attendant application, and Conferencing Announcement application in a central site, but not in a branch site.

<div>


> [!NOTE]  
> If you deploy dial-in conferencing, you must deploy it in every pool where you deploy Lync Server 2013 conferencing. You do not need to assign access numbers in every pool, but you must deploy the dial-in conferencing feature in every pool. This requirement supports the recorded name feature when a user calls an access number from one pool to join a Lync Server 2013 conference in a different pool.



</div>

</div>

<div>

## Supported Topologies for Lync Server 2013 and Office Web Apps

Lync Server 2013 provides the following ways to configure Office Web Apps Server. Depending on your needs you can:

  - **Install both Lync Server 2013 and Office Web Apps Server on-premises behind your organization’s firewall, and in the same network zone.** With this topology, external access to Office Web Apps Server will be provided through your reverse proxy server. Both Lync Server 2013 and Office Web Apps Server (or an Office Web Apps Server farm) are installed on-premises and behind your organization's firewall. Ideally, you should install Office Web Apps Server in the same network zone as Lync Server.
    
    External Lync clients can connect to Lync Server 2013 and to Office Web Apps Server by using a reverse proxy server, which is a server that takes requests from the Internet and forwards them to the internal network. (Internal clients do not need to use the reverse proxy server because they can connect to Office Web Apps Server directly.) This topology works best if you want to use a dedicated Office Web Apps Server farm that is only used by Lync Server 2013.

  - **Using an externally deployed Office Web Apps Server**
    
    In this topology, Lync Server 2013 is deployed on-premises, and uses an Office Web Apps Server that is deployed outside of Lync Server network zone. This may happen when Office Web Apps Server is shared across multiple applications in the corporation and is deployed in a network requiring Lync Server to use the external interface of Office Web Apps Server and vice versa.
    
    You do not need to install a reverse proxy server; instead, all the requests from the Office Web Apps Server to Lync Server 2013 are routed through your Edge Server. Both your internal and your external Lync clients connect to Office Web Apps Server using the external URL.
    
    If the Office Web Apps Server is deployed outside your internal firewall, then select the option **Office Web Apps Server is deployed in an external network (that is, perimeter/Internet)** in Topology Builder. For more details see [Configuring integration with Office Web Apps Server and Lync Server 2013](lync-server-2013-enabling-office-web-apps-server-and-lync-server-2013.md).

Regardless of the topology you select, it is critical that the correct firewall ports be opened. You must make sure that DNS names, IP addresses, and ports are not blocked by firewalls on the Office Web Apps Server, the load balancer, or Lync Server.

<div>


> [!NOTE]  
> Another option for providing external access to Office Web Apps Server is to deploy the server in the perimeter network. If you elect to do this, keep in mind that Office Web Apps Server setup requires the server computer to be a member of your Active Directory domain. Unless your network policy allows computers in the perimeter network to be Active Directory domain members, it is recommended that you do not install Office Web Apps Server in the perimeter network. Instead, you should install Office Web Apps Server in the internal network and provide external user access through your reverse proxy server.



</div>

</div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

