---
title: 'Lync Server 2013: New Response Group application features'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: New Response Group application features
ms:assetid: 569544b4-fa97-429b-97e6-568afab6c19b
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398373(v=OCS.15)
ms:contentKeyID: 48184196
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# New Response Group application features in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-29_

With the Response Group application, you can route and queue incoming calls to designated persons for special purposes, such as customer service, an internal help desk, or general telephone support for a department.

The following Response Group application features are new in Lync Server 2013:

  - **Manager role**
    
    Lync Server 2013 introduces a new Response Group Manager role. Now there are two management roles for response groups: Response Group Manager and Response Group Administrator. While Response Group Administrators can still configure any element for any response group, Managers can configure only certain elements, only for response groups they own.
    
    This improvement in the administration model benefits Response Group scalability, especially for large deployment scenarios.

  - **High availability**
    
    High availability support for the Response Group application, in the form of SQL Server mirroring, is enabled as part of the overall configuration and deployment of high availability for Lync Server 2013. If you configure for high availability and lose connectivity to the primary back-end server, Response Group functionality is not affected by leveraging the mirrored back-end server.
    
    Support for SQL Server mirroring for the Response Group application can’t be individually enabled or configured outside of the overall Lync Server 2013 high availability configuration.

  - **Disaster recovery**
    
    Disaster recovery support for the Response Group application is enabled as part of the configuration and deployment of the paired Front End pools, which are part of the overall Lync Server 2013 disaster recovery configuration. In addition, Response Group import and export cmdlets support the failover process to the backup pool and the failback process to the primary pool or to a new pool. If an outage occurs in the primary pool, response groups can be failed over to the backup pool, and then failed back to the primary pool or to a new pool when the outage is over.

<div id="sectionSection0" class="section">

</div>

<div>

## See Also


[Planning for response groups in Lync Server 2013](lync-server-2013-planning-for-response-groups.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

