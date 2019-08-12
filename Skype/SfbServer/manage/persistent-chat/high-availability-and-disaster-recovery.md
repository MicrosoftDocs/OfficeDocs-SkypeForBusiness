---
title: "Manage high availability and disaster recovery for Persistent Chat Server in Skype for Business Server 2015"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 1/31/2018
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 4346e70b-ac48-4ab9-853e-3cdd6dcfe678
description: "Summary: Learn how to manage Persistent Chat Server high availability and disaster recovery in Skype for Business Server 2015."
---

# Manage high availability and disaster recovery for Persistent Chat Server in Skype for Business Server 2015
 
**Summary:** Learn how to manage Persistent Chat Server high availability and disaster recovery in Skype for Business Server 2015.
  
This topic describes how to fail over and fail back Persistent Chat Server. Before reading this topic, be sure to read [Plan for high availability and disaster recovery for Persistent Chat Server in Skype for Business Server 2015](../../plan-your-deployment/persistent-chat-server/high-availability-and-disaster-recovery.md) and [Configure high availability and disaster recovery for Persistent Chat Server in Skype for Business Server 2015](../../deploy/deploy-persistent-chat-server/configure-hadr-for-persistent-chat.md).

> [!NOTE]
> Persistent chat is available in Skype for Business Server 2015 but is no longer supported in Skype for Business Server 2019. The same functionality is available in Teams. For more information, see [Getting started with your Microsoft Teams upgrade](/microsoftteams/upgrade-start-here). If you need to use Persistent chat, your choices are to either migrate users requiring this functionality to Teams, or to continue using Skype for Business Server 2015. 
  
## Fail over Persistent Chat Server

Failover for Persistent Chat Server is designed to be mainly a manual process.
  
The failover procedure is based on the assumption that the secondary data center is up and running, but the Persistent Chat Server services where the primary Persistent Chat database is located are completely unavailable, including the following:
  
- Persistent Chat Server primary database and Persistent Chat Server mirror database are down.
    
- Skype for Business Server Front End Server is down.
    
The procedure is based on two basic steps:
  
- Recover the primary Persistent Chat database (mgc).
    
- Establish mirroring for the new primary database.
    
The Persistent Chat compliance database (mgccomp) is not failed over. The contents of this database are transient and are purged as the compliance adapter processes the data. It is your responsibility, as Persistent Chat Administrator, to correctly manage the adapter output to avoid data loss.
  
To fail over Persistent Chat Server:
  
1. Remove log shipping from the Persistent Chat Server Backup Log Shipping database.
    
   - Using SQL Server Management Studio, connect to the database instance where the Persistent Chat Server backup mgc database is located.
    
   - Open a query window to the master database.
    
   - Use the following command to drop log shipping:
    
   ```
   exec sp_delete_log_shipping_secondary_database mgc
   ```

2. Copy any uncopied backup files from the backup share to the copy destination folder of the backup server.
    
