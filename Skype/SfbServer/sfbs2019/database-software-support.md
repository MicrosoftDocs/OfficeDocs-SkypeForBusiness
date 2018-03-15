---
title: "Database software support in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: e05d0032-bbea-4e61-987d-d07b1c045fd5
description: "Lync Server 2013 supports the following database management systems:"
---

# Database software support in Lync Server 2013
[]
Lync Server 2013 supports the following database management systems:
  
- **Back-end database of a Front End pool, Archiving database, Monitoring database, persistent chat database, and persistent chat compliance database**
    
  - Microsoft SQL Server 2008 R2 Enterprise database software (64-bit edition). Additionally running the latest service pack is recommended.
    
  - Microsoft SQL Server 2008 R2 Standard (64-bit edition). Additionally running the latest service pack is recommended.
    
  - Microsoft SQL Server 2012 Enterprise (64-bit edition). Additionally running the latest service pack is recommended.
    
  - Microsoft SQL Server 2012 Standard (64-bit edition). Additionally running the latest service pack is recommended.
    
- **Standard Edition server database and Front End Server databases**
    
  - Microsoft SQL Server 2012 Express (64-bit edition). Additionally running the latest service pack is recommended.
    
    We support the patching and upgrade of Microsoft SQL Server on Front End Servers and Standard Edition servers. However, when you make any kind of upgrade or patch on Front End Servers, you must account for quorum requirements. For more information, see [Upgrade or update Front End Servers in Lync Server 2013](upgrade-or-update-front-end-servers.md) and [Topologies and components for Front End Servers, instant messaging, and presence in Lync Server 2013](topologies-and-components-for-front-end-servers-instant-messaging-and-presence.md).
    
    > [!NOTE]
    > Microsoft SQL Server 2012 Express (64-bit edition) is automatically installed by Lync Server 2013 on each Standard Edition server and each Front End Server server. 
  
> [!IMPORTANT]
>  Lync Server 2013 does not support the 32-bit edition of SQL Server. You must use the 64-bit edition. >  SQL Server Web edition and SQL Server Workgroup edition are not supported. You cannot use them with Lync Server 2013. >  Lync Server 2013 does support native database mirroring. >  To use the Monitoring Server role, you should install SQL Server Reporting Services. 
  
In a Front End pool, the back-end database can be a single SQL Server computer. 
  
> [!IMPORTANT]
> If you collocate Lync Server databases with other databases, we highly recommend assessing all factors that might affect availability and performance, as well as ensuring that, if one node fails, the remaining node can handle the load. To verify failover capabilities, we recommend testing all failover scenarios. 
  
## Using SQL Mirroring and SQL Clustering

Lync Server 2013 supports the use of either SQL mirroring or SQL clustering for each Lync Server database. You can easily set up SQL mirroring with the Topology Builder tool in Lync Server 2013. For SQL failover clustering, you must use SQL Server for setup. 
  
Lync Server 2013 supports both SQL mirroring and SQL clustering topologies for all deployments, including greenfield deployments and organizations that have upgraded from previous versions of Lync Server.
  
SQL Clustering support is for an active/passive configuration. For performance reasons, the passive node should not be shared by any other SQL instance. 
  
The following support is included:
  
- Two-node failover clustering for the following:
    
  - Microsoft SQL Server 2012 Standard (64-bit edition). Additionally running the latest service pack is recommended.
    
  - Microsoft SQL Server 2008 R2 Standard (64-bit edition). Additionally running the latest service pack is recommended.
    
- Up to sixteen-node failover clustering for the following:
    
  - Microsoft SQL Server 2012 Enterprise (64-bit edition). Additionally running the latest service pack is recommended.
    
  - Microsoft SQL Server 2008 R2 Enterprise database software (64-bit edition). Additionally running the latest service pack is recommended.
    
For more information about SQL mirroring, see [Back End Server high availability in Lync Server 2013](back-end-server-high-availability.md). For details on how to deploy SQL clustering, see [Configure SQL Server clustering for Lync Server 2013](configure-sql-server-clustering.md).
  
For more information and best practices for failover clustering in SQL Server 2012, see [https://technet.microsoft.com/en-us/library/hh231721.aspx](https://technet.microsoft.com/en-us/library/hh231721.aspx). For failover clustering in SQL Server 2008, see [https://technet.microsoft.com/en-us/library/ms189134(v=sql.105).aspx](https://technet.microsoft.com/en-us/library/ms189134%28v=sql.105%29.aspx).
  

