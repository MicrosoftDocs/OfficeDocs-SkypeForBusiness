---
title: 'Lync Server 2013: Configure SQL Server for Lync Server'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Configure SQL Server for Lync Server 2013
ms:assetid: 375e5cc4-e436-46dc-9b02-5063f35cdcc1
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425848(v=OCS.15)
ms:contentKeyID: 48183869
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure SQL Server for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-08-12_

The topics in this section discuss how to deploy and configure SQL Server to use in an Enterprise deployment of Lync Server. Standard Edition servers use a collocated SQL Server Express version of SQL Server that is right sized for the workloads of a Standard Edition server.

The Lync Server 2013 Central Management store holds user data for all Enterprise Edition servers within a pool, and is designed to be located on a SQL Server -based Back End Server. As a centralized repository, the Central Management store cannot be installed on the same computer as any other Lync Server 2013 role. The Central Management store cannot reside on an Enterprise Edition server in the pool. The Central Management store is created automatically when you publish the topology for the first time and select to create the databases. The computer that you designate as the Back End Server must already be running SQL Server database software in order for the installation to succeed.

<div>

## In This Section

  - [SQL Server data and log file placement for Lync Server 2013](lync-server-2013-sql-server-data-and-log-file-placement.md)

  - [Configure SQL Server in Lync Server 2013](lync-server-2013-configure-sql-server.md)

  - [Deployment permissions for SQL Server in Lync Server 2013](lync-server-2013-deployment-permissions-for-sql-server.md)

  - [Database installation using Lync Server Management Shell in Lync Server 2013](lync-server-2013-database-installation-using-lync-server-management-shell.md)

  - [Understanding firewall requirements for SQL Server with Lync Server 2013](lync-server-2013-understanding-firewall-requirements-for-sql-server.md)

  - [Configure SQL Server clustering for Lync Server 2013](lync-server-2013-configure-sql-server-clustering.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

