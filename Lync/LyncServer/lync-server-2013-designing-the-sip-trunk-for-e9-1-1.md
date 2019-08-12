---
title: 'Lync Server 2013: Designing the SIP trunk for E9-1-1'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Designing the SIP trunk for E9-1-1
ms:assetid: 4f93b974-b460-45c7-a4a8-6f38e34840f5
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398323(v=OCS.15)
ms:contentKeyID: 48184096
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Designing the SIP trunk for E9-1-1 in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-03_

Lync Server uses SIP trunks to connect an emergency call to the E9-1-1 service provider. You can set up emergency service SIP trunks for E9-1-1 at one central site, at multiple central sites, or at each branch site. However, if the WAN link between the caller’s site and the site that hosts the emergency service SIP trunk is unavailable, then a call placed by a user at the disconnected site will need a special phone usage record in the user’s voice policy that will route the call to the ECRC through the local public switched telephone network (PSTN) gateway. The same is true if call admission control concurrent call limits are in effect.

<div>


> [!NOTE]  
> There are two ways to implement a SIP trunk in a Lync Server environment: 
> <UL>
> <LI>
> <P>Use multihomed Mediation Servers that use their outward-facing publicly-routed interfaces to communicate with the SIP trunk provider.</P>
> <LI>
> <P>Use an on-premises Session Border Controller (SBC) to provide a secure demarcation point between the Mediation Servers and the SIP trunk provider’s services.</P></LI></UL>If you choose the latter method, be sure that the SBC make and model that you choose has been certified and supports passing Presence Information Data Format Location Object (PIDF-LO) location data as part of its SIP INVITE. Otherwise, the calls will arrive at the emergency services service provider stripped of their location information. For details about certified SBCs, see "Infrastructure Qualified for Microsoft Lync" at <A href="http://go.microsoft.com/fwlink/p/?linkid=248425">http://go.microsoft.com/fwlink/p/?LinkId=248425</A>.<BR>E9-1-1 service providers supply you with access to a pair of SBCs for redundancy. You need to make several decisions regarding the Mediation Server topology and call routing configuration. Will you treat both SBCs as equal peers and use round-robin routing for calls between them, or will you designate one SBC as primary and the other as secondary?



</div>

For details about deploying a SIP trunk in Lync Server, see [How do I implement SIP trunking in Lync Server 2013?](lync-server-2013-how-do-i-implement-sip-trunking.md). The following questions will help you decide how to deploy the SIP trunks for E9-1-1.

  - **Should you deploy the SIP trunk over a dedicated leased or a shared internet connection?**  
    It is important that emergency calls always connect. A dedicated line provides a connection that will not be preempted by other traffic on the network, and gives you the ability to implement Quality of Service (QoS). Remember that if you are connecting to emergency services service providers over the public Internet and you need to guarantee the confidentiality of emergency calls, IPSec encryption is required.

<!-- end list -->

  - **Is your E9-1-1 deployment designed for disaster tolerance?**  
    Because this is an emergency solution, resiliency is important. Deploy your primary and secondary Mediation Servers and SIP trunks in disaster tolerant locations. It is a good idea to deploy your primary Mediation Server closest to the users that it is supporting, and route failover calls through the secondary Mediation Server (located in a different geographic location).

<!-- end list -->

  - **Should you deploy a separate SIP trunk for each branch office?**  
    Lync Server provides several strategies for handling voice resiliency in branch offices, including: having resilient data networks, deploying a SIP trunk at each branch, or pushing calls out to the local gateway during outages. For details, see [Branch site SIP trunking in Lync Server 2013](lync-server-2013-branch-site-sip-trunking.md).

<!-- end list -->

  - **Is call admission control (CAC) enabled?**  
    Lync Server does not handle emergency calls any differently than an ordinary call. For this reason, bandwidth management, or call admission control (CAC), can have a negative impact on an E9-1-1 configuration. Emergency calls will be blocked or routed to the local PSTN gateway if a CAC is enabled and the configured limit is exceeded on a link where emergency calls are being routed. As indicated earlier in this topic, such calls will not have location data and must be manually routed to the ECRC.

</div>

<span> </span>

</div>

</div>

</div>

