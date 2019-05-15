---
title: 'Lync Server 2013: Deploying Persistent Chat Server'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Deploying Persistent Chat Server
ms:assetid: e3b930fb-6855-47f0-b6b3-7dfae386540d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205357(v=OCS.15)
ms:contentKeyID: 48185717
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Deploying Persistent Chat Server in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-03-31_

Lync Server 2013, Persistent Chat Server is part of the Lync Server 2013 infrastructure.

Deploying Persistent Chat Server requires that you:

  - Use Topology Builder to define, or import, and subsequently publish your topology and the components that you want to deploy.

  - Prepare your environment for deploying Persistent Chat Server components.

  - Install and configure Persistent Chat Server components for your deployment.

Persistent Chat Server is available with Lync Server 2013 Enterprise Edition as a separate pool (not collocated with the Enterprise Edition Front End Servers). Persistent Chat Server requires a SQL Server Back End Server in your Enterprise Edition pool to store the chat room content and other relevant metadata. We recommend that you install the **PersistentChatStore** on a dedicated SQL Server Back End Server, although collocating Lync Server 2013 Back End Server and **PersistentChatStore** on the same SQL Server instance is supported.

Persistent Chat Server can also be deployed with Lync Server 2013 Standard Edition. In this case, the **PersistentChatService** Front End Server is collocated on the Standard Edition computer, and the **PersistentChatStore** Back End Server can be deployed on the local SQL Server Express instance.

For details about supported colocation configurations, see [Supported server collocation in Lync Server 2013](lync-server-2013-supported-server-collocation.md).

<div>


> [!IMPORTANT]  
> We do not support high availability for Persistent Chat Server&nbsp;Standard Edition. Performance and scale will be limited. Furthermore, we support only new Persistent Chat Server&nbsp;Standard Edition server. We do not support upgrading Lync Server 2010, Group Chat Server to a Lync Server 2013&nbsp;Persistent Chat Server&nbsp;Standard Edition.



</div>

If your organization requires compliance support, you can install the Persistent Chat Server Compliance service on the Persistent Chat Server Front End Server. A separate database is required for compliance.

At a minimum, each topology requires a server with Lync Server 2013 installed and a server with SQL Server database software installed.

Use Topology Builder to add Persistent Chat Server to your Lync Server 2013 deployments. You can choose to add one or more Persistent Chat Server pools using Topology Builder. Follow the same deployment instructions for deploying multiple Persistent Chat Server pools as you would for any pool. For details, see [Deploying Lync Server 2013](lync-server-2013-deploying-lync-server.md) in the Deployment documentation.

For details about available topologies and the technical and software requirements for installing Persistent Chat Server, see [Planning for Persistent Chat Server in Lync Server 2013](lync-server-2013-planning-for-persistent-chat-server.md) in the Planning documentation, [How Persistent Chat Server works in Lync Server 2013](lync-server-2013-how-persistent-chat-server-works.md) in the Planning documentation, Deployment documentation, or Operations documentation, and [Supported hardware for Lync Server 2013](lync-server-2013-supported-hardware.md) in the Supportability documentation.

For details about acquiring certificates, creating the SQL Server database, and creating file stores, see [Deploying Lync Server 2013](lync-server-2013-deploying-lync-server.md) in the Deployment documentation.

A single Persistent Chat Server Front End Server can support 20,000 active users. You can have a Persistent Chat Server pool with up to 4 active Front End Servers supporting a total of 80,000 concurrent users.

Persistent Chat Server is also supported on a virtual server. The virtual server can support up to 20,000 concurrent users if it matches the specifications of the physical server.

<div>


> [!IMPORTANT]  
> Persistent Chat Server must be installed on an NTFS file system to help enforce file system security. FAT32 is not a supported file system for Persistent Chat Server.



</div>

<div>

## In This Section

  - [How Persistent Chat Server works in Lync Server 2013](lync-server-2013-how-persistent-chat-server-works.md)

  - [Deployment checklist for Persistent Chat Server in Lync Server 2013](lync-server-2013-deployment-checklist-for-persistent-chat-server.md)

  - [Technical requirements for Persistent Chat Server in Lync Server 2013](lync-server-2013-technical-requirements-for-persistent-chat-server.md)

  - [Setting up systems and infrastructure for Persistent Chat Server in Lync Server 2013](lync-server-2013-setting-up-systems-and-infrastructure-for-persistent-chat-server.md)

  - [Adding Persistent Chat Server to your deployment in Lync Server 2013](lync-server-2013-adding-persistent-chat-server-to-your-deployment.md)

  - [Installing Persistent Chat Server in Lync Server 2013](lync-server-2013-installing-persistent-chat-server.md)

  - [Adding a Persistent Chat administrator in Lync Server 2013](lync-server-2013-adding-a-persistent-chat-administrator.md)

  - [Configuring Persistent Chat Server in Lync Server 2013](lync-server-2013-configuring-persistent-chat-server.md)

  - [Configuring Persistent Chat Server by using Windows PowerShell cmdlets](configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md)

  - [Troubleshooting Persistent Chat Server configuration using Windows PowerShell cmdlets in Lync Server 2013](lync-server-2013-troubleshooting-persistent-chat-server-configuration-using-windows-powershell-cmdlets.md)

  - [Configuring Persistent Chat Server for high availability and disaster recovery in Lync Server 2013](lync-server-2013-configuring-persistent-chat-server-for-high-availability-and-disaster-recovery.md)

  - [Failing over and failing back Persistent Chat Server in Lync Server 2013](lync-server-2013-failing-over-and-failing-back-persistent-chat-server.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

