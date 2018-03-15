---
title: "Deployment overview for Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: da67555e-f410-4c37-9996-d511f37da8d1
description: "The main difference between Lync Server 2013 Enterprise Edition and Lync Server 2013 Standard Edition is that Standard Edition does not support the high availability features included with Enterprise Edition. For high availability, you need to deploy multiple Front End Servers to a pool and then you can mirror the server running SQL Server. With Enterprise Edition you can choose to collocate or define a stand-alone Mediation Server. The Monitoring Server and Archiving Server can use a stand-alone server running SQL Server. Or, they can have instances of SQL Server running on the database server for the Front End Servers and pools."
---

# Deployment overview for Lync Server 2013
[]
The main difference between Lync Server 2013 Enterprise Edition and Lync Server 2013 Standard Edition is that Standard Edition does not support the high availability features included with Enterprise Edition. For high availability, you need to deploy multiple Front End Servers to a pool and then you can mirror the server running SQL Server. With Enterprise Edition you can choose to collocate or define a stand-alone Mediation Server. The Monitoring Server and Archiving Server can use a stand-alone server running SQL Server. Or, they can have instances of SQL Server running on the database server for the Front End Servers and pools.
  
Servers running Lync Server 2013 Standard Edition are intended for smaller organizations and remote locations, which are geographically removed from the organization's main deployment. Two Standard Edition server servers paired together for failover in case of disaster can support up to 5,000 users. You cannot pool Standard Edition servers like you can Front End Servers in Enterprise Edition. Also, the SQL Server database that Standard Edition uses is a collocated server running SQL Server Express that is designed to handle Standard Edition server workloads. This is not to say that all roles must reside on a Standard Edition server. You can have stand-alone Mediation Servers and Edge Servers. The SQL Server database for the Central Management store and for the purposes of Lync Server 2013 must reside on the Standard Edition server collocated with the server running SQL Server. The Monitoring Server and Archiving Server use a stand-alone server with the SQL Server database.
  

