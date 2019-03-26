---
title: 'Lync Server 2013: Components and topologies for monitoring'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Components and topologies for monitoring
ms:assetid: c1bb36b0-1fb8-4d8e-9cc9-9bef740fe3c6
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412952(v=OCS.15)
ms:contentKeyID: 48185313
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Components and topologies for monitoring in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-05_

Because the unified data collection agents are automatically installed and activated on each Front End server you do not need to configure a server to act as the Monitoring server; each Front End server already functions as a Monitoring server. However, you will need to install and configure a database to act as the backend data store for your monitoring data. Microsoft Lync Server 2013 can use any of the following databases as the backend store for monitoring:

  - Microsoft SQL Server 2008 R2 Enterprise Edition

  - Microsoft SQL Server 2008 R2 Standard Edition

  - Microsoft SQL Server 2012 Enterprise Edition

  - Microsoft SQL Server 2012 Standard Edition

Note that you must use the 64-bit editions of these databases; 32-bit versions of SQL Server cannot be used as the backend store for monitoring. Likewise, Lync Server 2013 does not support the Express Editions of SQL Server 2008 or SQL Server 2012. For more information on database requirements for Lync Server 2013 see the topic [Database software support in Lync Server 2013](lync-server-2013-database-software-support.md) in the Lync Server 2013 Supportability guide.

Keep in mind that SQL Server must be installed and configured before you deploy and configure monitoring. However, you only need to deploy SQL Server itself; you do not have to setup the monitoring databases in advance. Instead, those databases will automatically be created for you when you publish your Lync Server topology.

Monitoring data can share a SQL Server instance with other types of data. Typically, the call detail recording database (LcsCdr) and the Quality of Experience database (QoEMetrics) share the same SQL instance; it is also common for the two monitoring databases to be in the same SQL instance as the archiving database (LcsLog). About the only real requirement with SQL Server instances is that any one instance of SQL Server is limited to the following:

  - One instance of the Lync Server 2013 backend database. (As a general rule, it is not recommended that your monitoring database be collocated in the same SQL instance, or even on the same computer, as the backend database. Although technically possible, you run the risk of the monitoring database using up disk space needed by the backend database.)

  - One instance of the call detail recording database.

  - One instance of the Quality of Experience database.

  - One instance of the archiving database.

In other words, you cannot have two instances of the LcsCdr database in the same instance of SQL Server. If you need multiple instances of the LcsCdr database then you will need to configure multiple instances of SQL Server.

<div>

## See Also


[Deploying monitoring in Lync Server 2013](lync-server-2013-deploying-monitoring.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

