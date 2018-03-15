---
title: "Preparing the infrastructure and systems for Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 1254ee38-0679-4714-b293-1050f107c158
description: "Deployment of Lync Server 2013 requires the use of Topology Builder to define and publish the topology design. To identify the components required for your topology, you use Topology Builder to create and save a topology design. Prior to publishing your topology in Topology Builder, you do the following:"
---

# Preparing the infrastructure and systems for Lync Server 2013
[]
Deployment of Lync Server 2013 requires the use of Topology Builder to define and publish the topology design. To identify the components required for your topology, you use Topology Builder to create and save a topology design. Prior to publishing your topology in Topology Builder, you do the following:
  
- Acquire and install the hardware for each component in the topology design that you created and saved by using Topology Builder, including all required computers (servers running Lync Server 2013, database servers, servers running Internet Information Services (IIS), and reverse proxy servers, as appropriate), network adapters, hardware load balancers, and storage devices (such as file servers). For details about how to define a topology that specifies the components needed for your deployment, see [Defining and configuring the topology in Lync Server 2013](defining-and-configuring-the-topology.md). For details about hardware requirements for servers, see [Supported hardware for Lync Server 2013](supported-hardware.md) in the Supportability documentation. 
    
- Make sure that the networking infrastructure meets requirements. For details, see [Network infrastructure requirements for Lync Server 2013](network-infrastructure-requirements.md) in the Planning documentation. 
    
- Set up Active Directory Domain Services. To publish and enable the topology, you need the internal servers to be represented by computer accounts in AD DS. This is accomplished by joining the computers to AD DS. For details about preparing AD DS, see [Preparing Active Directory Domain Services for Lync Server 2013](preparing-active-directory-domain-services-for-lync-server-2013.md).
    
- Create a file share. Standard Edition servers can host the file share for the required file, while in an Enterprise deployment the file share cannot be hosted on the front end server. The permissions and group memberships required for deploying and setting the access control list (ACL) on the folder and the share must be set correctly for Topology Builder to complete successfully. You should make sure that the person running Topology Builder has the following permissions and group memberships:
    
  - Member of Local Administrators
    
  - Member of Domain Users
    
  - Full Control on share and folder of file store
    
- For Enterprise Edition, install and configure SQL Server. For SQL Server setup to succeed the SQL Server-based server must be online and the person publishing the topology be a local admin on the SQL Server and must be a member of the SQL Server sysadmin group on the SQL Server instance.
    
After you complete all of the preparation tasks as described in this topic, but prior to publishing the topology, you also need to perform the other preparation tasks, including installing the Windows operating systems and other prerequisite software, setting up IIS, and configuring DNS. For details about these tasks, see [System requirements for servers running Lync Server 2013](system-requirements-for-servers-running-lync-server-2013.md), [Configure IIS for Lync Server 2013](configure-iis.md), and [Preparing the infrastructure and systems for Lync Server 2013](preparing-the-infrastructure-and-systems.md). Additionally, you should familiarize yourself with the clients and client requirements. For details, see [Deploying clients and devices in Lync Server 2013](deploying-clients-and-devices.md).
  
## In this section

- [Hardware setup for Lync Server 2013](hardware-setup.md)
    
- [Software setup for Lync Server 2013](software-setup.md)
    
- [Preparing Active Directory Domain Services for Lync Server 2013](preparing-active-directory-domain-services-for-lync-server-2013.md)
    
- [Configure SQL Server for Lync Server 2013](configure-sql-server-for-lync-server-2013.md)
    
- [Configure DNS records in Lync Server 2013 for a Front End pool or Standard Edition server](configure-dns-records-for-a-front-end-pool-or-standard-edition-server.md)
    
- [Install Lync Server 2013 administrative tools](install-lync-server-administrative-tools.md)
    