3. Apply any unapplied transaction log backups in sequence to the secondary database. For details, see [How to: Apply a Transaction Log Backup (Transact-SQL)](https://go.microsoft.com/fwlink/p/?linkid=247428).
    
4. Bring the backup mgc database online. Using the query window that opens in step 1b, do the following:
    
   - End all connections to the mgc database, if there are any:
    
   - **exec sp_who2** to identify connections to the mgc database.
    
   - **kill \<spid\>** to end these connections.
    
   - Bring the database online:
    
   - **restore database mgc with recovery**.
    
5. In Skype for Business Server Management Shell, use the command **Set-CsPersistentChatState -Identity "service:atl-cs-001.litwareinc.com" -PoolState FailedOver** to fail over to the mgc backup database. Be sure to substitute the fully qualified domain name of your Persistent Chat pool for atl-cs-001.litwareinc.com.
    
    The mgc backup database now serves as the primary database.
    
6. In Skype for Business Server Management Shell, use the **Install-CsMirrorDatabase** cmdlet to establish a high availability mirror for the backup database that now serves as the primary database. Use the backup database instance as the primary database and the backup mirror database instance as the mirror instance. This is not the same mirror as the one that was initially configured for the primary database during setup.
    
7. Set the Persistent Chat Server active servers. From the Skype for Business Server Management Shell, use the **Set-CsPersistentChatActiveServer** cmdlet to set the list of active servers.
    
    > [!IMPORTANT]
    > All the active servers must be located within the same data center as the new primary database, or in a data center that has a low latency/high bandwidth connection to the database. 
  
    At this point, the failover from the Persistent Chat Server primary database to the Persistent Chat Server backup database completes successfully.
    
## Fail back Persistent Chat Server

This procedure outlines the steps necessary to recover from a Persistent Chat Server failure, and to reestablish operations from the primary data center.
  
During Persistent Chat Server failure, the primary data center suffers complete outage, and the primary and mirror databases become unavailable. The primary data center fails over to the backup server.
  
The following procedure restores normal operation after the primary data center is back up, and the servers have been rebuilt. The procedure assumes that the primary data center has been recovered from total outage, and that the mgc database and the mgccomp database have been rebuilt and reinstalled by using Topology Builder.
  
The procedure also assumes that no new mirror and backup servers were deployed during the failover period, and that the only server deployed is the backup server and its mirror server, as defined in Fail over Persistent Chat Server previously.
  
These steps are designed to recover configuration as it existed prior to the disaster, resulting in failover from the primary server to the backup server.
  
1. Clear all servers from the Persistent Chat Server Active Server list by using the **Set-CsPersistentChatActiveServer** cmdlet from the Skype for Business Server Management Shell. This stops all Persistent Chat Servers from connecting to the mgc database and the mgccomp database during failback.
    
    > [!IMPORTANT]
    > The SQL Server agent on the secondary Persistent Chat Server Back End Server should be running under a privileged account. Specifically, the account must include: 
  
   - Read access to the network share that backups are being placed in.
    
   - Write access to the specific local directory that the backups are being copied to.
    
2. Disable mirroring on the backup mgc database:
    
   - Using SQL Server Management Studio, connect to the backup mgc instance.
    
   - Right-click the mgc database, point to **Tasks**, and then click **Mirror**.
    
   - Click **Remove Mirroring**.
    
   - Click **OK**.
    
   - Perform the same steps with the mgccomp database.
    
3. Back up the mgc database so that it can be restored to the new primary database:
    
   - Using SQL Server Management Studio, connect to the backup mgc instance.
    
   - Right-click the mgc database, point to **Tasks**, and then click **Back Up**. The **Back Up Database** dialog box appears.
    
   - In **Backup type**, select **Full**.
    
   - For **Backup component**, click **Database**.
    
   - Either accept the default backup set name suggested in **Name**, or enter a different name for the backup set.
    
   -  *\<Optional\>*  In **Description**, enter a description of the backup set.
    
   - Remove the default backup location from the destination list.
    
   - Add a file to the list by using the path to the share location that you established for log shipping. This path is available to the primary database and to the backup database.
    
   - Click **OK** to close the dialog box and begin the backup process.
    
4. Restore the primary database by using the backup database created in the previous step.
    
   - Using SQL Server Management Studio, connect to the primary mgc instance.
    
   - Right-click the mgc database, point to **Tasks**, point to **Restore**, and then click **Database**. The **Restore Database** dialog box appears.
    
   - Select **From Device**.
    
   - Click the browse button, which opens the **Specify Backup** dialog box. In **Backup media**, select **File**. Click **Add**, select the backup file that you created in step 3, and then click **OK**.
    
   - In **Select the backup sets to restore**, select the backup.
    
   - Click **Options** in the **Select a page** pane.
    
   - In **Restore options**, select **Overwrite the existing database**.
    
   - In **Recovery State**, select **Leave the database ready to use**.
    
   - Click **OK** to begin the restoration process.
    
5. Configure SQL Server Log Shipping for the primary database. Follow the procedures in [Configure high availability and disaster recovery for Persistent Chat Server in Skype for Business Server 2015](../../deploy/deploy-persistent-chat-server/configure-hadr-for-persistent-chat.md) to establish log shipping for the primary mgc database.
    
6. Set the Persistent Chat Server active servers. From the Skype for Business Server Management Shell, use the **Set-CsPersistentChatActiveServer** cmdlet to set the list of active servers.
    
    > [!IMPORTANT]
    > All the active servers must be located within the same data center as the new primary database, or in a data center that has a low latency/high bandwidth connection to the database. 
  
To restore the pool to its normal state run the following Windows PowerShell command:
  
```
Set-CsPersistentChatState -Identity "service: lyncpc.dci.discovery.com" -PoolState Normal
```

For more information, see the help topic for the [Set-CsPersistentChatState](https://docs.microsoft.com/powershell/module/skype/set-cspersistentchatstate?view=skype-ps) cmdlet.
  

