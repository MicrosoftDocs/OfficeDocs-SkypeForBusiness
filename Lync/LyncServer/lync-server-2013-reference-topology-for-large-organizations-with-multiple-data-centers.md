---
title: Lync Server 2013 reference topology for large organizations with multiple data centers
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Reference topology for large organizations with multiple data centers
ms:assetid: 9a6aeae6-629b-49e6-9804-7ef369d7c3dc
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398797(v=OCS.15)
ms:contentKeyID: 48184887
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Reference topology for Lync Server 2013 in large organizations with multiple data centers

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-22_

The reference topology for a large organization with multiple data centers support is for any size of organization with more than one central site. The exact topology in the following diagram is for an organization of 50,000 users, with 20,000 users at Central Site A, 20,000 at Central Site B. and a total of 10,000 at Central Site C and branch sites. The type of topology shown in this diagram can accommodate organizations with any number of users.

In addition to the high availability provided by pools of Front End Servers, this topology adds disaster recovery support. The Front End pools at Central Sites A and B are paired together. If one of these pools goes down, the administrator can shift the services for the affected users to the paired pool at the unaffected site.

This topology is shown in multiple diagrams, with an overview first followed by detailed views of the central sites.

**Overview of the reference topology for large organizations with multiple data centers**

![Reference topology for multiple data centers](images/Gg398797.471e1ce9-be11-44b9-9f4a-59e0551b7b30(OCS.15).jpg "Reference topology for multiple data centers")

**Reference topology for large organizations: Detailed view of Central Site A**

![dab33f19-e77b-42da-9047-858fb9851264](images/Gg398797.dab33f19-e77b-42da-9047-858fb9851264(OCS.15).jpg "dab33f19-e77b-42da-9047-858fb9851264")

**Reference topology for large organizations: Detailed view of Central Site B**

![5ccaf1d4-bd53-4cb7-96fe-723147334e7f](images/Gg398797.5ccaf1d4-bd53-4cb7-96fe-723147334e7f(OCS.15).jpg "5ccaf1d4-bd53-4cb7-96fe-723147334e7f")

**Reference topology for large organizations: Detailed view of Central Site C**

