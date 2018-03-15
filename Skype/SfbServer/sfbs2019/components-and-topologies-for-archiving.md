---
title: "Components and topologies for Archiving in Lync Server 2013"
ms.author: crowe
author: CarolynRowe
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 5893063d-a44a-4034-aba9-cbe883ecf710
description: "In this articleArchiving ComponentsSupported TopologiesSupported Collocation"
---

# Components and topologies for Archiving in Lync Server 2013
[]
 **In this article**
  
[Archiving Components](#sectionSection0)
  
[Supported Topologies](#sectionSection1)
  
[Supported Collocation](#sectionSection2)
  
If you want to archive Lync Server 2013 IM and conferencing content, you can implement Archiving in Lync Server.
  
## Archiving Components
<a name="sectionSection0"> </a>

The Archiving feature includes the following components:
  
- **Archiving agents**. Archiving agents (also known as unified data collection agents) are installed and activated automatically on every Front End pool and Standard Edition server. Although archiving agents are activated automatically, no messages are actually captured until Archiving is enabled and appropriately configured.
    
- **Archiving data storage**. Data storage for Lync Server 2013 can be either of the following: 
    
  - Exchange 2013 storage. If you enable the Microsoft Exchange integration option, user mailboxes homed on the Exchange 2013 server use Exchange 2013 storage for archived data, but only if the mailboxes have been put on In-Place Hold.
    
  - SQL Server storage. If you have users in your deployment who are homed on Lync Server 2013, you can set up Archiving databases that run a supported version of SQL Server to enable archiving for those users.
    
Archiving also requires file storage, but Archiving uses the same file storage as the Front End Servers or Standard Edition server.
  
For a list of hardware and software requirements for Archiving, see [Supported hardware for Lync Server 2013](supported-hardware.md) and [Server software and infrastructure support in Lync Server 2013](server-software-and-infrastructure-support.md) in the Supportability documentation. 
  
## Supported Topologies
<a name="sectionSection1"> </a>

You deploy Archiving in each pool that has users that require archiving support. Archiving runs on Front End Servers in Enterprise Edition pools and on Standard Edition servers. Archiving data storage can be the following:
  
- Integrated with Exchange 2013 storage
    
- Deployed using separate SQL Server databases
    
If your Exchange 2013 deployment does not include all users in your Lync Server deployment, you must use Microsoft Exchange integration for the users whose mailboxes are home on Exchange 2013 servers, and you must deploy separate SQL Server databases for all other Lync users to use for archiving.
  
## Supported Collocation
<a name="sectionSection2"> </a>

Lync Server 2013 supports a variety of collocation scenarios, allowing you flexibility to save hardware costs by running multiple components on one server (if you have a small organization), or to run individual components on different servers (if you have a larger organization that needs scalability and performance). Scalability factors should certainly be considered before you decide whether to collocate components.
  
Archiving is deployed on the Front End Servers of a pool or Standard Edition servers. For details about components that can be collocated there, see [Supported server collocation in Lync Server 2013](supported-server-collocation.md) in the Supportability documentation. 
  
If you use separate SQL Server databases for Archiving, instead of or in addition to integrating storage with Exchange 2013 storage, you can collocate the Archiving database with any of the following:
  
- Monitoring database
    
- Back-end database of an Enterprise Edition Front End pool
    
> [!NOTE]
> The server hosting the Archiving database can host other databases. However, when you consider collocating the Archiving database with other databases, be aware that if you are archiving the messages of more than a few users, the disk space needed by the Archiving database can grow very large. For this reason, we do not recommend collocating the Archiving database with the back-end database. 
  
If you collocate the Archiving database with the Monitoring database, back-end database, or both of these databases, you can either use a single SQL instance for any or all of the databases, or you can use a separate SQL instance for each database, with the following limitation: 
  
- Each SQL instance can contain only a single back-end database, single Monitoring database, and single Archiving database.
    
For details about collocation of all server roles and databases, see [Supported server collocation in Lync Server 2013](supported-server-collocation.md) in the Supportability documentation. 
  

