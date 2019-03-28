---
title: 'Lync Server 2013: New Persistent Chat Server features'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: New Persistent Chat Server features
ms:assetid: c3ec6f33-6261-4bf5-aa31-baa8ab2a87d8
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412965(v=OCS.15)
ms:contentKeyID: 48185341
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# New Persistent Chat Server features in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-29_

Lync Server 2013, Persistent Chat Server enables you to participate in multiparty, topic-based conversations that persist over time. Persistent Chat Server can help your organization do the following:

  - Improve communication between geographically dispersed and cross-functional teams

  - Broaden information awareness and participation

  - Improve communication with your extended organization

  - Reduce information overload

  - Improve information awareness

  - Increase dispersion of important knowledge and information

Lync Server 2013, Persistent Chat Server is not available in Microsoft Office 365. At this time, it is available only to on-premise Lync 2013 customers.

In Lync 2013, Persistent Chat functionality is integrated into the Lync 2013 client. As a result, users have access to Instant Messaging/Presence, Audio/Video, Conferencing, and Persistent Chat all in the Lync 2013 client. For more information about the Lync 2013 client, see <http://go.microsoft.com/fwlink/p/?linkid=270877>.

This topic describes feature changes between the new version of Lync Server 2013, Persistent Chat Server and the previous version (Microsoft Lync Server 2010, Group Chat), including:

  - Provide an administrative experience in Lync Server Control Panel, and eliminate the Group Chat Admin Tool

  - Integrate configuration settings for Persistent Chat Server into Topology Builder by eliminating the Group Chat Configuration tool

  - Ease migration and upgrade from previous versions of Persistent Chat Server

  - Provide high availability and disaster recovery solutions

For additional details about the latest version of Persistent Chat Server, see the following:

  - The Persistent Chat Help at <http://go.microsoft.com/fwlink/p/?linkid=270945> which provides a detailed list of Persistent Chat features, how they work, and how to use them while running Persistent Chat Server.

  - The [Planning for Persistent Chat Server in Lync Server 2013](lync-server-2013-planning-for-persistent-chat-server.md) in the Planning documentation, [Deploying Persistent Chat Server in Lync Server 2013](lync-server-2013-deploying-persistent-chat-server.md) in the Deployment documentation, [Migration from Lync Server 2010, Group Chat or Office Communications Server 2007 R2 Group Chat to Lync Server 2013, Persistent Chat Server](migration-from-lync-server-2010-group-chat-or-office-communications-server-2007-r2-group-chat-to-lync-server-2013-persistent-chat-server.md) in the Migration documentation, and [Managing Lync Server 2013, Persistent Chat Server](managing-lync-server-2013-persistent-chat-server.md) in the Operations documentation, all of which provide instructions for setting up Persistent Chat Server.

  - The Persistent Chat Server Documentation.msi file (Windows Installer file) lets users access comprehensive offline documentation about Persistent Chat Server.

<div>

## Key Topology Changes for Persistent Chat Server

The following high-level changes for Persistent Chat Server include:

Persistent Chat Server is now a server role. In Microsoft Lync Server 2010, Group Chat Server was a third-party trusted application for Microsoft Lync Server 2010. Persistent Chat can be added to your Lync Server 2013 topology by using Topology Builder. In Lync Server 2013, Persistent Chat Server functionality is implemented by using three new server roles:

  - **PersistentChatService:** This is the front end role for Persistent Chat. In Standard Edition deployments, Persistent Chat Server Service Role is collocated on the Standard Edition server deployed by Bootstrapper, like any other Lync Server role. In Enterprise Edition deployments, Persistent Chat Service Role is deployed on stand-alone computers by Bootstrapper, like any other Lync Server role.

  - **PersistentChatStore:** Back End Server that corresponds to the Persistent Chat content database, where all the chat content is stored.

  - **PersistentChatComplianceStore:** Back End Server role that corresponds to the Persistent Chat Compliance database, where all compliance events are stored.

These Persistent Chat Server roles are optional, and are installed only by customers who want comprehensive Persistent Chat Server functionality. The **PersistentChatComplianceStore** role is needed only if you choose to deploy Persistent Chat Compliance.

