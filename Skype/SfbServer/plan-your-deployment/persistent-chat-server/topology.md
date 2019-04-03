---
title: "Plan Persistent Chat Server topology"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 5/17/2016
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 6a0a14a0-baad-44e9-b26e-4d192c0a0e70
description: "Summary: Read this topic to learn about Persistent Chat Server components and topologies in Skype for Business Server 2015."
---

# Plan Persistent Chat Server topology
 
**Summary:** Read this topic to learn about Persistent Chat Server components and topologies in Skype for Business Server 2015.
  
Persistent Chat Server supports both single-server and multiple-server configurations. You can install Persistent Chat Server on either a Skype for Business Server 2015 Enterprise Edition or Standard Edition Server. 

> [!NOTE] 
> Persistent chat is available in Skype for Business Server 2015 but is no longer supported in Skype for Business Server 2019. The same functionality is available in Teams. For more information, see [Journey from Skype for Business to Microsoft Teams](/microsoftteams/journey-skypeforbusiness-teams). If you need to use Persistent chat, your choices are to either migrate users requiring this functionality to Teams, or to continue using Skype for Business Server 2015. 
  
## Persistent Chat Server components

Persistent Chat Server consists of the following components:
  
- One or more computers running Persistent Chat Server and providing the following services:
    
  - Persistent Chat service
    
  - Compliance service, which is turned on if compliance is enabled
    
- One or more servers (more than one if mirroring is used) running the SQL Server back-end database for hosting the Persistent Chat content database where chat room content, rooms, and categories are stored.
    
    > [!NOTE]
    > The back-end database stores chat history data, including information about categories and Persistent Chat rooms that are created. 
  
- If compliance is enabled, one or more servers (more than one if mirroring is used) running the SQL Server back-end database for hosting the Persistent Chat Compliance database, where compliance events and chat content for the purpose of compliance are stored.
    
For details about hardware and software requirements for Persistent Chat Server, see [Server requirements for Skype for Business Server 2015](../../plan-your-deployment/requirements-for-your-environment/server-requirements.md) and [Hardware and software requirements for Persistent Chat Server in Skype for Business Server 2015](hardware-and-software-requirements.md). 
  
## Persistent Chat Server topologies

You can deploy Persistent Chat Server in single-server or multiple-server pools, and with single-pool or multiple-pool topology. Persistent Chat Server supports the following topologies:
  
-  Standard Edition Server with Persistent Chat Server collocated on the Front End Server
    
-  Standard Edition Server with Persistent Chat Server on a separate server
    
-  Enterprise Edition Server with a single Persistent Chat Server on a separate server
    
-  Enterprise Edition Server with more than one Persistent Chat Server on separate servers
    
Although you can deploy Persistent Chat Server on a Standard Edition Server, be aware that performance and scale will be affected, and high availability is not an option. Therefore, it is recommended that you deploy Persistent Chat on a Standard Edition Server primarily for proof of concept and evaluation purposes. 
  
Skype for Business Server 2015 supports a variety of collocation scenarios, providing you the flexibility to save hardware costs by running multiple components on one server (if you have a small organization), or to run individual components on different servers (if you have a larger organization that needs scalability and performance). You should consider scalability factors before deciding whether to collocate components. Collocation scenarios differ for Skype for Business Server 2015 Enterprise Edition and Standard Edition servers. 
  
The following sections describe the topologies in more detail, including collocation scenarios and options for the back-end database servers. For details about collocation of all server roles and databases, see [Topology Basics for Skype for Business Server 2015](../../plan-your-deployment/topology-basics/topology-basics.md).
  
### Standard Edition Server with Persistent Chat Server collocated on the Front End Server

With Standard Edition, you can collocate Persistent Chat on the Front End Server. This is the simplest and most basic configuration. You must make sure that the existing Front End Server has enough capacity in terms of physical resources: CPU, memory, disk space, and so on.
  
