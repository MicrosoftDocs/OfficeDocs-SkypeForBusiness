---
title: 'Lync Server 2013: Failing over Persistent Chat Server'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Failing over Persistent Chat Server
ms:assetid: 2cd79ffd-fee6-44ce-96cf-b98bf25e2690
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204772(v=OCS.15)
ms:contentKeyID: 48183726
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Failing over Persistent Chat Server in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-02-05_

Failover for Persistent Chat Server is designed to be mainly a manual process.

The failover procedure is based on the assumption that the secondary data center is up and running, but the Persistent Chat Server services where the primary Persistent Chat database is located are completely unavailable, including the following:

  - Persistent Chat Server primary database and Persistent Chat Server mirror database are down.

  - Lync Server Front End Server is down.

The procedure is based on two basic steps:

  - Recover the primary Persistent Chat database (mgc).

  - Establish mirroring for the new primary database.

The Persistent Chat compliance database (mgccomp) is not failed over. The contents of this database are transient and are purged as the compliance adapter processes the data. It is your responsibility, as Persistent Chat Administrator, to correctly manage the adapter output to avoid data loss.

<div>

## To fail over Persistent Chat Server

1.  Remove log shipping from the Persistent Chat Server Backup Log Shipping database.
    
    1.  Using SQL Server Management Studio, connect to the database instance where the Persistent Chat Server backup mgc database is located.
    
    2.  Open a query window to the master database.
    
    3.  Use the following command to drop log shipping:
        
            exec sp_delete_log_shipping_secondary_database mgc

2.  Copy any uncopied backup files from the backup share to the copy destination folder of the backup server.

3.  Apply any unapplied transaction log backups in sequence to the secondary database. For details, see "How to: Apply a Transaction Log Backup (Transact-SQL)" at http://go.microsoft.com/fwlink/p/?linkid=247428.

4.  Bring the backup mgc database online. Using the query window that opens in step 1b, do the following:
    
    1.  End all connections to the mgc database, if there are any:
        
        1.  **exec sp\_who2** to identify connections to the mgc database.
        
        2.  **kill \<spid\>** to end these connections.
    
    2.  Bring the database online:
        
        1.  **restore database mgc with recovery**.

5.  In Lync Server Management Shell, use the command **Set-CsPersistentChatState -Identity "service:atl-cs-001.litwareinc.com" –PoolState FailedOver** to fail over to the mgc backup database. Be sure to substitute the fully qualified domain name of your Persistent Chat pool for atl-cs-001.litwareinc.com.
    
    The mgc backup database now serves as the primary database.

6.  In Lync Server Management Shell, use the **Install-CsMirrorDatabase** cmdlet to establish a high availability mirror for the backup database that now serves as the primary database. Use the backup database instance as the primary database and the backup mirror database instance as the mirror instance. This is not the same mirror as the one that was initially configured for the primary database during setup. For details, see the section "Using Lync Server Management Shell Cmdlets" in [Deploying SQL mirroring for Back End Server high availability in Lync Server 2013](lync-server-2013-deploying-sql-mirroring-for-back-end-server-high-availability.md).

7.  Set the Persistent Chat Server active servers. From the Lync Server Command Shell, use the **Set-CsPersistentChatActiveServer** cmdlet to set the list of active servers.
    
    <div>
    

    > [!IMPORTANT]  
    > All the active servers must be located within the same data center as the new primary database, or in a data center that has a low latency/high bandwidth connection to the database.

    
    </div>
    
    At this point, the failover from the Persistent Chat Server primary database to the Persistent Chat Server backup database completes successfully.

</div>

</div>

<span> </span>

</div>

</div>

</div>