The **PersistentChatService** role runs two services:

  - Persistent Chat service

  - Persistent Chat Compliance service

Having these services run on each Persistent Chat Server provides high availability for these services in a multiserver Persistent Chat Server pool.

Additionally, to support the file upload and download in Persistent Chat rooms, Persistent Chat Server includes a web service. Previously, this service was collocated on the Persistent Chat Server, Front End Server and required Internet Information Services (IIS) to be installed as a prerequisite. In Lync Server 2013 Persistent Chat Server, the File Upload/Download web service is collocated with the Lync Server 2013 Front End Server. As a side effect, Internet Information Services (IIS) is no longer a prerequisite for Persistent Chat Server. The File Upload/Download web service is identified as **PersistentChat** in the Internet Information Services (IIS) Manager.

<div>


> [!IMPORTANT]  
> The <STRONG>PersistentChatService</STRONG> role can run on the same server as a Lync Server 2013&nbsp;Front End Server only if that Front End Server is a Standard Edition&nbsp;Front End Server. The <STRONG>PersistentChatService</STRONG> role cannot run independently of a Lync Server 2013&nbsp;Front End Server. It can be installed only in the context of a Lync Server 2013 deployment.



</div>

In Persistent Chat Server, Lookup service has been eliminated. In Lync Server 2010, Group Chat, the Lookup service ran on every Group Chat Server Front End Server, and performed routing to one of the Channel Servers. Lync Server 2013 relies on routing by using contact objects, where each Persistent Chat Server pool is represented by a contact object that is used by the Lync Server Front End Servers to identify and route requests to an appropriate Persistent Chat Server pool, and to one of the computers running Persistent Chat Server in the pool.

In Lync Server 2013, there are Compliance service modifications:

  - In Lync Server 2010, the Compliance service ran stand-alone (non-collocated), and only on a single server. The Compliance service now runs on all the Persistent Chat Server Front End Servers, alongside the Persistent Chat service, and thereby provides high availability in a multiserver Persistent Chat Server pool. A single compliance adapter can be configured to extract data from the compliance database and into one of the other systems (XML file, Exchange-hosted archives, and so on). Persistent Chat Server includes an XML adapter.

  - The Message Queuing (also known as MSMQ) queue that is shared by the Persistent Chat service and the Compliance service on each Persistent Chat Server Front End Server is now a private queue shared only by the two services. All compliance services write to the same Compliance Back End database. They also all read from that database, for the purpose of sending the data to their instance of the adapter. The Compliance Back End Server is represented as a new Back End Server role.
    
    <div>
    

    > [!IMPORTANT]  
    > As in previous versions, all compliance data is processed only once. The data may be processed by any of the adapter instances invoked by the compliance service running on the various Lync Server 2013, Persistent Chat Server computers. In Persistent Chat Server, any one of the adapter instances could process the data.

    
    </div>
    
    <div>
    

    > [!NOTE]  
    > For information about installing Message Queuing, see <A href="lync-server-2013-install-operating-systems-and-prerequisite-software-on-servers.md">Install operating systems and prerequisite software on servers for Lync Server 2013</A> in the Deployment documentation.

    
    </div>

In Lync Server 2013, there are improvements in both high availability and disaster recovery:

  - High availability improvements: SQL Server mirroring is used to provide high availability for the Persistent Chat Server content database and Persistent Chat compliance database within a data center (in-site).

  - Disaster recovery improvements: Persistent Chat Server supports a stretched pool architecture that enables a single Persistent Chat Server pool to be stretched across two sites (that is, a single logical pool in the topology, with servers in the pool physically located across two sites). SQL Server Log Shipping is used for cross-site disaster recovery.

For more information about high availability and disaster recovery, see [Configuring Persistent Chat Server for high availability and disaster recovery in Lync Server 2013](lync-server-2013-configuring-persistent-chat-server-for-high-availability-and-disaster-recovery.md) in the Deployment documentation.

</div>

<div>

## Key Administration and Management Changes for Persistent Chat Server

