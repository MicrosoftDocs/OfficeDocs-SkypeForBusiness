---
title: "Back End Server high availability in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: c559aacb-4e1d-4e78-9582-41f966ad418d
description: "Learn about the Back End Server high availability options supported in Skype for Business Server, including AlwaysOn Availability Groups, AlwaysOn Failover Cluster Instances, database mirroring, and SQL failover clustering."
---

# Back End Server high availability in Skype for Business Server
 
Learn about the Back End Server high availability options supported in Skype for Business Server, including AlwaysOn Availability Groups, AlwaysOn Failover Cluster Instances, database mirroring, and SQL failover clustering.
  
To enhance high availability for your Back End Servers, you have four options:
  
- Database mirroring
    
- AlwaysOn Availability Groups
    
- AlwaysOn Failover Cluster Instances (FCI)
    
- SQL failover clustering
    
Using one of these solutions is optional, but is recommended to maintain your organization's business continuity. Otherwise, having a single database server go down could cause the loss of significant Skype for Business Server data. 
  
You can set up database mirroring using only Topology Builder. For AlwaysOn Availability Groups, AlwaysOn Failover Cluster Instances,or SQL failover clustering, you use SQL Server to create the high availability solution, then you can use Topology Builder to associate it with a Front End pool.
  
If you use Back End Server high availability on a Front End pool that is paired with another Front End pool for disaster recovery, you should use the same Back End high availability solution in both pools. 
  
## Database mirroring

Skype for Business Server supports mirroring with the following database software:
  
- SQL Server 2016, both Enterprise Edition and Standard Edition

- SQL Server 2014, both Enterprise Edition and Standard Edition
    
- SQL Server 2012 SP2 and CU2, both Enterprise Edition and Standard Edition
    

> [!NOTE]
> SQL Mirroring is available in Skype for Business Server 2015 but is no longer supported in Skype for Business Server 2019. The  AlwaysOn Availability Groups, AlwaysOn Failover Cluster Instances (FCI), and SQL failover clustering methods are preferred with Skype for Business Server 2019.
    
Asynchronous database mirroring is not supported for Back End Server high availability in Skype for Business Server. In the rest of this document, database mirroring means synchronous database mirroring, unless otherwise explicitly stated. 
  
When you deploy database mirroring in a Front End pool, all Skype for Business Server databases in the pool are mirrored, including the Central Management store, if it is located in this pool, as well as the Response Group application database and the Call Park application database, if those applications are running in the pool. 
  
With database mirroring, you do not need to use shared storage for the servers. Each server keeps its copy of the databases in local storage. 
  
You may choose to deploy database mirroring with or without a witness. We recommend using a witness because it enables failover of the Back End Server to be automatic. Otherwise, an administrator must manually invoke failover. Note that even if a witness is deployed, an administrator can manually invoke Back End Server failover, if necessary.
  
If you use a witness, you can use a single witness for multiple pairs of Back End Servers. There is no strict 1:1 correspondence between witnesses and pairs of Back End Servers. Deployments that use a single witness for multiple pairs of Back End Servers are not quite as resilient as topologies with a separate witness for each Back End Server pair. 
  
### Guidelines for planning Back End Server mirroring

In general, setting up SQL mirroring between the two Back End Servers with a witness requires the following:
  
- The primary server's version of SQL Server must support SQL mirroring.
    
- The primary, mirror, and the witness (if deployed) must have the same version of SQL Server. 
    
- The primary and the mirror must have the same edition of SQL Server. The witness may have a different edition.
    
