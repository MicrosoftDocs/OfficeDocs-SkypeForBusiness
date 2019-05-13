---
title: 'Lync Server 2013: Hardware setup'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Hardware setup
ms:assetid: 37a9f295-cde3-4beb-9a6a-2580082798ab
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425852(v=OCS.15)
ms:contentKeyID: 48183834
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Hardware setup for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

Setting up the hardware and other components required in the infrastructure that you need to implement your topology requires that, prior to publishing your topology in Topology Builder, you do the following:

  - Install the hardware for each component in the topology design that you created and saved by using Topology Builder, including all required computers (servers running Lync Server 2013, database servers, servers running Internet Information Services (IIS), and reverse proxy servers, as appropriate), network adapters, hardware load balancers, and storage devices (such as file servers). Confirm that you have followed the recommendations for the number and speed for network adapters. If you will be using hardware load balancers, make sure that you have the proper information from the vendor to configure them for use with Lync Server 2013. If you will be using a file server or other server to house the file share required by Lync Server, make sure that the server is available and ready for the configuration of the file share. For details about how to define a topology that specifies the components needed for your deployment, see [Defining and configuring the topology in Lync Server 2013](lync-server-2013-defining-and-configuring-the-topology.md). For details about hardware requirements for servers, see [Supported hardware for Lync Server 2013](lync-server-2013-supported-hardware.md) in the Supportability documentation.

  - Make sure that the networking infrastructure meets requirements. For details, see [Network infrastructure requirements for Lync Server 2013](lync-server-2013-network-infrastructure-requirements.md) in the Planning documentation.

  - Set up Active Directory Domain Services. Setting up AD DS includes preparing AD DS and defining all components that you want to deploy in AD DS. For details about preparing AD DS, see [Preparing Active Directory Domain Services for Lync Server 2013](lync-server-2013-preparing-active-directory-domain-services.md) in the Deployment documentation.

  - Set up the required permissions for creating the file share. Permissions for use of file shares by Lync Server 2013 are automatically configured by Topology Builder when you publish your topology. However, the user account used to publish the topology must have full control (read/write/modify) on the file share in order for Topology Builder to configure the required permissions. To make sure that the file share can be managed properly during the Topology Builder publishing process, the user or domain group that the user is a member of should be made a member of the local Administrators group on the machine where the file share is located. In a multi-domain scenario, Domain A user or group should be made a member of the local Administrators group on the machine in Domain B where the file share will be located.
    
    For details about updating using file shares in a Distributed File System (DFS), see [Configure file storage for Lync Server 2013](lync-server-2013-configure-dfs-file-storage.md).
    
    <div>
    

    > [!WARNING]  
    > The file share for Lync Server 2013, Enterprise Edition cannot be located on the Front End Server.

    
    </div>

  - Install and set up the hardware load balancer for Web Services. With Domain Name System (DNS) load balancing deployed, you still need to also use hardware load balancers for these pools, but only for HTTP/HTTPS traffic. The hardware load balancer is used for HTTPS traffic from clients over ports 443 and 80. Although you still need hardware load balancers for these pools, their setup and administration will be primarily for HTTP/HTTPS traffic, which the administrators of the hardware load balancers are accustomed to.

After you complete all of the preparation tasks as described in this topic, but prior to publishing the topology, you also need to:

  - [Install operating systems and prerequisite software on servers for Lync Server 2013](lync-server-2013-install-operating-systems-and-prerequisite-software-on-servers.md)

  - [Configure IIS for Lync Server 2013](lync-server-2013-configure-iis.md)

  - [Configure SQL Server for Lync Server 2013](lync-server-2013-configure-sql-server-for-lync-server.md)

  - [Configure DNS records in Lync Server 2013 for a Front End pool or Standard Edition server](lync-server-2013-configure-dns-records-for-a-front-end-pool-or-standard-edition-server.md)

</div>

<span> </span>

</div>

</div>

</div>

