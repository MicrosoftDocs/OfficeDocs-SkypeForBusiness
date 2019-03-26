---
title: 'Lync Server 2013: Failing back Persistent Chat Server'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Failing back Persistent Chat Server
ms:assetid: 67b91de4-6ddc-43e6-9812-5e1aa84a7980
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204970(v=OCS.15)
ms:contentKeyID: 48184396
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Failing back Persistent Chat Server in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-02-05_

This procedure outlines the steps necessary to recover from a Persistent Chat Server failure, and to reestablish operations from the primary data center.

During Persistent Chat Server failure, the primary data center suffers complete outage, and the primary and mirror databases become unavailable. The primary data center fails over to the backup server.

The following procedure restores normal operation after the primary data center is back up, and the servers have been rebuilt. The procedure assumes that the primary data center has been recovered from total outage, and that the mgc database and the mgccomp database have been rebuilt and reinstalled by using Topology Builder.

The procedure also assumes that no new mirror and backup servers were deployed during the failover period, and that the only server deployed is the backup server and its mirror server, as defined in [Failing over Persistent Chat Server in Lync Server 2013](lync-server-2013-failing-over-persistent-chat-server.md).

These steps are designed to recover configuration as it existed prior to the disaster, resulting in failover from the primary server to the backup server.

<div>

## To fail back Persistent Chat Server

1.  Clear all servers from the Persistent Chat Server Active Server list by using the `Set-CsPersistentChatActiveServer` cmdlet from the Lync Server Management Shell. This stops all Persistent Chat Servers from connecting to the mgc database and the mgccomp database during failback.
    
    <div>
    

    > [!IMPORTANT]  
    > The SQL Server agent on the secondary Persistent Chat Server Back End Server should be running under a privileged account. Specifically, the account must include: 
    > <UL>
    > <LI>
    > <P>Read access to the network share that backups are being placed in.</P>
    > <LI>
    > <P>Write access to the specific local directory that the backups are being copied to.</P></LI></UL>

    
    </div>

2.  Disable mirroring on the backup mgc database:
    
    1.  Using SQL Server Management Studio, connect to the backup mgc instance.
    
    2.  Right-click the mgc database, point to **Tasks**, and then click **Mirror**.
    
    3.  Click **Remove Mirroring**.
    
    4.  Click **OK**.
    
    5.  Perform the same steps with the mgccomp database.

3.  Back up the mgc database so that it can be restored to the new primary database:
    
    1.  Using SQL Server Management Studio, connect to the backup mgc instance.
    
    2.  Right-click the mgc database, point to **Tasks**, and then click **Back Up**. The **Back Up Database** dialog box appears.
    
    3.  In **Backup type**, select **Full**.
    
    4.  For **Backup component**, click **Database**.
    
    5.  Either accept the default backup set name suggested in **Name**, or enter a different name for the backup set.
    
    6.  *\<Optional\>* In **Description**, enter a description of the backup set.
    
    7.  Remove the default backup location from the destination list.
    
    8.  Add a file to the list by using the path to the share location that you established for log shipping. This path is available to the primary database and to the backup database.
    
    9.  Click **OK** to close the dialog box and begin the backup process.

4.  Restore the primary database by using the backup database created in the previous step.
    
    1.  Using SQL Server Management Studio, connect to the primary mgc instance.
    
    2.  Right-click the mgc database, point to **Tasks**, point to **Restore**, and then click **Database**. The **Restore Database** dialog box appears.
    
    3.  Select **From Device**.
    
    4.  Click the browse button, which opens the **Specify Backup** dialog box. In **Backup media**, select **File**. Click **Add**, select the backup file that you created in step 3, and then click **OK**.
    
    5.  In **Select the backup sets to restore**, select the backup.
    
    6.  Click **Options** in the **Select a page** pane.
    
    7.  In **Restore options**, select **Overwrite the existing database**.
    
    8.  In **Recovery State**, select **Leave the database ready to use**.
    
    9.  Click **OK** to begin the restoration process.

5.  Configure SQL Server Log Shipping for the primary database. Follow the procedures in [Configuring Persistent Chat Server for high availability and disaster recovery in Lync Server 2013](lync-server-2013-configuring-persistent-chat-server-for-high-availability-and-disaster-recovery.md) to establish log shipping for the primary mgc database.

6.  Set the Persistent Chat Server active servers. From the Lync Server Management Shell, use the **Set-CsPersistentChatActiveServer** cmdlet to set the list of active servers.
    
    <div>
    

    > [!IMPORTANT]  
    > All the active servers must be located within the same data center as the new primary database, or in a data center that has a low latency/high bandwidth connection to the database.

    
    </div>

The restore the pool to its normal state run the following Windows PowerShell command:

    Set-CsPersistentChatState -Identity "service: lyncpc.dci.discovery.com" -PoolState Normal

See the help topic for the [Set-CsPersistentChatState](https://docs.microsoft.com/powershell/module/skype/Set-CsPersistentChatState) cmdlet for more information.

</div>

</div>

<span> </span>

</div>

</div>

</div>

