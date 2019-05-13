---
title: 'Lync Server 2013: Back End Server high availability'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Back End Server high availability
ms:assetid: c559aacb-4e1d-4e78-9582-41f966ad418d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205248(v=OCS.15)
ms:contentKeyID: 48185358
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Back End Server high availability in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-08-12_

To ensure high availability for your Back End Servers, you can use either synchronous SQL mirroring or SQL clustering. Using one of these solutions optional, but is recommended to maintain your organization's business continuity. Asynchronous SQL mirroring is not supported for Back End Server high availability in Lync Server 2013. In the rest of this document, SQL mirroring means synchronous SQL mirroring, unless otherwise explicitly stated.

You can easily set up SQL mirroring with Topology Builder. For SQL failover clustering, you must use SQL Server for setup.

If you use either SQL mirroring or SQL clustering in a pool which is paired with another Front End pool for disaster recovery, you should use the same Back End high availability solution in both pools. You should not pair a pool using SQL mirroring with a pool using SQL clustering.

When you deploy SQL mirroring, all Lync Server databases in the pool are mirrored, including the Central Management store, if it is located in this pool, as well as the Response Group application database and the Call Park application database, if those applications are running in the pool.

With SQL mirroring, you do not need to use shared storage for the servers. Each server keeps its copy of the databases in local storage.

You may choose to deploy SQL mirroring with or without a witness. We recommend using a witness because it enables failover of the Back End Server to be automatic. Otherwise, an administrator must manually invoke failover. Note that even if a witness is deployed, an administrator can manually invoke Back End Server failover, if necessary.

If you use a witness, you can use a single witness for multiple pairs of Back End Servers. There is no strict 1:1 correspondence between witnesses and pairs of Back End Servers. Deployments that use a single witness for multiple pairs of Back End Servers are not quite as resilient as topologies with a separate witness for each Back End Server pair.

For more information about SQL clustering support, see [Database software support in Lync Server 2013](lync-server-2013-database-software-support.md). For details on deploying SQL clustering, see [Configure SQL Server clustering for Lync Server 2013](lync-server-2013-configure-sql-server-clustering.md).

<div>

## Recovery Time for Automatic Back End Server Failover with SQL Mirroring

For automatic Back End failover with SQL mirroring, the engineering target for recovery time objective (RTO) is 5 minutes. Because of the synchronous SQL mirroring, we do not anticipate data loss during Back End Server failures except in rare occasions when both the Front End Servers and the Back End Server go down simultaneously while data is being moved between the servers. The engineering target for recovery point objective (RPO) is 5 minutes.

</div>

<div>

## User Experience During Back End Server Failure with SQL Mirroring

User experience during a failure depends on the nature of the failure, and on your topology.

If you use SQL mirroring and have a witness configured, and the principal fails, Back End Server failover happens automatically and quickly. Active users should not notice much interruption to their ongoing sessions.

If there is no witness configured, it will take some time for the administrator to manually invoke the failover. During that time, active users may be affected. They will continue their sessions as normal for about 30 minutes. If the primary is still not restored, or an administrator has not failed over to the backup, then users are switched to Resiliency mode, meaning that they are unable to perform tasks that require a persistent change on Lync Server (such as adding a contact).

If both the principal and the mirror Back End Servers fail, or if one of those servers and the witness fails, the Back End Server will become unavailable (even if it is the principal that is still working). In this case, active users are switched to Resiliency mode after some time.

</div>

</div>

<span> </span>

</div>

</div>

</div>

