---
title: Lync Server 2013 server collocation in a Standard Edition server deployment
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Server collocation in a Standard Edition server deployment
ms:assetid: 0763ffab-4fd6-463a-8e62-d97876b376d3
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398131(v=OCS.15)
ms:contentKeyID: 48183314
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Server collocation in a Standard Edition server deployment for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-01-20_

This section describes the server roles, databases, and file shares that you can collocate in a Lync Server 2013 Standard Edition server deployment.

<div>

## Server Roles

In Lync Server 2013, A/V Conferencing service, Mediation service, Monitoring, and Archiving are collocated on the Standard Edition Server, but additional configuration is required to enable them. You can choose to deploy Mediation service on separate servers.

You can collocate a trusted application server with a Standard Edition server.

The following server roles must each be deployed on a separate computer:

  - Director

  - Edge Server

  - Mediation Server (if not collocated with the Standard Edition server)

  - Office Web Apps Server

</div>

<div>

## Databases

By default, the SQL Server Express back-end database is collocated on the Standard Edition server. You cannot move it to a separate computer. With one exception, you cannot collocate other databases on the Standard Edition server. If you choose to deploy Persistent Chat Server on a Standard Edition server, you can collocate the Persistent chat database and the Persistent Chat Compliance database on the same Standard Edition server.

You can collocate each of the following databases on a single database server:

  - Monitoring database

  - Archiving database

  - A back-end database for an Enterprise Edition Front End pool

You can collocate any or any or all of these databases in a single SQL instance or use a separate SQL instances for each, with the following limitations:

  - Each SQL instance can contain only a single back-end database (for an Enterprise Edition Front End pool), single Monitoring database, single Archiving database, single persistent chat database, and single persistent chat compliance database.

  - The database server cannot support more than one Enterprise Edition Front End pool, one server running Archiving, one server running Monitoring, single Persistent Chat database, and single Persistent Chat compliance database, but it can support one of each, regardless of whether the databases use the same instance of SQL Server or separate instances of SQL Server.

You can collocate a file share with the databases, as described later in this section.

<div>


> [!NOTE]  
> In Lync Server 2013, you have the option of integrating Monitoring and Archiving storage with Exchange 2013 storage for some or all users in your deployment. You cannot deploy any servers running Lync Server or components on the same servers as the Exchange storage.



</div>

<div>


> [!IMPORTANT]  
> Although collocation of databases is supported, the size of the databases can grow quickly. For example, when you consider collocating the Archiving database with other databases, be aware that if you are archiving the messages of more than a few users, the disk space needed by the Archiving database can grow very large. For this reason, we do not recommend collocating multiple databases, especially the Archiving database, Persistent Chat database, and Persistent Chat compliance database with the back-end database of an Enterprise pool.



</div>

</div>

<div>

## File Shares

The file share can be a separate server or can be collocated on the same server as any or all of the following:

  - Database server, including the Back End Server of an Enterprise Edition Front End pool

  - Archiving database

  - Monitoring database

  - Persistent Chat database

  - Persistent Chat compliance database

A single file share can be used for multiple Front End pools, Standard Edition servers (all in the same site).

<div>


> [!NOTE]  
> In Lync Server 2013, Monitoring and Archiving use the Lync Server file share as the Standard Edition server.



</div>

</div>

<div>

## Other Components

You cannot collocate a reverse proxy server, which is not a Lync Server 2013 component, but is required in your deployment if you want to support sharing of web content for federated users with any Lync Server 2013 server role. You can, however, implement reverse proxy support for a Lync Server 2013 deployment by configuring the support on an existing reverse proxy server in your organization that is used for other applications.

You cannot collocate any Exchange UM component or SharePoint component with any Lync Server 2013 role.

</div>

</div>

<span> </span>

</div>

</div>

</div>

