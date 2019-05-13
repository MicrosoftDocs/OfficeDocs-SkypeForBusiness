---
title: Lync Server 2013 reference topology for medium-size organizations
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Reference topology for medium-size organizations
ms:assetid: 446b0914-2198-445e-ab6e-94802acebd5c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425939(v=OCS.15)
ms:contentKeyID: 48184026
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Reference topology for Lync Server 2013 in medium-size organizations

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-10-07_

The reference topology with high availability and a single data center is designed for a small-to-medium size organization with one central site. The exact topology in the following diagram is for an organization of 20,000 users.

**Reference topology for medium organizations**

![Reference topology for single data center diagram](images/Gg425939.12b574fd-0b14-4563-a88c-3c8b0809bb90(OCS.15).jpg "Reference topology for single data center diagram")

  - **Accommodate more users by adding more Front End Servers.**   The exact topology in this diagram has three Front End Servers to provide support for 20,000 users. If you have a single central site and more users, you can simply add more Front End Servers to the pool. The maximum number of users per pool is 80,000, with twelve Front End Servers.
    
    However, the single site topology can support even more users by adding another Front End pool to the site.

  - **Disaster Recovery could be added.**   For this organization, high availability for their Lync Server services is a necessary feature, but disaster recovery is not. The pool of Front End Servers they have deployed provides high availability.
    
    If they wanted to add disaster recovery ability, they could consider establishing another datacenter and adding another Front End pool there, and pairing it with the Front End pool in their current datacenter. Then, if there was a disaster affecting their primary pool, the administrators could fail over users to the backup pool.

  - **Back End Servers are mirrored**   To provide more high availability for basic user features, the organization has deployed a mirrored pair of Back End Servers for each Front End pool. This is a new topology option for Lync Server 2013, and is optional. You could choose to deploy a single Back End Server instead.

  - **Monitoring Server database options.**   This organization has deployed Monitoring to ensure the quality of Enterprise Voice calls and A/V conferences. Monitoring is deployed on every Front End Server, and the Monitoring database is collocated with the Back End Servers. We also support topologies in which the Monitoring database is located on a separate server.

  - **Edge Server high availability**    In this example organization with 20,000 users, just one Edge Server would be sufficient for performance. However, there is a pool of two Edge Servers deployed to provide high availability.

  - **Branch site deployment options.**   The organization in this topology has Enterprise Voice deployed as their voice solution. Branch Site 1 does not have a resilient wide area network (WAN) link to the central site, so it has a Survivable Branch Appliance deployed to maintain many Lync Server features in case the WAN link to the central site goes down. Branch Site 2 however has a resilient WAN link, so only a public switched telephone network (PSTN) gateway is needed. The PSTN gateway deployed there supports media bypass, so no Mediation Server is needed at Branch Site 2. For details about deciding what to deploy at a branch site, see [Planning for branch-site voice resiliency in Lync Server 2013](lync-server-2013-planning-for-branch-site-voice-resiliency.md) in the Planning documentation.

  - **DNS load balancing.**   The Front End pool andEdge Server pool, have DNS load balancing for SIP traffic deployed. This eliminates the need for hardware load balancers for the Edge Servers, and significantly lessens the setup and maintenance of the hardware load balancers for the other pools, as the hardware load balancers are needed only for HTTP traffic. For details about DNS load balancing, see [DNS load balancing in Lync Server 2013](lync-server-2013-dns-load-balancing.md) in the Planning documentation.

  - **Exchange UM deployment.** This reference topology includes an Exchange Unified Messaging (UM) Server, which runs Microsoft Exchange Server, not Lync Server.
    
    For details about Exchange UM, see [Planning for Exchange Unified Messaging integration in Lync Server 2013](lync-server-2013-planning-for-exchange-unified-messaging-integration.md) and [Hosted Exchange Unified Messaging integration in Lync Server 2013](lync-server-2013-hosted-exchange-unified-messaging-integration.md) in the Planning documentation.

  - **Office Web Apps Server.** We recommend deploying an Office Web Apps Server or Office Web Apps Server farm in every organization that uses web conferencing. Office Web Apps Server makes it possible for Powerpoint slides to be presented in web conferences. For more information, see [Configuring integration with Office Web Apps Server and Lync Server 2013](lync-server-2013-enabling-office-web-apps-server-and-lync-server-2013.md).

  - **Edge Servers are recommended.**   Although deploying an Edge Server is not required, we recommend it for any size of deployment. You can maximize your Lync Server investment by deploying an Edge Server to provide service to users currently outside your organization’s firewalls. The benefits include the following:
    
      - Your organization’s own users can use Lync Server functionality, if they are working from home or are out on the road.
    
      - Your users can invite outside users to participate in meetings.
    
      - If you have a partner, vendor or customer organization that also uses Lync Server, you can form a *federated relationship* with that organization. Your Lync Server deployment would then recognize users from that federated organization, leading to better collaboration.
    
      - Your users can exchange instant messages with users of public IM services, including any or all of the following: Windows Live, AOL, Yahoo\!, and Google Talk. A separate license might be required for public IM connectivity with these services.
        
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

  - **Directors could be added.**   If this organization wanted to help to increase security against denial of service attacks, it could also deploy a pool of Directors. A Director is a separate, optional server role in Lync Server that does not home user accounts, or provide presence or conferencing services. It serves as an internal next hop server to which an Edge Server routes inbound SIP traffic destined for internal servers. The Director pre-authenticates inbound requests and redirects them to the user’s home pool or server. Pre-authentication at the Director allows for dropping of requests from user accounts unknown to the deployment. A Director helps insulate Front End Servers from malicious traffic such as denial-of-service (DoS) attacks. If the network is flooded with invalid external traffic in such an attack, the traffic ends at the Director.

  - **System Center Operations Manager is recommended.**  We recommend that you monitor the health of your Lync Server deployment to help ensure service availability for end-users. You can monitor Lync with the System Center Operations Manager Management Pack for Lync that is available as a free download from Microsoft. With the Lync Management Pack, you can proactively get real-time alerts when issues occur, run synthetic transactions to test end-to-end Lync functionality, get reports for service availability, and so on.  This helps you to proactively respond to issues with your deployment before end-users experience them.

</div>

<span> </span>

</div>

</div>

</div>

