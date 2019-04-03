---
title: 'Lync Server 2013: Technical requirements for Persistent Chat Server'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Technical requirements for Persistent Chat Server
ms:assetid: 692b7d99-1bc9-4c99-a050-2bc2be8688b2
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398495(v=OCS.15)
ms:contentKeyID: 48184383
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Technical requirements for Persistent Chat Server in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-01-06_

Each computer that hosts Persistent Chat Server must have access to an existing Lync Server 2013 topology with the following components:

  - **Lync Server 2013, Front End Server.** The Front End Server is the foundation for Session Initiation Protocol (SIP) routing, which makes communication between computers running Persistent Chat Server and the Persistent Chat functionality possible. Before you begin to deploy Persistent Chat Server, verify the deployment of Lync Server 2013, Standard Edition, or a Lync Server Front End pool and any other internal computers running Lync Server, as appropriate to your organization.

The following sections describe the specific requirements for the Persistent Chat Server and the database that stores the Persistent Chat data.

<div>

## Persistent Chat Server Requirements

For details about the recommended hardware for deploying Lync Server and the latest version of Persistent Chat Server, see [Server hardware platforms for Lync Server 2013](lync-server-2013-server-hardware-platforms.md) in the Supportability documentation.

For details about the server and tools operating system support for Lync Server and Persistent Chat Server, see [Server and tools operating system support in Lync Server 2013](lync-server-2013-server-and-tools-operating-system-support.md) in the Supportability documentation.

For details about additional software required for deploying Persistent Chat Server, see the following table.

### Persistent Chat Server Software Prerequisites

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Software</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Message Queuing</p></td>
<td><p>Used by the Persistent Chat Server and Persistent Chat Compliance service, if deployed.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Persistent Chat Server Database Requirements

Persistent Chat Server uses the Persistent Chat database to store chat history, configuration, and user provisioning data. Optionally, it uses the Persistent Chat compliance database to store compliance data.

<div>


> [!IMPORTANT]  
> The Persistent Chat database (mgc) and the compliance database (mgccomp) can be located in the same instance of SQL Server or on different SQL Servers.



</div>

To prepare a database server platform, be sure that each computer meets the hardware requirements, and then install the prerequisite software.

The server platform for the Persistent Chat database servers requires the same hardware as the Lync Server back-end database server. For details, see [Server hardware platforms for Lync Server 2013](lync-server-2013-server-hardware-platforms.md) in the Supportability documentation.

On the database server, be sure that one of the following software applications is installed:

  - Microsoft SQL Server 2012. For details about how to install Microsoft SQL Server 2012, see "Install SQL Server 2012" at [http://go.microsoft.com/fwlink/p/?LinkID=248559](http://go.microsoft.com/fwlink/p/?linkid=248559).

  - Microsoft SQL Server 2008 R2. For details about how to install Microsoft SQL Server 2008 R2, see "SQL Server Installation (SQL Server 2008 R2)" at [http://go.microsoft.com/fwlink/?LinkId=275702](http://go.microsoft.com/fwlink/?linkid=275702).

</div>

<div>

## Persistent Chat Server Certificate Requirements

For details about acquiring certificates, creating the SQL Server database, and creating file stores, see [Deploying Lync Server 2013](lync-server-2013-deploying-lync-server.md) in the Deployment documentation.

</div>

</div>

<span> </span>

</div>

</div>

</div>

