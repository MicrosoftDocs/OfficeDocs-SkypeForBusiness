---
title: Lync Server 2013 server collocation in an Enterprise Edition Front End pool deployment
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Server collocation in an Enterprise Edition Front End pool deployment
ms:assetid: 0516b18d-14c0-4237-9279-0f92e341b1bd
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398102(v=OCS.15)
ms:contentKeyID: 48183287
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Server collocation in an Enterprise Edition Front End pool deployment for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-11-11_

This section describes the server roles, databases, and file shares that you can collocate in a Lync Server 2013 Front End pool deployment.

<div>

## Server Roles

In Lync Server 2013, A/V Conferencing service, Mediation service, Monitoring, and Archiving are collocated on the Front End Server, but additional configuration is required to enable them. If you do not want to collocate the Mediation Server with the Front End Server, you can deploy it as a stand-alone Mediation Server on a separate computer.

You can collocate a trusted application server with the Front End Server.

The following server roles must each be deployed on a separate computer:

  - Director

  - Edge Server

  - Mediation Server (if not collocated with the Front End Server)

  - Office Web Apps Server

You cannot collocate Persistent Chat server role with the Front End Server.

</div>

<div>

## Databases

You can collocate each of the following databases on the same database server:

  - Back-end database

  - Monitoring database

  - Archiving database

  - Persistent Chat database

  - Persistent Chat compliance database

You can collocate any or any or all of these databases in a single instance of SQL Server or use a separate instance of SQL Server for each, with the following limitations:

  - Each instance of SQL Server can contain only a single back-end database, a single Monitoring database, a single Archiving database, a single Persistent Chat database, and a single Persistent Chat compliance database.

  - The database server cannot support more than one Front End pool, one Archiving deployment, and one Monitoring deployment, but it can support one of each, regardless of whether the databases use the same instance of SQL Server or separate instances of SQL Server.

You can collocate a file share with the databases, as described later in this section.

<div>


> [!NOTE]  
> In Lync Server 2013, you have the option of integrating Archiving storage with Exchange 2013 storage for some or all users in your deployment. You cannot deploy any servers running Lync Server or components on the same servers as the Exchange storage.



</div>

<div>


> [!IMPORTANT]  
> Although collocation of databases is supported, the size of the databases can grow quickly. For example, when you consider collocating the Archiving database with other databases, be aware that if you are archiving the messages of more than a few users, the disk space needed by the Archiving database can grow very large. For this reason, we do not recommend collocating multiple databases, especially the Archiving database, the Persistent Chat database, or the Persistent Chat compliance database with the back-end database.



</div>

</div>

<div>

## File Share

The file share can be a separate server or can be collocated on the same server as any or all of the following:

  - Database server, including the Back End Server of an Enterprise Edition Front End pool

  - Archiving database

  - Monitoring database

  - Persistent Chat database

  - Persistent Chat compliance database

A single file share can be used for multiple Front End pools, Standard Edition servers (all in the same site).

<div>


> [!NOTE]  
> In Lync Server 2013, Monitoring and Archiving use the Lync Server file share as the Front End Server.



</div>

</div>

<div>

## Other Components

You cannot collocate a reverse proxy server, which is not a Lync Server 2013 component, but is required in your deployment if you want to support sharing of web content for federated users with any Lync Server 2013 server role. You can, however, implement reverse proxy support for a Lync Server 2013 deployment by configuring the support on an existing reverse proxy server in your organization that is used for other applications.

You cannot collocate any Exchange Unified Messaging (UM) component or SharePoint component with any SharePoint Server role.

</div>

</div>

<span> </span>

</div>

</div>

</div>

