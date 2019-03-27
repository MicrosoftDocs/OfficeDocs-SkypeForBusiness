---
title: 'Lync Server 2013: Setting up SQL Server Log Shipping between the primary mirror and the Log Shipping secondary database'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Setting up SQL Server Log Shipping between the primary mirror and the Log Shipping secondary database
ms:assetid: 4e8e9ce9-4301-47f2-a0c3-669afeb53295
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204887(v=OCS.15)
ms:contentKeyID: 48184119
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Setting up SQL Server Log Shipping between the primary mirror and the Log Shipping secondary database in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

Perform the following steps for log shipping to continue if the primary Persistent Chat database is failed over to its mirror database.

1.  Manually fail over the primary Persistent Chat database to the mirror. This is done by using the Lync Server Management Shell and the **Invoke-CsDatabaseFailover** cmdlet. For details, see "Using Lync Server Management Shell Cmdlets" in [Deploying SQL mirroring for Back End Server high availability in Lync Server 2013](lync-server-2013-deploying-sql-mirroring-for-back-end-server-high-availability.md).

2.  Using the SQL Server Management Studio, connect to the primary Persistent Chat Server mirror instance.

3.  Be sure that the SQL Server Agent is running.

4.  Right-click the mgc database, and then click **Properties**.

5.  Under **Select a page**, click **Transaction Log Shipping**.

6.  Select the **Enable this as a primary database in a log shipping configuration** check box.

7.  Under **Transaction log backups**, click **Backup Settings**.

8.  In the **Network path to the backup folder** box, type the network path to the share you created for the transaction log backup folder.

9.  If the backup folder is located on the primary server, type the local path to the backup folder in the **If the backup folder is located on the primary server, type a local path to the folder** box. (If the backup folder is not on the primary server, you can leave this box empty.)
    
    <div>
    

    > [!IMPORTANT]  
    > If the SQL Server service account on your primary server runs under the local system account, you must create your backup folder on the primary server and specify a local path to that folder.

    
    </div>

10. Configure the **Delete files older than** and **Alert if no backup occurs within** parameters.

11. Look at the backup schedule listed in the **Schedule** box under **Backup job**. To customize the schedule for your installation, click **Schedule**, and adjust the SQL Server Agent schedule, as required.
    
    <div>
    

    > [!IMPORTANT]  
    > Use the same settings that you used for the primary database.

    
    </div>

12. Under **Compression**, select **Use the default server setting**, and click **OK**.

13. Under **Secondary server instances and databases**, click **Add**.

14. Click **Connect**, and connect to the instance of SQL Server that you have configured as your secondary server.

15. In the **Secondary Database** box, select the **mgc** database from the list.

16. On the **Initialize Secondary database** tab, select the option **No, the secondary database is initialized**.

17. On the **Copy Files** tab, in **Destination folder for copied files**, type the path of the folder into which the transaction logs backups should be copied, and click **OK**. This folder is often located on the secondary server.

18. Open the **Script Configuration** drop-down list, and select **Script Configuration to New Query Window**.

19. In the new query window, in **Database Properties**, click **OK** to begin the configuration process.

20. Select and run the first half of the query (see step 18) up to the line: -- \*\*\*\*\*\* End: Script to be run at Primary: \*\*\*\*\*\*.
    
    <div>
    

    > [!IMPORTANT]  
    > Manually running this script is necessary because SQL Server Management Studio does not support multiple primary databases in a SQL Server Log Shipping configuration.

    
    </div>

21. Select **Cancel** to close the Log File shipping configuration panel and to establish a working setup that correctly implements the log file shipping for both the primary and mirrored database (in case of failover).

22. Manually fail back the primary Persistent Chat database to the primary. This is done by using the Lync Server Management Shell, and the **Invoke-CsDatabaseFailover** cmdlet. For details, see "Using Lync Server Management Shell Cmdlets" in [Deploying SQL mirroring for Back End Server high availability in Lync Server 2013](lync-server-2013-deploying-sql-mirroring-for-back-end-server-high-availability.md).

<div>

## See Also


[Deploying SQL mirroring for Back End Server high availability in Lync Server 2013](lync-server-2013-deploying-sql-mirroring-for-back-end-server-high-availability.md)  
[Deploying SQL mirroring for Back End Server high availability in Lync Server 2013](lync-server-2013-deploying-sql-mirroring-for-back-end-server-high-availability.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

