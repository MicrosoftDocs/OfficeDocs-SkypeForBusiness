---
title: "Hardware and software requirements for archiving in Skype for Business Server 2015"
ms.author: jambirk
author: jambirk
manager: serdars
ms.date: 12/20/2016
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 896d60e2-be4b-462d-8357-4cd307ab7304
description: "Summary: Read this topic to learn about hardware and software requirements for archiving in Skype for Business Server 2015."
---

# Hardware and software requirements for archiving in Skype for Business Server 2015
[]
 **Summary:** Read this topic to learn about hardware and software requirements for archiving in Skype for Business Server 2015.
  
Skype for Business Server 2015 archiving is now part of the Front End role, so you do not need to install a separate server. You do, however, need to consider the following requirements:
  
- Infrastructure requirements
    
- Prerequisite software requirements
    
- Data storage requirements
    
## Infrastructure requirements

Skype for Business Server Archiving infrastructure requirements are the same as for deployment of Skype for Business Server. For details, see [Requirements for your Skype for Business environment](../../plan-your-deployment/requirements-for-your-environment/requirements-for-your-environment.md). 
  
## Prerequisite software requirements

Archiving prerequisites for Skype for Business Server are simpler than earlier versions of Lync Server because of the following: 
  
- Because archiving is no longer a server role, you do not need to install a separate server for archiving. Instead, Unified Data Collection Agents are installed and activated automatically on every Enterprise Edition Front End pool and every Standard Edition Server. You will need to enable and publish your archiving topology by using Topology Builder.
    
- Archiving uses the Skype for Business Server file storage for temporary storage of meeting content files, so you do not set up a separate file store for archiving.
    
- In Skype for Business Server, Microsoft Message Queuing is not required.
    
## Data Storage requirements

You will need to set up the infrastructure for archiving storage. This includes choosing one or both of the following options:
  
- **Microsoft Exchange storage**. Meeting content files, such as PowerPoint presentations, are archived as attachments. If you want to store Skype for Business archive data with Exchange compliance data, you must use Exchange for your Exchange deployment and ensure that the maximum storage size supports storage of the meeting content files. You must deploy Exchange prior to deploying and enabling archiving using the Microsoft Exchange integration option. 
    
    If you choose to use Exchange storage, you do not need to deploy separate SQL Server databases for archiving, unless you have Skype for Business users who are not homed on your Exchange servers. If you deploy archiving using the Microsoft Exchange integration option, Skype for Business archive data is stored with Exchange compliance data only for the users who are homed on your Exchange servers. 
    
- **Skype for Business Server archiving storage**. To support users who are not homed on Exchange servers, or if you do not want to use the Microsoft Exchange integration option, you must deploy archiving storage using a SQL Server database. Skype for Business Server supports the following 64-bit versions of SQL Server:
    
  - Microsoft SQL Server 2008 R2 Enterprise
    
  - Microsoft SQL Server 2008 R2 Standard
    
  - Microsoft SQL Server 2012 Enterprise
    
  - Microsoft SQL Server 2012 Standard
    
  - Microsoft SQL Server 2014 Enterprise
    
  - Microsoft SQL Server 2014 Standard
    
    > [!NOTE]
    > Microsoft SQL Server Express versions are not supported for archiving. 32-bit versions of SQL Server are not supported. For additional SQL Server requirements and restrictions, see [Requirements for your Skype for Business environment](../../plan-your-deployment/requirements-for-your-environment/requirements-for-your-environment.md). 
  
    You must set up the SQL Server platforms prior to deploying and enabling archiving. If the account to be used to publish the topology has the appropriate administrator rights and permissions, you can create the Archiving database (LcsLog) when you publish your topology. You can also create the database later, included as part of the installation procedure. For details about SQL Server, see the [SQL Server TechCenter](https://go.microsoft.com/fwlink/p/?linkID=129045).
    
    The load increase for archiving can be significant. Therefore, you should ensure that disk space is adequate for Front End Servers on which archiving is enabled.
    

