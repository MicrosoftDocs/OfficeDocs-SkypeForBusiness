---
title: 'Lync Server 2013: Backup and restoration process overview'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Backup and restoration process overview
ms:assetid: e0f23b21-070f-4df5-b795-cea2f5338d85
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Hh202192(v=OCS.15)
ms:contentKeyID: 51541524
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Backup and restoration process overview for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-26_

This section provides an overview of how the backup and restoration process works for Lync Server 2013. You use the same process for all Standard Edition servers and Enterprise Edition servers, regardless of their location.

In general, the backup process works as follows:

  - You create a backup location as a shared folder on a stand-alone computer that is not part of any pool. The location of the backup is referenced in **$Backup**.

  - On a regular, scheduled basis, you back up all the Lync Server databases and all the file stores that are described in [Backup and restoration requirements in Lync Server 2013: data](lync-server-2013-backup-and-restoration-requirements-data.md) by following the procedures described in [Backing up Lync Server 2013](lync-server-2013-backing-up-lync-server.md) The Central Management store includes all the server settings and configurations.

  - Each time you run a subsequent backup, you create a new shared folder and change the path that **$Backup** references.

In general, the restoration process works as follows:

  - When a failure or outage occurs, you restore the data in the location referenced by **$Backup** to new or clean computers.
    
    <div>
    

    > [!IMPORTANT]  
    > This restoration process does not restore data onto an existing server state. That is, this process requires that the server is clean or new.

    
    </div>

  - To enable your user and conference information to be recoverable to the point of failure, you can implement a disaster recovery topology with paired Front End pools, as described in [Planning for high availability and disaster recovery in Lync Server 2013](lync-server-2013-planning-for-high-availability-and-disaster-recovery.md).

  - All Domain Name System (DNS) configuration, Dynamic Host Configuration Protocol (DHCP) configuration, domain names, computer fully qualified domain names (FQDNs), file store paths, and so on must be the same at the time of restoration that they were at the time of back up.

If a server running Lync Server fails, recovery includes the following steps:

  - Install the operating system on a new or clean computer with the same FQDN as the failed computer.

  - Reinstall certificates.

  - If the server hosted a database, install Microsoft SQL Server 2012 or Microsoft SQL Server 2008 R2.

  - In general, if the server hosted a database, run Topology Builder to create and install the database and set up access control lists (ACLs).

  - In general, if the server hosted a server role, run step 1 through step 4 of the Lync Server Deployment Wizard to install the local configuration files, install the server role components, assign certificates, and start the services.
    
    <div>
    

    > [!NOTE]  
    > If the server hosted a database collocated with the server role, running step 2 of the Lync Server Deployment Wizard recreates the database.

    
    </div>

  - If the server hosted a database, restore the backed up data.

</div>

<span> </span>

</div>

</div>

</div>

