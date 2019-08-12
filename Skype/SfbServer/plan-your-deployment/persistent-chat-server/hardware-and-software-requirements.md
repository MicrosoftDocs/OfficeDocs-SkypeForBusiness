---
title: "Hardware and software requirements for Persistent Chat Server in Skype for Business Server 2015"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 7/19/2018
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 692b7d99-1bc9-4c99-a050-2bc2be8688b2
description: "Summary: Read this topic to learn about hardware and software requirements for Persistent Chat Server in Skype for Business Server 2015."
---

# Hardware and software requirements for Persistent Chat Server in Skype for Business Server 2015
 
**Summary:** Read this topic to learn about hardware and software requirements for Persistent Chat Server in Skype for Business Server 2015.
  
Persistent Chat Server can be installed with Skype for Business Server 2015 Enterprise Edition or Standard Edition. Requirements depend on which edition of Skype for Business Server 2015 you have installed, and the performance requirements of your business. Enterprise Edition can support up to 80,000 concurrent users; Standard Edition can support up to 20,000 concurrent users. Persistent Chat consists of a front-end component as well as a back-end SQL database component.
  
Before you deploy Persistent Chat Server, you must ensure that the following hardware and software requirements are met:
  
- Hardware that meets minimum requirements to support Skype for Business Server 2015, Persistent Chat Server, database servers, and file servers. For more information, see [Server requirements for Skype for Business Server 2015](../../plan-your-deployment/requirements-for-your-environment/server-requirements.md).
    
- Supported operating system and database software.
    
    For details about supported operating systems and database software, and Windows update requirements, see [Server requirements for Skype for Business Server 2015](../../plan-your-deployment/requirements-for-your-environment/server-requirements.md).
    
- Skype for Business Server 2015 Front End Server. The Front End Server is the foundation for Session Initiation Protocol (SIP) routing, which makes communication between computers running Persistent Chat Server and the Persistent Chat functionality possible. 
    
- Message Queuing software. Used by the Persistent Chat Server and Persistent Chat Compliance service, if deployed.
    
The following sections describe the specific requirements for Persistent Chat Server and the database that stores the Persistent Chat data.

> [!NOTE] 
> Persistent chat is available in Skype for Business Server 2015 but is no longer supported in Skype for Business Server 2019. The same functionality is available in Teams. For more information, see [Getting started with your Microsoft Teams upgrade](/microsoftteams/upgrade-start-here). If you need to use Persistent chat, your choices are to either migrate users requiring this functionality to Teams, or to continue using Skype for Business Server 2015. 
  
## Front End Server requirements

Front End Server requirements depend on whether you are deploying Persistent Chat Server with Skype for Business Server 2015 Enterprise Edition or Standard Edition.
  
- If you are deploying Persistent Chat Server with Skype for Business Server 2015 Enterprise Edition, you can deploy the Persistent Chat Server Front End Server on one or more standalone computers in the Enterprise Edition pool. You cannot collocate the Persistent Chat Front End Servers on the Skype for Business Server 2015 Front End Server. 
    
    A single Persistent Chat Server Front End Server can support 20,000 active users. You can have a Persistent Chat Server pool with up to 4 active front ends thereby supporting a total of 80,000 concurrent users. 
    
- If you are deploying Persistent Chat Server with Skype for Business Server 2015 Standard Edition, you can collocate Persistent Chat with the Front End Server. This single server deployment can support up to 20,000 users. 
    
## Persistent Chat Server database requirements

Persistent Chat Server requires SQL Server database software to store chat room history and content, configuration data, user provisioning data, and other relevant metadata. Optionally, it uses the Persistent Chat Compliance database to store compliance data. Persistent Chat databases can be collocated on the same SQL Server, or even the same SQL instance, as the back-end databases. 
  
- If you are installing Persistent Chat Server with Skype for Business Server 2015 Enterprise Edition, to ensure optimum performance, it is recommended that you install the Persistent Chat file store.
    
- If you are installing Persistent Chat Server with Skype for Business Server 2015 Standard edition, you can deploy the Persistent Chat Store Back End Server on the local SQL Server Express instance.
    
- The Persistent Chat database (mgc) and the compliance database (mgccomp) can be located in the same instance of SQL Server or on different SQL Servers.
    
To prepare a database server platform, be sure that each computer meets the hardware requirements, and then install the prerequisite software. The server platform for the Persistent Chat database servers requires the same hardware as the Skype for Business Server 2015 back-end database server. For details, see [Server requirements for Skype for Business Server 2015](../../plan-your-deployment/requirements-for-your-environment/server-requirements.md).
  
On the database server, be sure that one of the following software applications is installed:

- Microsoft SQL Server 2017 with the latest service pack.

- Microsoft SQL Server 2016 with Service Pack 1, and you must run with Skype for Business Server Cumulative Update 7 or later releases. We recommended running SQL Server 2016 with the latest service pack. For details about how to install Microsoft SQL Server 2016, see [Install SQL Server 2016](https://docs.microsoft.com/pt-pt/sql/database-engine/install-windows/install-sql-server?view=sql-server-2016).

- Microsoft SQL Server 2014, and you must run with Skype for Business Server Cumulative Update 6 or later releases. We recommended running SQL Server 2014 with the latest service pack. For details about how to install Microsoft SQL Server 2014, see [Install SQL Server 2014](https://docs.microsoft.com/pt-pt/sql/database-engine/install-windows/install-sql-server?view=sql-server-2014).

- Microsoft SQL Server 2012 (64-bit edition), and we recommended running with the latest service pack. For details about how to install Microsoft SQL Server 2012, see [Install SQL Server 2012](https://go.microsoft.com/fwlink/p/?LinkID=248559).

## Persistent Chat Server certificate requirements

For details about acquiring certificates, creating the SQL Server database, and creating file stores, see [Deploy Skype for Business Server 2015](../../deploy/deploy.md). 
  
## For more information

For more information about hardware and software requirements, see the following topics:
  
- [Server requirements for Skype for Business Server 2015](../../plan-your-deployment/requirements-for-your-environment/server-requirements.md)
    
- [Environmental requirements for Skype for Business Server 2015](../../plan-your-deployment/requirements-for-your-environment/environmental-requirements.md)
    

