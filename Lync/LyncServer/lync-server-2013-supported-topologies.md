---
title: Lync Server 2013 supported topologies
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Supported topologies
ms:assetid: 3475d430-0394-491b-a09b-ba85bd62be70
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425833(v=OCS.15)
ms:contentKeyID: 48183832
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Supported topologies in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-01-14_

Lync Server 2013 supports deployment of sites on premises in an organization and integration of on-premises deployments with Lync Online deployments, which is known as a hybrid deployment. In a hybrid deployment, some users are homed on-premises and some users are homed online.

For on-premises deployments, Lync Server 2013 supports deployment of one or more sites that can be scaled to meet high availability and location requirements. You can structure these sites and their components to meet the access and resiliency requirements of your organization.

A Lync Server 2013 on-premises deployment consists of the following:

  - Your deployment must include at least one central site (also known as a data center). Each central site must contain at least one Enterprise Edition Front End pool or one Standard Edition server. These consist of the following:
    
      - Enterprise Edition Front End pool, which consists of one or more Front End Servers (typically, at least two Front End Servers for scalability) and a separate Back End Server. A Front End pool can contain a maximum of twelve Front End Servers. Load balancing is required for multiple Front End Servers. For SIP traffic, we recommend DNS load balancing, but hardware load balancing is also supported. If you use DNS load balancing for SIP traffic, you still need a hardware load balancer for HTTP traffic. We recommend SQL Server mirroring for high availability of databases. The back-end database requires a separate instance, but you can collocate the archiving database, monitoring database, persistent chat database, and persistent chat compliance database with it. Lync Server 2013 supports the use of a shared cluster for the file shares in your deployment. For details about database storage requirements, see [Database software support in Lync Server 2013](lync-server-2013-database-software-support.md). For details about file storage requirements, see [File storage support in Lync Server 2013](lync-server-2013-file-storage-support.md).
        
        <div>
        

        > [!IMPORTANT]  
        > If you collocate Lync Server databases, we highly recommend assessing all factors that might affect availability and performance. To verify failover capabilities, we recommend testing all failover scenarios.

        
        </div>
    
      - Standard Edition server, which includes a collocated SQL Server Express database.

  - Your deployment can also have one or more branch sites associated with a central site.

This section describes the sites and components of a Lync Server 2013 deployment. For details about Lync Server 2013 site, topology, and component planning, see [Topology basics you must know before planning for Lync Server 2013](lync-server-2013-topology-basics-you-must-know-before-planning.md) and [Reference topologies in Lync Server 2013](lync-server-2013-reference-topologies.md) in the Planning documentation. For details about integration of components of previous releases, see [Supported migration paths and coexistence scenarios in Lync Server 2013](lync-server-2013-supported-migration-paths-and-coexistence-scenarios.md).

<div>


> [!NOTE]  
> Stretched pools are not supported for the Front End, Edge, Mediation, and Director server roles.



</div>

<div>

## Central Site Topologies and Components (On-Premises)

