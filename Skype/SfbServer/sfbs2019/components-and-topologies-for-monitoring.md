---
title: "Components and topologies for monitoring in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c1bb36b0-1fb8-4d8e-9cc9-9bef740fe3c6
description: "Because the unified data collection agents are automatically installed and activated on each Front End server you do not need to configure a server to act as the Monitoring server; each Front End server already functions as a Monitoring server. However, you will need to install and configure a database to act as the backend data store for your monitoring data. Microsoft Lync Server 2013 can use any of the following databases as the backend store for monitoring:"
---

# Components and topologies for monitoring in Lync Server 2013
[]
Because the unified data collection agents are automatically installed and activated on each Front End server you do not need to configure a server to act as the Monitoring server; each Front End server already functions as a Monitoring server. However, you will need to install and configure a database to act as the backend data store for your monitoring data. Microsoft Lync Server 2013 can use any of the following databases as the backend store for monitoring:
  
- Microsoft SQL Server 2008 R2 Enterprise Edition
    
- Microsoft SQL Server 2008 R2 Standard Edition
    
- Microsoft SQL Server 2012 Enterprise Edition
    
- Microsoft SQL Server 2012 Standard Edition
    
Note that you must use the 64-bit editions of these databases; 32-bit versions of SQL Server cannot be used as the backend store for monitoring. Likewise, Lync Server 2013 does not support the Express Editions of SQL Server 2008 or SQL Server 2012. For more information on database requirements for Lync Server 2013 see the topic [Database software support in Lync Server 2013](database-software-support.md) in the Lync Server 2013 Supportability guide. 
  
Keep in mind that SQL Server must be installed and configured before you deploy and configure monitoring. However, you only need to deploy SQL Server itself; you do not have to setup the monitoring databases in advance. Instead, those databases will automatically be created for you when you publish your Lync Server topology.
  
Monitoring data can share a SQL Server instance with other types of data. Typically, the call detail recording database (LcsCdr) and the Quality of Experience database (QoEMetrics) share the same SQL instance; it is also common for the two monitoring databases to be in the same SQL instance as the archiving database (LcsLog). About the only real requirement with SQL Server instances is that any one instance of SQL Server is limited to the following:
  
- One instance of the Lync Server 2013 backend database. (As a general rule, it is not recommended that your monitoring database be collocated in the same SQL instance, or even on the same computer, as the backend database. Although technically possible, you run the risk of the monitoring database using up disk space needed by the backend database.) 
    
- One instance of the call detail recording database.
    
- One instance of the Quality of Experience database.
    
- One instance of the archiving database.
    
In other words, you cannot have two instances of the LcsCdr database in the same instance of SQL Server. If you need multiple instances of the LcsCdr database then you will need to configure multiple instances of SQL Server.
  
## See also

#### 

[Deploying monitoring in Lync Server 2013](deploying-monitoring.md)

