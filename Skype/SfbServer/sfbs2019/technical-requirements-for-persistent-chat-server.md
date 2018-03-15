---
title: "Technical requirements for Persistent Chat Server in Lync Server 2013"
ms.author: crowe
author: CarolynRowe
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 692b7d99-1bc9-4c99-a050-2bc2be8688b2
description: "In this articlePersistent Chat Server RequirementsPersistent Chat Server Database RequirementsPersistent Chat Server Certificate Requirements"
---

# Technical requirements for Persistent Chat Server in Lync Server 2013
[]
 **In this article**
  
[Persistent Chat Server Requirements](#sectionSection0)
  
[Persistent Chat Server Database Requirements](#sectionSection1)
  
[Persistent Chat Server Certificate Requirements](#sectionSection2)
  
Each computer that hosts Persistent Chat Server must have access to an existing Lync Server 2013 topology with the following components:
  
- **Lync Server 2013, Front End Server.** The Front End Server is the foundation for Session Initiation Protocol (SIP) routing, which makes communication between computers running Persistent Chat Server and the Persistent Chat functionality possible. Before you begin to deploy Persistent Chat Server, verify the deployment of Lync Server 2013, Standard Edition, or a Lync Server Front End pool and any other internal computers running Lync Server, as appropriate to your organization. 
    
The following sections describe the specific requirements for the Persistent Chat Server and the database that stores the Persistent Chat data.
  
## Persistent Chat Server Requirements
<a name="sectionSection0"> </a>

For details about the recommended hardware for deploying Lync Server and the latest version of Persistent Chat Server, see [Server hardware platforms for Lync Server 2013](server-hardware-platforms.md) in the Supportability documentation. 
  
For details about the server and tools operating system support for Lync Server and Persistent Chat Server, see [Server and tools operating system support in Lync Server 2013](server-and-tools-operating-system-support.md) in the Supportability documentation. 
  
For details about additional software required for deploying Persistent Chat Server, see the following table.
  
**Persistent Chat Server Software Prerequisites**

|**Software**|**Description**|
|:-----|:-----|
|Message Queuing  <br/> |Used by the Persistent Chat Server and Persistent Chat Compliance service, if deployed.  <br/> |
   
## Persistent Chat Server Database Requirements
<a name="sectionSection1"> </a>

Persistent Chat Server uses the Persistent Chat database to store chat history, configuration, and user provisioning data. Optionally, it uses the Persistent Chat compliance database to store compliance data.
  
> [!IMPORTANT]
> The Persistent Chat database (mgc) and the compliance database (mgccomp) can be located in the same instance of SQL Server or on different SQL Servers. 
  
To prepare a database server platform, be sure that each computer meets the hardware requirements, and then install the prerequisite software.
  
The server platform for the Persistent Chat database servers requires the same hardware as the Lync Server back-end database server. For details, see [Server hardware platforms for Lync Server 2013](server-hardware-platforms.md) in the Supportability documentation. 
  
On the database server, be sure that one of the following software applications is installed:
  
- Microsoft SQL Server 2012. For details about how to install Microsoft SQL Server 2012, see "Install SQL Server 2012" at [https://go.microsoft.com/fwlink/p/?LinkID=248559](https://go.microsoft.com/fwlink/p/?LinkID=248559).
    
- Microsoft SQL Server 2008 R2. For details about how to install Microsoft SQL Server 2008 R2, see "SQL Server Installation (SQL Server 2008 R2)" at [https://go.microsoft.com/fwlink/?LinkId=275702](https://go.microsoft.com/fwlink/?LinkId=275702).
    
## Persistent Chat Server Certificate Requirements
<a name="sectionSection2"> </a>

For details about acquiring certificates, creating the SQL Server database, and creating file stores, see [Deploying Lync Server 2013](deploying-lync-server-2013.md) in the Deployment documentation. 
  

