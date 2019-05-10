---
title: Move the Lync Server 2010 Central Management Server to Lync Server 2013
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Move the Lync Server 2010 Central Management Server to Lync Server 2013
ms:assetid: 30cc98f2-1916-4dbe-99d0-8df5368ed3ec
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ688013(v=OCS.15)
ms:contentKeyID: 49733602
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Move the Lync Server 2010 Central Management Server to Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-11-25_

After migrating from Lync Server 2010 to Lync Server 2013, you need to move the Lync Server 2010 Central Management Server to the Lync Server 2013 Front End Server or pool, before you can remove the legacy Lync Server 2010 server.

The Central Management Server is a single master/multiple replica system, where the read/write copy of the database is held by the Front End Server that contains the Central Management Server. Each computer in the topology, including the Front End Server that contains the Central Management Server, has a read-only copy of the Central Management store data in the SQL Server database (named RTCLOCAL by default) installed on the computer during setup and deployment. The local database receives replica updates by way of the Lync Server Replica Replicator Agent that runs as a service on all computers. The name of the actual database on the Central Management Server and the local replica is XDS, which is made up of the xds.mdf and xds.ldf files. The master database location is referenced by a service control point (SCP) in Active Directory Domain Services. All tools that use the Central Management Server to manage and configure Lync Server use the SCP to locate the Central Management store.

After you have successfully moved the Central Management Server, you should remove the Central Management Server databases from the original Front End Server. For information on removing the Central Management Server databases, see [Remove the SQL Server database for a Front End pool](remove-the-sql-server-database-for-a-front-end-pool.md).

You use the Windows PowerShell cmdlet **Move-CsManagementServer** in the Lync Server Management Shell to move the database from the Lync Server 2010 SQL Server database to the Lync Server 2013 SQL Server database, and then update the SCP to point to the Lync Server 2013 Central Management Server location.

<div>

## Preparing Lync Server 2013 Front End Servers before moving the Central Management Server

Use the procedures in this section to prepare the Lync Server 2013 Front End Servers before you move the Lync Server 2010 Central Management Server.

<div>

## To prepare an Enterprise Edition Front End pool

1.  On the Lync Server 2013 Enterprise Edition Front End pool where you want to relocate the Central Management Server: Log on to the computer where the Lync Server Management Shell is installed as a member of the **RTCUniversalServerAdmins** group. You must also have SQL Server database sysadmin user rights and permissions on the database where you want to install the Central Management store.

2.  Open the Lync Server Management Shell.

3.  To create the new Central Management store in the Lync Server 2013 SQL Server database, in the Lync Server Management Shell, type:
    
        Install-CsDatabase -CentralManagementDatabase -SQLServerFQDN <FQDN of your SQL Server> -SQLInstanceName <name of instance>

4.  Confirm that the status of the **Lync Server Front-End** service is **Started**.

</div>

<div>

## To prepare a Standard Edition Front End Server

1.  On the Lync Server 2013 Standard Edition Front End Server where you want to relocate the Central Management Server: Log on to the computer where the Lync Server Management Shell is installed as a member of the **RTCUniversalServerAdmins** group.

2.  Open the Lync Server Deployment Wizard.

3.  In the Lync Server Deployment Wizard, click **Prepare first Standard Edition server**.

4.  On the **Executing Commands** page, SQL Server Express is installed as the Central Management Server. Necessary firewall rules are created. When the installation of the database and prerequisite software is completed, click **Finish**.
    
    <div>
    

    > [!NOTE]  
    > The initial installation may take some time with no visible updates to the command output summary screen. This is due to the installation of the SQL Server Express. If you need to monitor the installation of the database, use Task Manager to monitor the setup.

    
    </div>

5.  To create the new Central Management store on the Lync Server 2013 Standard Edition Front End Server, in the Lync Server Management Shell, type:
    
        Install-CsDatabase -CentralManagementDatabase -SQLServerFQDN <FQDN of your Standard Edition Server> -SQLInstanceName <name of instance - RTC by default>

6.  Confirm that the status of the **Lync Server Front-End** service is **Started**.

</div>

</div>

<div>

## To move the Lync Server 2010 Central Management Server to Lync Server 2013

1.  On the Lync Server 2013 server that will be the Central Management Server: Log on to the computer where the Lync Server Management Shell is installed as a member of the **RTCUniversalServerAdmins** group. You must also have the SQL Server database administrator user rights and permissions.

2.  Open Lync Server Management Shell.

3.  In the Lync Server Management Shell, type:
    
        Enable-CsTopology
    
    <div>
    

    > [!WARNING]  
    > If <CODE>Enable-CsTopology</CODE> is not successful, resolve the problem preventing the command from completing before continuing. If <STRONG>Enable-CsTopology</STRONG> is not successful, the move will fail and it may leave your topology in a state where there is no Central Management store.

    
    </div>

4.  On the Lync Server 2013 Front End Server or Front End pool, in the Lync Server Management Shell, type:
    
        Move-CsManagementServer

5.  Lync Server Management Shell displays the servers, file stores, database stores, and the service connection points of the Current State and the Proposed State. Read the information carefully and confirm that this is the intended source and destination. Type **Y** to continue, or **N** to stop the move.

6.  Review any warnings or errors generated by the **Move-CsManagementServer** command and resolve them.

7.  On the Lync Server 2013 server, open the Lync Server Deployment Wizard.

8.  In Lync Server Deployment Wizard, click **Install or Update Lync Server System**, click **Step 2: Setup or Remove Lync Server Components**, click **Next**, review the summary, and then click **Finish**.

9.  On the Lync Server 2010 server, open the Lync Server Deployment Wizard.

10. In Lync Server Deployment Wizard, click **Install or Update Lync Server System**, click **Step 2: Setup or Remove Lync Server Components**, click **Next**, review the summary, and then click **Finish**.

11. Reboot the Lync Server 2013 server. This is required because of a group membership change to access Central Management Server database.

12. To confirm that replication with the new Central Management store is occurring, in the Lync Server Management Shell, type:
    
        Get-CsManagementStoreReplicationStatus
    
    <div>
    

    > [!NOTE]  
    > The replication may take some time to update all current replicas.

    
    </div>

</div>

<div>

## To remove Lync Server 2010 Central Management store files after a move

1.  On the Lync Server 2010 server: Log on to the computer where the Lync Server Management Shell is installed as a member of the **RTCUniversalServerAdmins** group. You must also have the SQL Server database administrator user rights and permissions.

2.  Open Lync Server Management Shell
    
    <div>
    

    > [!WARNING]  
    > Do not proceed with the removal of the previous database files until replication is complete and is stable. If you remove the files prior to completing replication, you will disrupt the replication process and leave the newly moved Central Management Server in an unknown state. Use the cmdlet <STRONG>Get-CsManagementStoreReplicationStatus</STRONG> to confirm the replication status.

    
    </div>

3.  To remove the Central Management store database files from the Lync Server 2010 Central Management Server, type:
    
        Uninstall-CsDatabase -CentralManagementDatabase -SqlServerFqdn <FQDN of SQL Server> -SqlInstanceName <Name of source server>
    
    For example:
    
        Uninstall-CsDatabase -CentralManagementDatabase -SqlServerFqdn sql.contoso.net -SqlInstanceName rtc
    
    Where the \<FQDN of SQL Server\> is either the Lync Server 2010 Back End Server in an Enterprise Edition deployment or the FQDN of the Standard Edition server.

</div>

</div>

<span> </span>

</div>

</div>

</div>

