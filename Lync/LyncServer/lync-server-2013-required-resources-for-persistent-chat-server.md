---
title: 'Lync Server 2013: Required resources for Persistent Chat Server'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Required resources
ms:assetid: bce50b95-f3c8-407e-963a-d8896ee77fbc
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205211(v=OCS.15)
ms:contentKeyID: 48185255
ms.date: 02/05/2016
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Required resources for Persistent Chat Server in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2016-02-05_

High availability and disaster recovery for Persistent Chat Server requires additional resources beyond what is typically needed for full operation. Before configuring Persistent Chat Server for high availability and disaster recovery, ensure that you have the following resources in addition to what is required for standard Persistent Chat Server operation. For additional configuration information, see [Configuring Persistent Chat Server in Lync Server 2013](lync-server-2013-configuring-persistent-chat-server.md).

  - One dedicated database instance located in the same physical data center in which the home front end of the Persistent Chat Server service is located. This database will serve as the SQL Server mirror for the primary Persistent Chat database. Optionally, designate an additional SQL Server to serve as the mirroring witness if you want an automated failover to the mirror database.

  - One dedicated database instance located in the other physical data center. This database will serve as the SQL Server Log Shipping secondary database for the database in the primary data center.

  - One dedicated database instance to serve as the SQL Server mirror for the secondary database. Optionally, designate an additional SQL Server to server as the mirroring witness. Both of these must be located in the same physical data center as the secondary database.

  - If Persistent Chat Server compliance is enabled, an additional three dedicated database instances are required. Their distribution is the same as those previously outlined for the Persistent Chat database. While it is possible for the compliance database to share the same SQL Server instance as the Persistent Chat database, we recommend standalone instances for high availability and disaster recovery.

  - A file share must be created and designated for the SQL Server Log Shipping transaction logs. All SQL Servers in both data centers that run Persistent Chat databases must have read/write access to this file share. This share is not defined as part of a FileStore role.

  - A file share on the secondary database server to serve as the destination folder for the SQL Server transaction logs that are copied from the primary server file share.

<div>


> [!NOTE]  
> Active Persistent Chat servers in a Persistent Chat Server pool MUST reside in the same time zone as the next hop Lync Pool defined in the topology.



</div>

The following figures provide examples about how the entire Persistent Chat Server pool can be configured in the two different stretched pool topologies:

  - Stretched Persistent Chat Server pool when data centers are geo-located with high bandwidth/low latency.

  - Stretched Persistent Chat Server pool when data centers are geo-located with low bandwidth/high latency.

The following figure shows a stretched Persistent Chat Server pool topology where data centers are geo-located with high bandwidth/low latency.

**Stretched Persistent Chat Server pool when data centers are geo-located with high bandwidth/low latency.**

![Persistent Chat Server pool HBW configuration exam](images/JJ205211.55d10910-c824-41e6-bed2-08d13a2abd65(OCS.15).jpg "Persistent Chat Server pool HBW configuration exam")

The following figure shows a stretched Persistent Chat Server pool topology where data centers are geo-located with low bandwidth/high latency.

**Stretched Persistent Chat Server pool when data centers are geo-located with low bandwidth/high latency.**

![Persistent Chat Server pool LBW configuration exam](images/JJ205211.586b0a3a-3767-4991-944f-ee54389512aa(OCS.15).jpg "Persistent Chat Server pool LBW configuration exam")

</div>

<span> </span>

</div>

</div>

</div>

