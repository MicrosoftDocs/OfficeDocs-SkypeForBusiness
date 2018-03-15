---
title: "Add Monitoring Server SQL Server Store"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
f1_keywords:
- ms.lync.tb.AddMonitoringServerSqlStorePage
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d873a2ad-9d3a-4ef6-9f25-ccdd3716218c
description: "Monitoring Server requires a supported 64-bit edition of SQL Server database software to store the monitoring data. You can either select a previously defined SQL Server database to be used for monitoring, or define a new SQL Server database by specifying a fully qualified domain name (FQDN) of the server on which the SQL Server database will reside, in addition to the instance of SQL Server that you want to use for the new SQL Server database (which can be the default instance, or a named instance that you specify)."
---

# Add Monitoring Server SQL Server Store
[]
Monitoring Server requires a supported 64-bit edition of SQL Server database software to store the monitoring data. You can either select a previously defined SQL Server database to be used for monitoring, or define a new SQL Server database by specifying a fully qualified domain name (FQDN) of the server on which the SQL Server database will reside, in addition to the instance of SQL Server that you want to use for the new SQL Server database (which can be the default instance, or a named instance that you specify).
  
For details about SQL Server support, see [Database software support in Lync Server 2013](database-software-support.md) in the Supportability documentation. For details about the monitoring database, including collocation of the monitoring database, see [Supported server collocation in Lync Server 2013](supported-server-collocation.md) in the Supportability documentation, [Planning for monitoring in Lync Server 2013](planning-for-monitoring.md) in the Planning documentation and [SQL Server data and log file placement for Lync Server 2013](sql-server-data-and-log-file-placement.md) in the Deployment documentation. 
  
> [!NOTE]
> If the account used to publish the topology has the appropriate user rights and permissions, you can create the monitoring database when you publish your topology. You can also create the database later, including as part of the installation procedure. > To install and deploy the databases on the SQL Server-based server for monitoring, you must be a member of the SQL Server sysadmins group for the SQL Server-based server where you are installing the database files. If you are not a member of the SQL Server sysadmin group, you must request to be added to the group until the database files are deployed. If you cannot be made a member of the sysadmins group, you should provide your SQL Server database administrator with the script to configure and deploy the databases. For details about the user rights and permissions that you need to accomplish these procedures, see [Deployment permissions for SQL Server in Lync Server 2013](deployment-permissions-for-sql-server.md) in the Deployment documentation. 
  