For SQL best practices in terms of what SQL versions are supported for a Witness role, see  ["Database Mirroring Witness"](https://go.microsoft.com/fwlink/p/?LinkId=247345) in the MSDN Library.
  
Before configuring server mirroring, you must first set up SQL database permissions correctly. For details, see  ["Set Up Login Accounts for Database Mirroring or AlwaysOn Availability Groups (SQL Server)"](https://go.microsoft.com/fwlink/p/?LinkId=268454).
  
With SQL mirroring, database recovery mode is always set to **Full**, which means you must closely monitor transaction log size and back up transaction logs on a regular basis to avoid running out of disk space on the Back End Servers. The frequency of transaction log backups depends on the log growth rate, which in turn depends on database transactions incurred by user activities on the Front End pool. We recommend that you determine how much transaction log growth is expected for your Lync deployment workload so that you can do the planning accordingly. The following articles provide additional information on SQL backup and log management:
  
> [!IMPORTANT]
> Using Topology Builder or cmdlets to set up and remove SQL mirroring is supported only when the primary, mirror, and witness (if desired) servers all belong to the same domain. If you want to set up SQL mirroring among servers in different domains, see your SQL Server documentation. 

> [!NOTE]
> SQL Mirroring is available in Skype for Business Server 2015 but is no longer supported in Skype for Business Server 2019. The  AlwaysOn Availability Groups, AlwaysOn Failover Cluster Instances (FCI), and SQL failover clustering methods are preferred with Skype for Business Server 2019.
  
### Recovery time for automatic Back End Server failover with database mirroring

For automatic Back End failover with database mirroring, the engineering target for recovery time objective (RTO) is 5 minutes. Because of the synchronous database mirroring, we do not anticipate data loss during Back End Server failures except in rare occasions when both the Front End Servers and the Back End Server go down simultaneously while data is being moved between the servers. The engineering target for recovery point objective (RPO) is 5 minutes.
  
### User experience during Back End Server failure with database mirroring

User experience during a failure depends on the nature of the failure, and on your topology.
  
If you use database mirroring and have a witness configured, and the principal fails, Back End Server failover happens automatically and quickly. Active users should not notice much interruption to their ongoing sessions.
  
If there is no witness configured, it will take some time for the administrator to manually invoke the failover. During that time, active users may be affected. They will continue their sessions as normal for about 30 minutes. If the primary is still not restored, or an administrator has not failed over to the backup, then users are switched to Resiliency mode, meaning that they are unable to perform tasks that require a persistent change on Lync Server (such as adding a contact).
  
If both the principal and the mirror Back End Servers fail, or if one of those servers and the witness fails, the Back End Server will become unavailable (even if it is the principal that is still working). In this case, active users are switched to Resiliency mode after some time.
  
## AlwaysOn Availability Groups and AlwaysOn Failover Cluster Instances

AlwaysOn Availability Groups and AlwaysOn Failover Cluster Instances are supported only on SQL Server 2014 Enterprise Edition and SQL Server 2012 Enterprise Edition. Skype for Business Server supports AlwaysOn Availability Groups only as active/passive, not active/active. 
  
To use AlwaysOn Availability Groups or AlwaysOn Failover Cluster Instances, you first use SQL Server to set up and configure the high availability solution. You can then use Topology Builder to associate it with a Front End pool.
  
> [!IMPORTANT]
> Instance names for multiple AlwaysOn Availability Group instances must be the same. 
  
For steps for deploying AlwaysOn Availability Groups, see [Deploy an AlwaysOn Availability Group on a Back End Server in Skype for Business Server](../../deploy/deploy-high-availability-and-disaster-recovery/alwayson-availability-group.md).
  
## SQL Server Failover Clustering

Skype for Business Server supports SQL Server failover clustering with the following database software:
  
- SQL Server 2017, both Enterprise Edition and Standard Edition

- SQL Server 2016, both Enterprise Edition and Standard Edition

- SQL Server 2014, both Enterprise Edition and Standard Edition
    
- SQL Server 2012 SP2 and CU2, both Enterprise Edition and Standard Edition

To use SQL failover clustering, you should first set up and configure the SQL Server cluster before deploying your Front End pool. For best practices and setup instructions for failover clustering in SQL Server 2012, see [https://technet.microsoft.com/en-us/library/hh231721.aspx](https://technet.microsoft.com/en-us/library/hh231721.aspx).

> [!NOTE]
> SQL Server 2017 and SQL Server 2016 are the only versions supported by Skype for Business Server 2019.
    
To use SQL failover clustering, you should first set up and configure the SQL Server cluster before deploying your Front End pool. For best practices and setup instructions for failover clustering in SQL Server 2014 and 2016, see [https://technet.microsoft.com/en-us/library/hh231721.aspx](https://technet.microsoft.com/en-us/library/hh231721.aspx). For failover clustering in SQL Server 2008, see [https://technet.microsoft.com/en-us/library/ms189134(v=sql.105).aspx](https://technet.microsoft.com/en-us/library/ms189134%28v=sql.105%29.aspx).
  
When you install SQL Server, you should install SQL Server Management Studio to manage the locations for database and log file locations. SQL Server Management Studio is installed as an optional component when you install SQL Server.
  

