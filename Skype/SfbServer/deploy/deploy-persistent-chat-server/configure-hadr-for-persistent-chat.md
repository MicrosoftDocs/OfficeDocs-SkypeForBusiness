---
title: "Configure high availability and disaster recovery for Persistent Chat Server in Skype for Business Server 2015"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 2/7/2018
audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 5fb5b189-56c1-49cf-92c8-e4fd6e2fdd5c
description: "Summary: Read this topic to learn how to configure high availability and disaster recovery for Persistent Chat Server in Skype for Business Server 2015."
---

# Configure high availability and disaster recovery for Persistent Chat Server in Skype for Business Server 2015
 
**Summary:** Read this topic to learn how to configure high availability and disaster recovery for Persistent Chat Server in Skype for Business Server 2015.
  
Skype for Business Server supports multiple modes of high availability for your Back End Servers, including database mirroring. For more information, see [Plan for high availability and disaster recovery in Skype for Business Server 2015](../../plan-your-deployment/high-availability-and-disaster-recovery/high-availability-and-disaster-recovery.md).
  
> [!NOTE]
> AlwaysOn Availability Groups are not supported with Persistent Chat Servers. 

> [!NOTE] 
> Persistent chat is available in Skype for Business Server 2015 but is no longer supported in Skype for Business Server 2019. The same functionality is available in Teams. For more information, see [Journey from Skype for Business to Microsoft Teams](/microsoftteams/journey-skypeforbusiness-teams). If you need to use Persistent chat, your choices are to either migrate users requiring this functionality to Teams, or to continue using Skype for Business Server 2015.
  
Before you configure your Persistent Chat deployment for high availability and disaster recovery, be sure you are familiar with the concepts in [Plan for high availability and disaster recovery for Persistent Chat Server in Skype for Business Server 2015](../../plan-your-deployment/persistent-chat-server/high-availability-and-disaster-recovery.md). The disaster recovery solution for Persistent Chat Server described in these topics is built on a stretched Persistent Chat Server pool. The planning content describes resource requirements, and the stretched pool topology that enables high availability and disaster recovery for Persistent Chat Server, including using SQL Server mirroring for high availability and SQL Server log shipping for disaster recovery.
  
## Use Topology Builder to configure high availability and disaster recovery

Within Topology Builder, perform the following steps to configure high availability and disaster recovery for Persistent Chat Server.
  
1. Add the mirror databases and the log shipping secondary database SQL Server stores.
    
2. Edit the Persistent Chat Server service properties to:
    
    a. Enable mirroring for the primary database.
    
    b. Add the primary mirror SQL Server store.
    
    c. Enable the SQL Server Log Shipping database.
    
    d. Add the SQL Server Log Shipping secondary SQL Server store.
    
    e. Add the SQL Server store mirror for the secondary database.
    
    f. Publish the topology.
    
## Set up SQL Server log shipping for the Persistent Chat Server primary database

Using SQL Server Management Studio, connect to the Persistent Chat Server secondary Log Shipping database instance, and be sure that SQL Server Agent is running. Then connect to the Persistent Chat primary database instance and perform the following steps:
  
1. Right-click the mgc database, and then click **Properties**.
    
2. Under **Select a page**, click **Transaction Log Shipping**.
    
3. Select the **Enable this as a primary database in a log shipping configuration** check box.
    
4. Under **Transaction log backups**, click **Backup Settings**.
    
5. In the **Network path to the backup folder** box, type the network path to the share that you created for the transaction log backup folder.
    
6. If the backup folder is located on the primary server, type the local path to the backup folder in the **If the backup folder is located on the primary server, type a local path to the folder (example: c:\backup)** box. (If the backup folder is not on the primary server, you can leave this box empty.)
    
    > [!IMPORTANT]
    > If the SQL Server service account on your primary server runs under the local system account, you must create your backup folder on the primary server and specify a local path to that folder. 
  
7. Configure the **Delete files older than** and **Alert if no backup occurs within** parameters.
    
8. Look at the backup schedule listed in the **Schedule** box under **Backup job**. To customize the schedule for your installation, click **Schedule**, and adjust the SQL Server Agent schedule as required.
    
9. Under **Compression**, select **Use the default server setting**, and then click **OK**.
    
10. Under **Secondary server instances and databases**, click **Add**.
    
