---
title: "Preparing to restore Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 857e4e02-908e-433a-96c6-be1795a9cb61
description: "In this articleDetermining What to RestoreGathering Hardware, Software, and ToolsPreparing to Restore a Server"
---

# Preparing to restore Lync Server 2013
[]
 **In this article**
  
[Determining What to Restore](#sectionSection0)
  
[Gathering Hardware, Software, and Tools](#sectionSection1)
  
[Preparing to Restore a Server](#sectionSection2)
  
Before you begin restoring servers and databases after a failure, you need to determine the following:
  
- What needs to be restored.
    
- The hardware, software, data, and tools you need for restoration.
    
## Determining What to Restore
<a name="sectionSection0"> </a>

This topic describes how to restore Lync Server outages that occur at the server, pool, or Central Management store level. If the Central Management store fails, your Lync Server deployment continues to function, but you cannot make any configuration changes. If a Back End Server or Standard Edition server fails, the user pool stops functioning. If any other server fails, the magnitude of the failure depends on the server role the server is running and whether the server hosts one or more databases.
  
**What to Restore**

|**If this failed**|**See this section:**|
|:-----|:-----|
|Standard Edition server  <br/> |[Restoring a Standard Edition server in Lync Server 2013](restoring-a-standard-edition-server.md) <br/> |
|Central Management store  <br/> |[Restoring the server hosting the Central Management store in Lync Server 2013](restoring-the-server-hosting-the-central-management-store.md) <br/> |
|Enterprise Edition Back End  <br/> |[Restoring an Enterprise Edition Back End Server in Lync Server 2013](restoring-an-enterprise-edition-back-end-server.md) <br/> |
|Enterprise Edition Mirrored Back End Primary Server  <br/> |[Restoring a mirrored Enterprise Edition Back End Server in Lync Server 2013 - primary](restoring-a-mirrored-enterprise-edition-back-end-serverprimary.md) <br/> |
|Enterprise Edition Mirrored Back End Secondary Server  <br/> |[Restoring a mirrored Enterprise Edition Back End Server in Lync Server 2013 - mirror](restoring-a-mirrored-enterprise-edition-back-end-servermirror.md) <br/> |
|Any Enterprise Edition server running a server role, such as a Front End Server, Edge Server, Director, Mediation Server,.or Persistent Chat Server.  <br/> |[Restoring an Enterprise Edition member server in Lync Server 2013](restoring-an-enterprise-edition-member-server.md) <br/> |
|An entire Lync Server pool  <br/> |[Restoring a Lync Server pool in Lync Server 2013](restoring-a-lync-server-pool.md) <br/> |
|Enterprise Edition File Store  <br/> |[Restoring a file store in Lync Server 2013](restoring-a-file-store.md) <br/> |
|A standalone Monitoring database or Archiving database  <br/> |[Restoring monitoring or archiving data in Lync Server 2013](restoring-monitoring-or-archiving-data.md) <br/> |
|A stand-alone Persistent Chat database  <br/> |[Restoring Persistent Chat data in Lync Server 2013](restoring-persistent-chat-data.md) <br/> |
   
## Gathering Hardware, Software, and Tools
<a name="sectionSection1"> </a>

When you restore a server, you need to start with a new or clean computer. Additionally, you must have the following hardware and software available:
  
- A clean or new server with the same fully qualified domain name (FQDN) as the server that failed.
    
    > [!IMPORTANT]
    > When you install the operating system, make sure that you do not delete the computer account in Active Directory Domain Services, and verify that the group permissions for the account are retained. 
  
- Installation software for the operating system. To install the operating system, use the server deployment procedures and configurations established by your organization. You should have these procedures and configuration requirements available when you restore service.
    
- Installation software for SQL Server 2012 or SQL Server 2008 R2. To install a database server, use the appropriate version of SQL Server and the database server deployment procedures and configurations established by your organization. You should have these procedures and configuration requirements available when you restore service.
    
    > [!NOTE]
    > The Lync Server Deployment Wizard automatically installs SQL Server 2012 Express on each Standard Edition server and on any other Lync Server server when a local configuration store is installed, unless you have preinstalled SQL Server 2012 or SQL Server 2008 R2 on the server. 
  
- Software for taking system images.
    
    > [!TIP]
    > We recommend that you take an image copy of the system after you install the operating system and SQL Server, and before you start restoration, so that you can use this image as a rollback point in case something goes wrong during restoration. 
  
- Lync Server 2013 installation software. The Lync Server Deployment Wizard is located in the Lync Server installation folder or media at \setup\amd64\Setup.exe.
    
During restoration, you use the following tools:
  
- Lync Server Management Shell cmdlets
    
- Import-CsUserData
    
- Tools for restoring Windows folders
    
- Topology Builder
    
- SQL Server database utilities, such as SQL Server Management Studio
    
## Preparing to Restore a Server
<a name="sectionSection2"> </a>

Before you restore the server, you must perform the following steps:
  
1. Install the operating system.
    
2. If the server is a Back End Server, install SQL Server 2012 or SQL Server 2008 R2.
    
3. Restore or reenroll your certificates. For details about certificates, see "Additional Backup Requirements" in [Backup and restoration requirements in Lync Server 2013: data](backup-and-restoration-requirements-data.md).
    
4. Take an image of the system before starting restoration to use as a rollback point, in case something goes wrong during restoration.
    
> [!NOTE]
> The Lync Server Deployment Wizard and cmdlets described in the procedures in this topic, and related topics, set all required access control lists (ACLs). 
  
Verify that the hardware and the software that you need for the components that you plan to restore are available before you start restoration. After you install the operating system and SQL Server, most of the steps in the following restoration procedures can be run remotely. The exceptions are noted in the procedures.
  
You should also have your organization's backup and restoration plan and the information from your last backup, such as the information in the worksheets in this document (for details, see [Backup and restoration worksheets for Lync Server 2013](backup-and-restoration-worksheets.md)), available before you begin restoration.
  

