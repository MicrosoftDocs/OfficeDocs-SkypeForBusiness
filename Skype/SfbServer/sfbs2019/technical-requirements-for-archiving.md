---
title: "Technical requirements for Archiving in Lync Server 2013"
ms.author: crowe
author: CarolynRowe
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 896d60e2-be4b-462d-8357-4cd307ab7304
description: "In this articleInfrastructure RequirementsArchiving PrerequisitesData Storage Requirements for Archiving"
---

# Technical requirements for Archiving in Lync Server 2013
[]
 **In this article**
  
[Infrastructure Requirements](#sectionSection0)
  
[Archiving Prerequisites](#sectionSection1)
  
[Data Storage Requirements for Archiving](#sectionSection2)
  
Lync Server 2013 technical requirements include the following:
  
- Infrastructure requirements.
    
- Prerequisite software that must be installed for Archiving.
    
- Data storage requirements for Archiving.
    
- Scaling requirements and considerations for your Archiving deployment.
    
- Performance requirements and considerations for your Archiving databases.
    
> [!NOTE]
> Scaling and performance information is not available in this Lync Server 2013 release. 
  
## Infrastructure Requirements
<a name="sectionSection0"> </a>

Lync Server 2013 Archiving infrastructure requirements are the same as for deployment of Lync Server 2013. For details, see [Determining your infrastructure requirements for Lync Server 2013](determining-your-infrastructure-requirements.md) in the Planning documentation. 
  
## Archiving Prerequisites
<a name="sectionSection1"> </a>

Lync Server 2013 streamlines prerequisites for Archiving because of the following: 
  
- Archiving Server is no longer a server role. Instead, Unified Data Collection Agents run on the Front End Servers in a pool and Standard Edition servers to capture data for Archiving, so you do not set up separate system platforms for Archiving.
    
- Archiving uses the Lync Server 2013 file storage for temporary storage of meeting content files, so you do not set up a separate file store for archiving.
    
- In Lync Server 2013, Message Queuing is not required.
    
## Data Storage Requirements for Archiving
<a name="sectionSection2"> </a>

Additionally, you need to set up the infrastructure for Archiving storage. This includes one or both of the following:
  
- **Microsoft Exchange storage**. Meeting content files, such as PowerPoint presentations, are archived as attachments. If you want to use Microsoft Exchange integration so that Lync archive data is stored with Exchange compliance data, you must use Exchange 2013 for your Exchange deployment and ensure that the maximum storage size supports storage of the meeting content files. If you deploy Archiving using the Microsoft Exchange integration option, Lync archive data is stored with Exchange 2013 compliance data only for the users who are homed on your Exchange 2013 servers. You must deploy Exchange 2013 prior to deploying and enabling Archiving using the Microsoft Exchange integration option. If you choose to use Exchange 2013 storage, you do not need to deploy separate SQL Server databases for Archiving, unless you have Lync users who are not homed on your Exchange 2013 servers.
    
- **SQL Server database storage for Archiving**. To support users who are not homed on Exchange 2013 servers, or if you do not want to use the Microsoft Exchange integration option, you must deploy Archiving storage using a SQL Server database. Lync Server 2013 supports the following 64-bit versions of SQL Server:
    
  - Microsoft SQL Server 2008 R2 Enterprise
    
  - Microsoft SQL Server 2008 R2 Standard
    
  - Microsoft SQL Server 2012 Enterprise
    
  - Microsoft SQL Server 2012 Standard
    
    > [!NOTE]
    > Microsoft SQL Server 2008 R2 Express and Microsoft SQL Server 2012 Express are not supported for Archiving. 32-bit versions of SQL Server are not supported. For additional SQL Server requirements and restrictions, see [Database software support in Lync Server 2013](database-software-support.md) in the Planning documentation or in the Supportability documentation. 
  
    You must set up the SQL Server platforms prior to deploying and enabling Archiving. If the account to be used to publish the topology has the appropriate administrator rights and permissions, you can create the Archiving database (LcsLog) when you publish your topology. You can also create the database later, including as part of the installation procedure. For details about SQL Server, see the SQL Server TechCenter at [https://go.microsoft.com/fwlink/p/?linkID=129045](https://go.microsoft.com/fwlink/p/?linkID=129045).
    

