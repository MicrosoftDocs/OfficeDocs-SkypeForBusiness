---
title: 'Lync Server 2013: Deploying monitoring'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Deploying monitoring
ms:assetid: 117f4a3e-0670-4388-a553-b9854921145f
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398199(v=OCS.15)
ms:contentKeyID: 48183442
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Deploying monitoring in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-12-17_

Major changes have been made to the Microsoft Lync Server 2013 monitoring infrastructure, beginning with the fact that the Monitoring Server role has been deprecated. Instead of separate Monitoring Server roles (which typically required organizations to set up dedicated computers to act as Monitoring servers) monitoring services are now collocated on each Front End server. Among other things, this change helps to:

  - Decrease the number of server roles required when implementing Lync Server 2013. In this case, decrementing the Monitoring Server server role also helps to reduce costs by eliminating the need to maintain dedicated servers for monitoring.

  - Reduce the complexity of Lync Server setup and administration. By automatically collocating the monitoring services on each Front End server you no longer have to install, configure, and manage the Monitoring Server role.

<div>


> [!NOTE]  
> The Archiving Server role has also been deprecated in Lync Server 2013. Like the monitoring services, Lync Server 2013 archiving services are now collocated on each Front End server. This is important to note simply because monitoring and archiving often share the same SQL Server database instance.



</div>

As you might expect, these changes have a major impact on how monitoring services are installed and managed. For example, because the Monitoring Server role no longer exists, the Monitoring Server node has been removed from the Lync Server Topology Builder; in turn, that means you no longer use Topology Builder's New Monitoring Server Wizard in order to add a new Monitoring Server to your topology. (That wizard no longer exists.) Instead, you will typically implement monitoring services within your topology by completing the following two steps:

1.  Enabling monitoring at the same time you set up a new Lync Server pool. (In Lync Server 2013, monitoring is enabled or disabled on a pool-by-pool basis.) Note that you can enable monitoring for a pool without actually collecting monitoring data, a process explained in the Configuring Call Detail Recording and Quality of Experience Settings section of this documentation.

2.  Associating a monitoring store (that is, a monitoring database) with the new pool. Note that a single monitoring store can be associated with multiple pools. Depending on the number of users homed on your Registrar pools, that means that you do not have to set up a separate monitoring database for each of your pools. Instead, single monitoring store can be used by multiple pools.

Although it's often easier to enable monitoring at the same time that you create a new pool, it's also possible to create a new pool with monitoring disabled. If you do that, you can later use Topology Builder to enable the service: Topology Builder provides a way to enable or disable monitoring for a pool, or to associate a pool with a different monitoring store. Keep in mind that even though there is no longer a Monitoring Server role you will still need to create one or more monitoring stores: backend databases used to store the data gathered by the monitoring service. These backend databases can be created using either Microsoft SQL Server 2008 R2 or Microsoft SQL Server 2012.

<div>


> [!NOTE]  
> If monitoring has been enabled for a pool you can disable the process of collecting monitoring data without having to change your topology: Lync Server Management Shell provides a way for you to disable (and then later re-enable) call detail recording (CDR) or Quality of Experience (QoE) data collection. For more information, see the Configuring Call Detail Recording and Quality of Experience Settings section of this document.



</div>

One other important enhancement to monitoring in Lync Server 2013 is the fact that Lync Server Monitoring Reports now support IPv6: reports that use the IP Address field will display either IPv4 or IPv6 addresses depending on : 1) the SQL query being used; and, 2) where or not the IPv6 address is stored in the monitoring database.

<div>


> [!NOTE]  
> Ensure that the SQL Server Agent Service Startup Type is Automatic and the SQL Server Agent Service is running for the SQL Instance which is holding the Monitoring databases, so that the Default Monitoring SQL Server Maintenance Jobs can run on their scheduled basis under the control of the SQL Server Agent Service.



</div>

This documentation walks you through the process of installing and configuring monitoring and Monitoring Reports for Lync Server 2013. The documentation provides step-by-step instructions that will help you to:

  - Enable monitoring in your topology and associate a monitoring store with a Front End pool.

  - Install SQL Server Reporting Services and the Lync Server Monitoring Reports. Monitoring Reports are preconfigured reports that provide different views into the information stored in a monitoring database.

  - Configure call detail recording (CDR) and Quality of Experience (QoE) data collection. Call detail recording provides a way for you to track usage of Lync Server capabilities such as Voice over IP (VoIP) phone calls; instant messaging (IM); file transfers; audio/video (A/V) conferencing; and application sharing sessions. QoE metrics track the quality of audio and video calls made in your organization, including such things as the number of network packets lost, background noise, and the amount of "jitter" (differences in packet delay).

  - Manually purge CDR and/or QoE records from the monitoring database.

</div>

<span> </span>

</div>

</div>

</div>