![7238ca40-340c-491f-b497-ddc2665dadb6](images/Gg398797.7238ca40-340c-491f-b497-ddc2665dadb6(OCS.15).jpg "7238ca40-340c-491f-b497-ddc2665dadb6")

  - **Front End pools Are Paired to Enable Disaster Recovery.**   The Front End pools at Site A and Site B are paired with each other, to provide disaster recovery support. If the pool at one site fails, the administrator can fail over the users from that site to the paired Front End pool at the other site, with a minimum of service interruption for users. Each of these two Front End pools has six servers, which is enough for all 40,000 users in both pools in case of failover. For more information, see [Planning for high availability and disaster recovery in Lync Server 2013](lync-server-2013-planning-for-high-availability-and-disaster-recovery.md).

  - **Back End Servers are mirrored**   To provide more high availability for basic user features, the organization has deployed a mirrored pair of Back End Servers for each Front End pool. This is an optional topology, and you could choose to deploy a single Back End Server instead.

  - **Using Standard Edition server at a branch site.**   This organization considers Site C as a branch site because it has only 600 employees. However, the users there have many A/V conferences among themselves. If it was deployed in Lync Server as a branch site, the media for these conferences would run across the wide area network (WAN) to and from a central site that has a Front End Server deployed. To avoid this potential bandwidth load, they have installed a pair of Standard Edition servers at this site, which will host these conferences. And because Standard Edition servers are installed there, Lync Server by definition considers it a central site, and it is treated as such in Topology Builder and the Planning Tool.
    
    Just one Standard Edition server would be enough for performance here, but the organization has deployed two and paired them together to provide high availability in case one server goes down.
    
    Although Site C is considered a central site, you do not have to deploy Edge Servers there. In this example, Site C will use the Edge Servers deployed at Site A.

  - **Monitoring and Archiving**   This organization has deployed both Monitoring and Archiving. When you deploy Monitoring or Archiving, it runs on every Front End Server. The databases for these features can be collocated with the Back End Database, or located on a separate server. This organization has located these databases on a server separate from the Back End Servers, in Central Site B. The databases here receive Monitoring and Archiving data from the Front End Servers in all sites.

  - **Branch site deployment options.**   This organization actually has over 50 branch sites, only three of which are shown in the detailed diagrams. Branch Sites 1 and 3 do not have a resilient WAN link to the central site, so they have Survivable Branch Appliances deployed to provide telephone service in case the WAN link to the central site goes down. Branch Site 2 however has a resilient WAN link, so you need only a public switched telephone network (PSTN) gateway. The PSTN gateway deployed there supports media bypass, so no Mediation Server is needed at Branch Site B. For details about deciding what to install at a branch site, see [Planning for Enterprise Voice resiliency in Lync Server 2013](lync-server-2013-planning-for-enterprise-voice-resiliency.md) in the Planning documentation.

  - **SIP trunking and Mediation Server.**   Notice that at Central Site B, Mediation Server is not collocated with the Front End Servers. This is because stand-alone Mediation Server is recommended for sites that use SIP trunking. In most other instances, we recommend you collocate Mediation Server with Front End Server. For details about Mediation Server topologies, see [Components and topologies for Mediation Server in Lync Server 2013](lync-server-2013-components-and-topologies-for-mediation-server.md) in the Planning documentation.

  - **Persistent Chat is Deployed.**   This organization has deployed the servers necessary to enable Persistent Chat. It has deployed multiple Persistent Chat Front End Servers to both handle the load for the number of users in the pool, and to provide high availability. It has also deployed Compliance for Persistent Chat, and located the Persistent Chat Store and the Persistent Chat Compliance Store on separate servers. These stores could be collocated, and can even be collocated with the Back End Server, but this organization has chosen to separate them to provide better performance.

  - **DNS load balancing.**   The Front End pool and Edge Server pool,. This eliminates the need for hardware load balancers for the internal interface of the Edge Servers, and significantly decreases the amount of time you have to spend on the setup and maintenance of the hardware load balancers for the other pools, as the hardware load balancers are needed only for HTTP traffic. For details about DNS load balancing, see [DNS load balancing in Lync Server 2013](lync-server-2013-dns-load-balancing.md) in the Planning documentation.

  - **Exchange UM deployment.**  Lync Server works with both *on-premises* deployments of Exchange Unified Messaging (UM) and *hosted* Exchange UM. Central Site A includes an Exchange Unified Messaging (UM) Server, which runs Microsoft Exchange Server, not Lync Server. The Exchange UM functionality for Lync Server runs on the Front End pool.
    
    Central Site B uses hosted Exchange, so the Exchange UM Server functionality is also hosted.
    
    For details about Exchange UM, see [Planning for Exchange Unified Messaging integration in Lync Server 2013](lync-server-2013-planning-for-exchange-unified-messaging-integration.md) and [Hosted Exchange Unified Messaging integration in Lync Server 2013](lync-server-2013-hosted-exchange-unified-messaging-integration.md) in the Planning documentation.

  - **Office Web Apps Server.**   We recommend deploying an Office Web Apps Server or Office Web Apps Server farm in every organization that uses web conferencing. You could deploy a single Office Web Apps Server farm in one site which serves traffic from all sites, or deploy it in each site. Office Web Apps Server makes it possible for Powerpoint slides to be presented in web conferences. For more information, see [Configuring integration with Office Web Apps Server and Lync Server 2013](lync-server-2013-enabling-office-web-apps-server-and-lync-server-2013.md).

  - **Directors could be added.**  If this organization wanted to increase security against denial of service attacks, it could also deploy a pool of Directors. A Director is a separate, optional server role in Lync Server that does not home user accounts, or provide presence or conferencing services. It serves as an internal next hop server to which an Edge Server routes inbound SIP traffic destined for internal servers. The Director pre-authenticates inbound requests and redirects them to the user’s home pool or server. Pre-authentication at the Director allows for dropping of requests from user accounts unknown to the deployment. A Director helps insulate Front End Servers from malicious traffic such as denial-of-service (DoS) attacks. If the network is flooded with invalid external traffic in such an attack, the traffic ends at the Director.

  - **System Center Operations Manager is deployed.**  We recommend that you monitor the health of your Lync Server deployment to ensure service availability for end-users. You can monitor Lync with the System Center Operations Manager Management Pack for Lync that is available as a free download from Microsoft. With the Lync Management Pack, you can proactively get real-time alerts when issues occur, run synthetic transactions to test end-to-end Lync functionality, get reports for service availability, and so on.  This helps you to proactively respond to issues with your deployment before end-users experience them.
    
    This organization has deployed a System Center Operations Manager server in each central site.

</div>

<span> </span>

</div>

</div>

</div>

