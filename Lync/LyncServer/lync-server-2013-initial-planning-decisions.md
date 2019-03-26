---
title: Lync Server 2013 initial planning decisions
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Initial planning decisions
ms:assetid: cbaa5cb3-2b00-4b9f-952d-986a0c9f160b
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398855(v=OCS.15)
ms:contentKeyID: 48185651
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Initial planning decisions for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-01_

The first part of the planning process is deciding which Lync Server workloads and major features you want for your organization.

1.  **Do you want an on-premises or online deployment?**   Lync Server supports both deployment scenarios. For more information on making this decision, see [Deciding how to deploy Lync Server 2013](lync-server-2013-deciding-how-to-deploy-microsoft-lync.md), earlier in this section

2.  **Do you want a physical or virtualized topology?**   Lync Server supports all workloads and server roles in both physical and virtualized topologies. User capacity and scalability can differ between physical and virtual topologies. For more information, see [Running Lync Server 2013 on virtual servers](lync-server-2013-running-lync-server-on-virtual-servers.md).

3.  **Instant messaging *(IM)* and *presence* are always enabled.**   In any Lync Server deployment, the instant messaging (IM) and presence workload is installed and enabled by default. IM enables your users to communicate with real-time text messages, and presence enables them to see the status of other users on the network. A user’s presence status provides information to help others decide whether they should try to contact the user, and by what means. For details, see [Planning for Front End Servers, instant messaging, and presence in Lync Server 2013](lync-server-2013-planning-for-front-end-servers-instant-messaging-and-presence.md) in the Planning documentation.

4.  **Do you want to deploy any modes of conferencing?**   Conferencing is another core feature of Lync Server. Several modes of conferencing are supported. You can choose to deploy all supported types of conferencing, or just some of them. *Web conferencing* enables users to see a file, such as a slide deck created with Microsoft PowerPoint presentation graphics program, that is being presented. *Application sharing* enables users to share all or part of their desktop with each other in real time. With *A/V conferencing*, users can add audio (and possibly video) to their conferences and peer-to-peer communications. *Dial-in conferencing* enables users to use standard PSTN phones to join the audio portion of conferences hosted at your organization. For details, see [Planning for conferencing in Lync Server 2013](lync-server-2013-planning-for-conferencing.md) in the Planning documentation.
    
    In Lync Server 2013, if you deploy Web conferencing, you must also plan for integration with Office Web Apps Server to enable Powerpoint sharing and viewing in meetings. For more information, see [Configuring integration with Office Web Apps Server and Lync Server 2013](lync-server-2013-enabling-office-web-apps-server-and-lync-server-2013.md).

5.  **If you deploy A/V conferencing, you should also monitor the audio quality of these conferences.**   Many factors affect the audio and video quality of Lync Server A/V conferences. By using Monitoring, you can monitor the A/V quality of your calls and conferences. You can detect issues that affect media quality, and ensure that your users have the best possible media experience. For more information, see [Planning for monitoring in Lync Server 2013](lync-server-2013-planning-for-monitoring.md).

6.  **Do you want high availability for your IM, presence, and conferencing servers?**   If you have only one server at a site providing IM, presence and conferencing features, your users’ productivity will be greatly affected if that server goes down. By deploying an Enterprise Edition *pool* of at least three servers for these functions, you make it possible for Lync Server to continue functioning with all of these features intact even if a server is unavailable.
    
    Another option for organizations with 5000 or fewer users who want high availability is to deploy two servers running Lync Server Standard Edition and pair these servers together. For more information, see [Planning for high availability and disaster recovery in Lync Server 2013](lync-server-2013-planning-for-high-availability-and-disaster-recovery.md).

7.  **Do you want disaster recovery options?**   If you have two datacenters and want disaster recovery options to enable your users to continue to work if all or many servers at one datacenter go down, you can deploy your servers with disaster recovery in mind. For this deployment, you pair a pool of servers at one datacenter with a corresponding pool at another datacenter. If one datacenter goes down, the other pool in the pair can service users in both pools with minimum interruption of services. For more information, see [Planning for high availability and disaster recovery in Lync Server 2013](lync-server-2013-planning-for-high-availability-and-disaster-recovery.md).

8.  **Do you want to enable your users to communicate and collaborate with external users?**   Enabling communication and collaboration with external users can increase your return on investment in Lync Server. This enables your organization’s own users to benefit from Lync Server features even when they are working outside your organization’s firewalls. You can also federate with your partner or customer organizations that run Lync Server. By doing so, your users and federated partner users can easily send and receive IM messages, invite each other to meetings, and see each other’s presence. Additionally, your users can use an email message to invite specific outside users to conferences that they organize. For more information, see [Planning for external user access in Lync Server 2013](lync-server-2013-planning-for-external-user-access.md).

9.  **Do you want to deploy Enterprise Voice?**    *Enterprise Voice* is the voice over IP (VoIP) solution provided by Lync Server. It provides an attractive alternative to traditional PBX-based telephony. Enterprise Voice enables users to place calls from their computers or VoIP phones by clicking a contact in Outlook or Lync Server. They can place calls over the IP network from computer to computer, computer to telephone, or telephone to computer. Users benefit from having all of their communications options-voice, email, IM, and conferencing-available and integrated on their computers. For details, see [Planning for Enterprise Voice in Lync Server 2013](lync-server-2013-planning-for-enterprise-voice.md) in the Planning documentation.

10. **If you deploy Enterprise Voice, you should also monitor the audio quality of these calls.**   We recommend you use Monitoring to ensure the audio quality of your Enterprise Voice calls, if you deploy Enterprise Voice. For more information, see [Planning for monitoring in Lync Server 2013](lync-server-2013-planning-for-monitoring.md).

11. **Do you need to archive IM content or meeting content for compliance purposes?**   If your organization has to archive IM content or meeting content for compliance purposes, you can deploy Archiving. For more information, see [Planning for Archiving in Lync Server 2013](lync-server-2013-planning-for-archiving.md).

12. **Do you want to deploy Persistent chat?**   If you want to enable your users to have real-time conversations that can persist over time, you can deploy Persistent chat. For more information, see [Planning for Persistent Chat Server in Lync Server 2013](lync-server-2013-planning-for-persistent-chat-server.md).

13. **Do you have Microsoft Exchange deployed?**   If your organization uses Microsoft Exchange Server for its email services, you can enable several features which enhance the usefulness of both Lync Server and Microsoft Exchange Server. Some of these features, called Exchange Unified Messaging (UM), include enabling users to receive voice mail notices and listen to voice mail from Outlook or Outlook Web Access, to access their Microsoft Exchange mailboxes using a telephone, and to receive faxes in their Microsoft Exchange mailboxes. Additionally, if you have Exchange 2013 deployed, you can integrate the contact stores for users between the two systems, use Exchange to store higher-resolution contact photos, and integrate the archiving of emails and instant messages. For more information, see [Planning for Exchange Server integration with Lync Server 2013](lync-server-2013-planning-for-exchange-server-integration.md).

14. **Do you have branch offices in your organization?**   If your organization has branch offices, Lync Server supports a variety of ways to support them and ensure their resiliency for voice and other features. In particular, at a branch office that does not have a resilient WAN link to a data center, you can install a Survivable Branch Appliance or Survivable Branch Server to maintain Enterprise Voice support should the wide area network (WAN) link go down. For more information, see [Planning for branch-site voice resiliency in Lync Server 2013](lync-server-2013-planning-for-branch-site-voice-resiliency.md).

</div>

<span> </span>

</div>

</div>

</div>

