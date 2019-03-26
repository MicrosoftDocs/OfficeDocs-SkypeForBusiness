---
title: Remove SQL Server instances and databases on the Back End Server
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Remove SQL Server instances and databases on the Back End Server
ms:assetid: 32457df9-7dd9-4fca-9362-ea4de26b0296
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ688016(v=OCS.15)
ms:contentKeyID: 49733606
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove SQL Server instances and databases on the Back End Server

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-19_

You remove the Microsoft SQL Server databases and instances after you remove the servers running Lync Server 2010 that are dependent on them, or after you reconfigure the servers running Lync Server 2010 to use another database. You need to perform the procedure in this topic when you retire the current SQL Server or reconfigure the current server running Lync Server 2010 in such a way that it renders the databases obsolete or unavailable.

To remove the databases or instances for the Archiving Server or Monitoring Server, you must first remove the server role. Similarly, to remove the instances or databases for Front End pool, you must first remove or reconfigure the dependent server role. These procedures make no distinction between collocated databases or separate instances for servers. The procedures are unaffected by the collocation of databases.

<div>

## In This Section

  - [Remove the SQL Server database for a Front End pool](remove-the-sql-server-database-for-a-front-end-pool.md)

  - [Remove the SQL Server database for a Monitoring server](remove-the-sql-server-database-for-a-monitoring-server.md)

  - [Remove the SQL Server database for an Archiving server](remove-the-sql-server-database-for-an-archiving-server.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

