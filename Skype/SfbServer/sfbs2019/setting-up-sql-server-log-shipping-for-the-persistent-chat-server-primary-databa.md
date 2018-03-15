---
title: "Setting up SQL Server Log Shipping in Lync Server 2013 for the Persistent Chat Server primary database"
ms.author: crowe
author: CarolynRowe
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 088ea1c2-d592-4a11-b3b8-f1e2f8beae93
description: "Using SQL Server Management Studio, connect to the Persistent Chat Server secondary Log Shipping database instance, and be sure that SQL Server Agent is running."
---

# Setting up SQL Server Log Shipping in Lync Server 2013 for the Persistent Chat Server primary database
[]
Using SQL Server Management Studio, connect to the Persistent Chat Server secondary Log Shipping database instance, and be sure that SQL Server Agent is running.
  
Using SQL Server Management Studio connected to the Persistent Chat primary database instance, perform the following steps:
  
1. Be sure that the SQL Server Agent is running.
    
2. Right-click the mgc database, and then click **Properties**.
    
3. Under **Select a page**, click **Transaction Log Shipping**.
    
4. Select the **Enable this as a primary database in a log shipping configuration** check box. 
    
5. Under **Transaction log backups**, click **Backup Settings**.
    
6. In the **Network path to the backup folder** box, type the network path to the share that you created for the transaction log backup folder. 
    
7. If the backup folder is located on the primary server, type the local path to the backup folder in the **If the backup folder is located on the primary server, type a local path to the folder (example: c:\backup)** box. (If the backup folder is not on the primary server, you can leave this box empty.) 
    
    > [!IMPORTANT]
    > If the SQL Server service account on your primary server runs under the local system account, you must create your backup folder on the primary server and specify a local path to that folder. 
  
8. Configure the **Delete files older than** and **Alert if no backup occurs within** parameters. 
    
9. Look at the backup schedule listed in the **Schedule** box under **Backup job**. To customize the schedule for your installation, click **Schedule**, and adjust the SQL Server Agent schedule as required.
    
10. Under **Compression**, select **Use the default server setting**, and then click **OK**.
    
11. Under **Secondary server instances and databases**, click **Add**.
    
12. Click **Connect** and connect to the instance of SQL Server that you have configured as your secondary server. 
    
13. In the **Secondary Database** box, select the **mgc** database from the list. 
    
14. On the **Initialize Secondary database** tab, choose the option **Yes, generate a full backup of the primary database and restore it into the secondary database (and create the secondary database if it doesn't exist)**.
    
15. On the **Copy Files** tab, in the **Destination folder for copied files** box, type the path of the folder into which the transaction logs backups should be copied. This folder is often located on the secondary server. 
    
16. Note the copy schedule listed in the **Schedule** box under **Copy job**. To customize the schedule for your installation, click **Schedule**, and adjust the SQL Server Agent schedule as required. This schedule should be approximately the same as the backup schedule.
    
17. On the **Restore** tab, under **Database state when restoring backups**, choose the **No recovery mode** option. 
    
18. Under **Delay restoring backups at least:**, select **0 minutes**.
    
19. Choose an alert threshold under **Alert if no restore occurs within**.
    
20. Look at the restore schedule listed in the **Schedule** box under **Restore job**. To customize the schedule for your installation, click **Schedule**, adjust the SQL Server Agent schedule as required, and click **OK**. This schedule should be approximately the same as the backup schedule.
    
21. On the **Database Properties** dialog box, click **OK** to begin the configuration process. 
    