Lync Server 2013 has made it easier to administer and manage Persistent Chat Server by providing:

  - Unified administration and management. Lync Server 2013 makes it easier to manage and administer Persistent Chat Server by using tools that are already familiar to Lync administrators. Persistent Chat Server includes an administrative user interface experience that is integrated with the Lync Server Control Panel, which addresses performance issues with the previous versions of the Group Chat Server user interface. Also, Persistent Chat Server includes a collection of Windows PowerShell cmdlets to administer and manage Persistent Chat Server categories, Persistent Chat Server rooms (including deleting rooms and purging obsolete content), and add-ins.

  - Simplified administration model. Lync Server 2013 has changed and simplified the Persistent Chat Server model by addressing the following key customer requirements:
    
      - Remove the complex nested hierarchies of scopes and categories.
    
      - Support to define deny lists as well as allowed lists (scopes) for current MindAlign customers who are planning to migrate to Persistent Chat Server.

</div>

<div>

## What’s Different about User Roles from Previous Group Chat Server Versions?

Lync Server 2010, Group Chat had a user administrator role, a chat room administrator role and a Lync Server administrator role that could manage add-ins. Persistent Chat Server simply provides a Persistent Chat Administrator role (which is similar to other Lync Server role-based access control (RBAC) roles). Anyone who is a member of this RBAC role can manage chat rooms, add-ins, and categories (and therefore gain user access for these categories), and configuration of the Persistent Chat Server pool.

</div>

<div>

## What’s Different about Chat Room Categories from Previous Group Chat Server Versions?

Chat room categories can no longer be nested, and the root category can no longer be modified. AllowedMembers/DeniedMembers comprise what a scope used to be in legacy Group Chat Server versions (except that it didn’t support specifying a Denied list). Scopes can no longer be overridden, because there are no nested categories. A Persistent Chat Administrator in Lync Server 2013 can create and manage chat room categories. As part of creating and managing chat room categories, a Persistent Chat Administrator can configure principals (Active Directory groups/containers/users) that have access to be members/creators of chat rooms of a particular category. A Persistent Chat Administrator can also add DeniedMembers to a category, and these become explicit exclusions to the allowed list. DeniedMembers override what’s in AllowedMembers.

</div>

<div>

## What’s Different about Chat Room Properties from Previous Group Chat Server Versions?

A new concept of open chat rooms exists in Lync Server 2013, Persistent Chat Server. All allowed members can join the chat room, without exclusive membership.

The following chat room properties that were included in previous versions of Persistent Chat Server have been eliminated:

  - Topic: A Room now only has a Description.

  - Create New Member list: In Persistent Chat Server, all chat rooms start with empty membership (and can maximize to a membership equaling the Allowed Members).

  - File Upload: Used to be a setting per chat room to control whether file upload/downloads were allowed. This is now set only the category level and applies to all rooms in that category.

  - Chat History: Used to be a setting per chat room to control if Chat History was enabled, but is now set only at the category level and applies to all rooms in that category.

  - Invites: A room always inherits the Invites setting for the category; or it can be turned off on the room. A room cannot turn on Invites if the category was previously set to Invites off.

</div>

<div>

## What’s Different about Policies from Previous Group Chat Server Versions?

Persistent Chat Server has a new Lync policy enabled with Persistent Chat, per user/pool/site/global settings. In the Lync 2013 client, the Persistent Chat environment is available only for users who are enabled by policy for Persistent Chat (either directly or through the pool/site/global setting).

Previous versions of Group Chat Server did not have any policies integrated into the Lync Server policies. On a per user and per category/room basis, by using the **Can Upload Files** per user feature, you could make the user a User administrator, a chat room administrator, or configure the user’s ability to upload files. The Persistent Chat Server **File Upload** feature is just per category.

</div>

<div>

## Logging

Logging for Persistent Chat Server and System Center Operations Manager is integrated into the Lync Server 2013 trace logging.

</div>

<div>

## See Also


[Planning for Persistent Chat Server in Lync Server 2013](lync-server-2013-planning-for-persistent-chat-server.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

