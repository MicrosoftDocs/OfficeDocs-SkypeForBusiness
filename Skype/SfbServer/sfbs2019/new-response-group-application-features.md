---
title: "New Response Group application features in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 569544b4-fa97-429b-97e6-568afab6c19b
description: "With the Response Group application, you can route and queue incoming calls to designated persons for special purposes, such as customer service, an internal help desk, or general telephone support for a department."
---

# New Response Group application features in Lync Server 2013
[]
With the Response Group application, you can route and queue incoming calls to designated persons for special purposes, such as customer service, an internal help desk, or general telephone support for a department. 
  
The following Response Group application features are new in Lync Server 2013:
  
- **Manager role**
    
    Lync Server 2013 introduces a new Response Group Manager role. Now there are two management roles for response groups: Response Group Manager and Response Group Administrator. While Response Group Administrators can still configure any element for any response group, Managers can configure only certain elements, only for response groups they own.
    
    This improvement in the administration model benefits Response Group scalability, especially for large deployment scenarios.
    
- **High availability**
    
    High availability support for the Response Group application, in the form of SQL Server mirroring, is enabled as part of the overall configuration and deployment of high availability for Lync Server 2013. If you configure for high availability and lose connectivity to the primary back-end server, Response Group functionality is not affected by leveraging the mirrored back-end server.
    
    Support for SQL Server mirroring for the Response Group application can't be individually enabled or configured outside of the overall Lync Server 2013 high availability configuration.
    
- **Disaster recovery**
    
    Disaster recovery support for the Response Group application is enabled as part of the configuration and deployment of the paired Front End pools, which are part of the overall Lync Server 2013 disaster recovery configuration. In addition, Response Group import and export cmdlets support the failover process to the backup pool and the failback process to the primary pool or to a new pool. If an outage occurs in the primary pool, response groups can be failed over to the backup pool, and then failed back to the primary pool or to a new pool when the outage is over.
    
## See also

#### 

[Planning for response groups in Lync Server 2013](planning-for-response-groups.md)