11. Click **Connect** and connect to the instance of SQL Server that you have configured as your secondary server.
    
12. In the **Secondary Database** box, select the **mgc** database from the list.
    
13. On the **Initialize Secondary database** tab, choose the option **Yes, generate a full backup of the primary database and restore it into the secondary database (and create the secondary database if it doesn't exist)**.
    
14. On the **Copy Files** tab, in the **Destination folder for copied files** box, type the path of the folder into which the transaction logs backups should be copied. This folder is often located on the secondary server.
    
15. Note the copy schedule listed in the **Schedule** box under **Copy job**. To customize the schedule for your installation, click **Schedule**, and adjust the SQL Server Agent schedule as required. This schedule should be approximately the same as the backup schedule.
    
16. On the **Restore** tab, under **Database state when restoring backups**, choose the **No recovery mode** option.
    
17. Under **Delay restoring backups at least:**, select **0 minutes**.
    
18. Choose an alert threshold under **Alert if no restore occurs within**.
    
19. Look at the restore schedule listed in the **Schedule** box under **Restore job**. To customize the schedule for your installation, click **Schedule**, adjust the SQL Server Agent schedule as required, and click **OK**. This schedule should be approximately the same as the backup schedule.
    
20. On the **Database Properties** dialog box, click **OK** to begin the configuration process.
    
## Set up SQL Server log shipping between the primary mirror and the secondary database

Perform the following steps for log shipping to continue if the primary Persistent Chat database is failed over to its mirror database.
  
1. Manually fail over the primary Persistent Chat database to the mirror. This is done by using the Skype for Business Server Management Shell and the **Invoke-CsDatabaseFailover** cmdlet.
    
2. Using the SQL Server Management Studio, connect to the primary Persistent Chat Server mirror instance.
    
3. Be sure that the SQL Server Agent is running.
    
4. Right-click the mgc database, and then click **Properties**.
    
5. Under **Select a page**, click **Transaction Log Shipping**.
    
6. Select the **Enable this as a primary database in a log shipping configuration** check box.
    
7. Under **Transaction log backups**, click **Backup Settings**.
    
8. In the **Network path to the backup folder** box, type the network path to the share you created for the transaction log backup folder.
    
9. If the backup folder is located on the primary server, type the local path to the backup folder in the **If the backup folder is located on the primary server, type a local path to the folder** box. (If the backup folder is not on the primary server, you can leave this box empty.)
    
    > [!IMPORTANT]
    > If the SQL Server service account on your primary server runs under the local system account, you must create your backup folder on the primary server and specify a local path to that folder. 
  
10. Configure the **Delete files older than** and **Alert if no backup occurs within** parameters.
    
11. Look at the backup schedule listed in the **Schedule** box under **Backup job**. To customize the schedule for your installation, click **Schedule**, and adjust the SQL Server Agent schedule, as required.
    
    > [!IMPORTANT]
    > Use the same settings that you used for the primary database. 
  
12. Under **Compression**, select **Use the default server setting**, and click **OK**.
    
13. Under **Secondary server instances and databases**, click **Add**.
    
14. Click **Connect**, and connect to the instance of SQL Server that you have configured as your secondary server.
    
15. In the **Secondary Database** box, select the **mgc** database from the list.
    
16. On the **Initialize Secondary database** tab, select the option **No, the secondary database is initialized**.
    
17. On the **Copy Files** tab, in **Destination folder for copied files**, type the path of the folder into which the transaction logs backups should be copied, and click **OK**. This folder is often located on the secondary server.
    
18. Open the **Script Configuration** drop-down list, and select **Script Configuration to New Query Window**.
    
19. In the new query window, in **Database Properties**, click **OK** to begin the configuration process.
    
20. Select and run the first half of the query (see step 18) up to the line: -- \*\*\*\*\*\* End: Script to be run at Primary: \*\*\*\*\*\*.
    
    > [!IMPORTANT]
    > Manually running this script is necessary because SQL Server Management Studio does not support multiple primary databases in a SQL Server Log Shipping configuration. 
  
21. Select **Cancel** to close the Log File shipping configuration panel and to establish a working setup that correctly implements the log file shipping for both the primary and mirrored database (in case of failover).
    
22. Manually fail back the primary Persistent Chat database to the primary. This is done by using the Skype for Business Server Management Shell, and the **Invoke-CsDatabaseFailover** cmdlet.
    

