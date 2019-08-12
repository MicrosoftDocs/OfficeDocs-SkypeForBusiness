---
title: 'Lync Server 2013: Setting up storage for Archiving'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Setting up storage for Archiving
ms:assetid: f751245c-743e-454f-8325-968ae5e3de71
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205392(v=OCS.15)
ms:contentKeyID: 48185858
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Setting up storage for Archiving in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-12-17_

Archiving storage for Lync Server 2013 includes the following:

  - **Data storage**   Data storage is required to store IM content.

  - **File storage**   File storage is required to store conferencing (meeting) content data storage and file storage.

<div>

## Setting Up Data Storage

Requirements for setting up data storage for Archiving in Lync Server 2013 depend on how you want to store archiving data:

  - Integrate Lync Server 2013 Archiving with your Exchange deployment to store Archiving data using Exchange storage.

  - Set up separate SQL Server database servers to store Archiving data.

<div>

## Setting Up Exchange Storage for Archiving Data

Setting up Exchange for storage of Archiving data requires that your Exchange deployment is running Exchange 2013. Additionally, user mailboxes must be homed on the Exchange 2013 server and their mailboxes must be put on In-Place Hold. For details about configuring Exchange 2013, see the Exchange product documentation.

</div>

<div>

## Setting Up SQL Server Database Servers for Storage of Archiving Data

Archiving in Lync Server 2013 requires the SQL Server database software to store the archived data, unless you integrate your deployment with Exchange.

For SQL Server archiving databases, you must install SQL Server on the computer that will host the Archiving database. You can use the same SQL instance that you use for the back-end database of a Front End pool. For best performance, you should deploy the Archiving database on a computer that is separate from the Central Management store. For details about collocating Lync Server 2013 components, see [Supported server collocation in Lync Server 2013](lync-server-2013-supported-server-collocation.md) in the Supportability documentation.

Each database server must be running a supported version of SQL Server. For details about the supported versions, see [Technical requirements for Archiving in Lync Server 2013](lync-server-2013-technical-requirements-for-archiving.md) in the Planning documentation.

You must set up the SQL Server platforms prior to deploying and enabling Archiving. If the account to be used to publish the topology has the appropriate administrator rights and permissions, you can create the Archiving database (LcsLog) when you publish your topology. You can also create the database later, including as part of the installation procedure. For details about SQL Server, see the SQL Server TechCenter at [http://go.microsoft.com/fwlink/p/?linkID=129045](http://go.microsoft.com/fwlink/p/?linkid=129045).

<div>


> [!NOTE]  
> Ensure that the SQL Server Agent Service Startup Type is Automatic and the SQL Server Agent Service is running for the SQL Instance which is holding the Archiving database, so that the Default Archiving SQL Server Maintenance Job can run on its scheduled basis under the control of the SQL Server Agent Service.



</div>

</div>

</div>

<div>

## Setting Up File Storage

Archiving uses the Lync Server 2013 file share that you specified when you set up your Front End pool or Standard Edition server. You cannot change the file share used for Archiving. For details about supported file storage systems, see [File storage support in Lync Server 2013](lync-server-2013-file-storage-support.md) in the Supportability documentation.

</div>

</div>

<span> </span>

</div>

</div>

</div>