Although a central site topology must include one Front End pool or one Standard Edition server, each central site can also contain the following:

  - Multiple Front End pools, which can be in the same domain or different domains. However, all Front End Servers in a Front End pool, and the Back End Server for that pool, must be in the same domain.

  - Multiple Standard Edition servers.

  - Office Web Apps Server, which is used with Office Web Applications in Lync Server 2013 to handle the sharing and rendering of Microsoft PowerPoint presentations.

  - Edge Server or Edge pool in your perimeter network, if you want your deployment to support federated partners, public IM connectivity, an extensible messaging and presence protocol (XMPP) gateway, remote user access, participation of anonymous users in meetings, or Exchange Unified Messaging (UM). You cannot collocate any other server role with an Edge Server. We recommend DNS load balancing, where appropriate, but hardware load balancing is also supported. The internal Edge interface and external Edge interface must use the same type of load balancing. You cannot use DNS load balancing on one Edge interface and hardware load balancing on the other Edge interface. For details about load balancing requirements and support, see [Planning for external user access in Lync Server 2013](lync-server-2013-planning-for-external-user-access.md) in the Planning documentation and [Deploying external user access in Lync Server 2013](lync-server-2013-deploying-external-user-access.md) in the Deployment documentation.

  - Mediation Server or pool, if you want to support Enterprise Voice or dial-in conferencing in a Front End pool at the central site. Depending on how you deploy Enterprise Voice support, you can collocate the Mediation Server in a Front End pool (the default) or deploy a stand-alone Mediation Server or pool. You can use DNS, hardware, or application load balancing (when appropriate) to distribute traffic from a Mediation Server pool’s gateway peer, including a PSTN gateway, IP-PBX, or SIP trunk Session Border Control (SBC).For details about planning the appropriate Mediation Server topology, see [Deployment guidelines for Mediation Server in Lync Server 2013](lync-server-2013-deployment-guidelines-for-mediation-server.md) in the Planning documentation.

  - Persistent Chat Server, if you want to users to be able to participate in multiparty, topic-based conversations that persist over time. To provide more capacity and increased reliability, your topology can include multiple computers running Persistent Chat Server. You cannot collocate Persistent Chat Server with other server roles in an Enterprise pool. However, you can collocate Persistent Chat Server on a Standard Edition server. Persistent chat requires a database and, if you implement persistent chat compliance, a persistent chat compliance database, but the databases can be collocated with the Archiving database, Monitoring database, or on the Back End Server of an Enterprise Edition Front End pool. For details about planning the appropriate Persistent Chat Server topology, see [Planning for Persistent Chat Server in Lync Server 2013](lync-server-2013-planning-for-persistent-chat-server.md) in the Planning documentation.

  - Monitoring, if you want to support data collection for audio/video Quality of Experience (QoE) and call detail recording (CDR) for Enterprise Voice and A/V conferences in your deployment. Optionally, you can install the Microsoft System Center Operations Manager (formerly Microsoft Operations Manager), which uses Monitoring CDR and QoE data to generate near real-time alerts that show the health of call reliability and media quality. Monitoring, when deployed, is collocated on Front End Servers or a Standard Edition server. Monitoring requires a database, but the database can be collocated with the Archiving database, persistent chat database, persistent chat compliance database, or on the Back End Server of an Enterprise Edition Front End pool.

  - Archiving, if you want to archive IM communications and meeting content (for compliance reasons) in your deployment. Archiving, when deployed, is collocated on Front End Servers or a Standard Edition server. Archiving storage requires either deployment of an Archiving database or integration with Exchange 2013 storage. If you use both, which is known as *mixed mode*, Exchange 2013 storage is used to store archive data for users who are homed on Exchange 2013, and the Archiving database is used to archive data for all other users in your deployment. If you require an Archiving database, the database can be collocated on the Monitoring database, persistent chat database, persistent chat compliance database, or on the Back End Server of a Front End pool. For details about planning the appropriate Archiving topology, see [Planning for Archiving in Lync Server 2013](lync-server-2013-planning-for-archiving.md) in the Planning documentation.

  - Director or Director pool, if you want to facilitate resiliency and redirection of Lync Server 2013 user requests to the user’s home pool, which can be either an Enterprise Edition Front End pool or a Standard Edition server. We recommend that you deploy a Director or Director pool in each central site that supports external user access and in each central site in which you deploy one or more Front End pools. Each Director pool can contain a maximum of ten Directors. A Director cannot be collocated with any other server role. For details about planning the appropriate Director topology, see [Scenarios for the Director in Lync Server 2013](lync-server-2013-scenarios-for-the-director.md) in the Planning documentation.

  - Reverse proxy, which is not a Lync Server 2013 component, but is required if you want to support sharing of web content for federated users or to support Mobility traffic. You cannot collocate a reverse proxy server with any Lync Server 2013 server role, but you can implement reverse proxy support for a Lync Server 2013 deployment by configuring the support on an existing reverse proxy server in your organization that is used for other applications. For details about reverse proxy servers, see [Setting up reverse proxy servers for Lync Server 2013](lync-server-2013-setting-up-reverse-proxy-servers.md) in the Deployment documentation.

<div>


> [!NOTE]  
> In Lync Server 2013, A/V Conferencing, Monitoring, and Archiving run on Front End Servers and are no longer separate server roles.



</div>

All Front End pools and Standard Edition servers that you deploy at a central site share any of the following that you deploy for the central site:

  - Director or Director pool

  - Stand-alone Mediation Server or pool

  - Office Web Apps Server

  - Edge Server or Edge pool

  - Persistent Chat Server or pool

  - Monitoring

  - Archiving

<div>


> [!NOTE]  
> An Exchange UM Server can be implemented with your Lync Server 2013 deployment if you want to support integration of Exchange 2013 Unified Messaging, but it is not a component of the Lync Server 2013 site.



</div>

Multiple central sites can also share any of the following that you deploy in one central site:

  - Stand-alone Mediation Server or pool

  - Edge Server or Edge pool

  - Persistent Chat Server or pool

  - Archiving

  - Monitoring

<div>


> [!NOTE]  
> An Exchange UM Server can be implemented with your Lync Server 2013 deployment and shared by multiple central sites, but it is not a component of the Lync Server 2013 site.



</div>

For details about Lync Server 2013 server roles and functionality, see [Server roles in Lync Server 2013](lync-server-2013-server-roles.md) in the Planning documentation.

For a summary of Lync Server 2013 server collocation support, see [Supported server collocation in Lync Server 2013](lync-server-2013-supported-server-collocation.md).

In addition to the server roles and functionality covered previously in this section, Lync Server 2013 has additional components and options, which can include some or all of the following:

  - Firewalls

  - PSTN gateways (if deploying Enterprise Voice)

  - Exchange UM Server

  - DNS load balancing

  - Hardware load balancers

  - SQL Server databases

  - File shares

For details about all of the Lync Server 2013 features, components, and options, see the Planning documentation.

</div>

<div>

## Branch Site Topologies and Components (On-Premises)

A branch site is associated with a central site, and each Survivable Branch Appliance in a branch site is associated with an Enterprise Edition Front End pool or a Standard Edition server in the associated central site. Branch sites depend on the central site for most of their functionality, so components at a branch site contain only the following:

  - A Survivable Branch Appliance, which combines a public switched telephone network (PSTN) gateway with some Lync Server functionality. A Mediation Server can be collocated with the instance of the Registrar on the Survivable Branch Appliance, and you can deploy a stand-alone Mediation Server or pool of Mediation Servers.

  - A Survivable Branch Server, which is a server running Windows Server that has Lync Server 2013 Registrar and Mediation Server software installed.

  - A stand-alone PSTN gateway (not part of the Survivable Branch Appliance) and a stand-alone Mediation Server.

The requirements for Survivable Branch Servers are the same as the requirements for any Lync Server 2013 server role.

</div>

</div>

<span> </span>

</div>

</div>

</div>