In addition, you can collocate the Persistent Chat Server back-end server and the Persistent Chat Compliance database (if enabled) on the local SQL Server Express back-end server. You can also choose to use a separate SQL Server with a dedicated instance. 
  
> [!IMPORTANT]
> You cannot add additional servers to a Persistent Chat Server pool if the first Persistent Chat Server is collocated with a Standard Edition Front End Server. It is recommended that you install the first server as a standalone instance so that you can add more servers later, if needed. 
  
### Standard Edition Server with Persistent Chat Server installed on a separate server

With Standard Edition, you can install Persistent Chat Server as a standalone instance and add more servers later if needed. 
  
You can collocate the Persistent Chat Server back-end server and the Persistent Chat Compliance database (if enabled) on the local SQL Server Express back-end server. You can also choose to use a separate SQL Server with a dedicated instance. 
  
### Enterprise Edition Server with a single Persistent Chat Server

With Enterprise Edition, you must install the Persistent Chat Server on a separate computer. That is, you cannot collocate the Persistent Chat Server on the Enterprise Edition Front End Server. This deployment requires a separate server that runs Persistent Chat Server and the Compliance service (if enabled).
  
You can, however, collocate the SQL Server database for Persistent Chat Server on the back-end database of an Enterprise Edition Front End pool.
  
> [!NOTE]
> If you plan to use SQL AlwaysOn Availability Groups for HA DR, note that it is not supported for Persistent Chat Server databases. 
  
If you collocate the Persistent Chat database with the back-end database, you can either use a single instance of SQL Server for any or all of the databases, or you can use a separate instance of SQL Server for each database.
  
> [!IMPORTANT]
> The server hosting the Persistent Chat database can host other databases. However, when you consider collocating the Persistent Chat database with other databases, be aware that if you are storing the messages of more than a few users, the disk space needed by the Persistent Chat database can grow very large. For this reason, we do not recommend collocating the Persistent Chat database with the back-end database. 
  
The following figure shows all components of a topology for a single Persistent Chat Server with compliance enabled (optional).
  
**Single Server Topology**

![Persistent Chat Server - Single Server Topology](../../media/e1b39c28-8a4d-4c03-983b-4392889c2d14.png)
  
### Enterprise Edition Server with multiple Persistent Chat Servers

With Enterprise Edition, you can deploy a multiple-server topology for greater capacity and reliability. A multiple-server topology is the same as the single-server topology except that multiple servers host Persistent Chat Server, and can scale higher. The multiple-server topology can include as many as four active computers running Persistent Chat Server (high availability and disaster recovery configurations will allow up to eight, but only four can be active and the remaining four on standby). Each server can support as many as 20,000 concurrent users, for a total of 80,000 concurrent users connected to a Persistent Chat Server pool with 4 servers. Multiple computers running Persistent Chat Server should reside in the same Active Directory Domain Services domain as Skype for Business Server and the Compliance service.
  
The following figure shows all the components of a multiple-server topology with multiple computers running Persistent Chat Server, the optional Compliance service, and a separate compliance database.
  
**Multiple Server Topology**

![Persistent Chat Server - Multiple Server Topology](../../media/8fc20997-7acc-46ea-8dea-11239ffd9458.png)
  
Multiple-server topologies provide pooling of server functionality. In a server pool, the Persistent Chat services communicate and share data. For example, chat history that was originally posted to one Persistent Chat service is available from any Persistent Chat service in the system. A file that is uploaded through one Persistent Chat service can be accessed by any Persistent Chat service. Users can be connected to different Persistent Chat Server Front End Servers and can be communicating with each other. The default port of TCP 8011 connects a server to a server pool, and is used by the Persistent Chat services to communicate between themselves, or for administrative purposes.
  
For example, in a four-server Persistent Chat Server deployment, where 80,000 users can be simultaneously signed in to Persistent Chat, the load is distributed evenly at 20,000 users per server. If one server becomes unavailable, the users who are connected to that server will lose their access to Persistent Chat Server. The disconnected users will be automatically transferred to the remaining servers until the unavailable server is restored. 
  

