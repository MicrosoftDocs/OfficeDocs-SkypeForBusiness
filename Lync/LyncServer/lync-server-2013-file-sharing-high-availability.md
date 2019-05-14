---
title: 'Lync Server 2013: File sharing high availability'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: File sharing high availability
ms:assetid: b8c8d5ec-9397-4128-8d1e-8ec6c30fade7
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205203(v=OCS.15)
ms:contentKeyID: 48185238
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# File sharing high availability in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-03-30_

To ensure high availability for Lync Server file sharing within a single data center, you can use the Distributed File System (DFS). DFS supports failover from one file server to another within the same data center. For a large scale deployment, we recommend that you use dedicated file servers that are paired using DFS.

Depending on your network's size, and the amount of resiliency you want, you can use one pair of servers to host all file shares in a site, or use one pair per Front End pool.

DFS is a best effort file replication mechanism, with no published recovery time objective (RTO) or recovery point objective (RPO) commitment. The failover between the DFS servers should be completed quickly, but data replication delay may prevent users from being able to continue work in progress when the failover happens.

If you use DFS and data store on the fileshare is critical, you should back up the file shares frequently, such as every 4 to 8 hours. When one file share goes down and replication is not up to date, you can use the backup to restore the content on the failed server to the other server that is paired with the server that is now unavailable.

</div>

<span> </span>

</div>

</div>

</div>

