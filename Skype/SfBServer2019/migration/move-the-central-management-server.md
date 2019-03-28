---
title: "Move the Central Management Server"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "After migrating to Skype for Business Server 2019, you need to move the Central Management Server to the Skype for Business Server 2019 Front End Server or pool, before you can remove the legacy server."
---

# Move the legacy Central Management Server to Skype for Business Server 2019

After migrating to Skype for Business Server 2019, and before you can remove the legacy server, you need to move the Central Management Server to the Skype for Business Server 2019 Front End Server or pool. 
  
The Central Management Server is a single master/multiple replica system, where the read/write copy of the database is held by the Front End Server that contains the Central Management Server. Each computer in the topology, including the Front End Server that contains the Central Management Server, has a read-only copy of the Central Management store data in the SQL Server database (named RTCLOCAL by default) installed on the computer during setup and deployment. The local database receives replica updates by way of the Skype for Business Server Replica Replicator Agent that runs as a service on all computers. The name of the actual database on the Central Management Server and the local replica is XDS, which is made up of the xds.mdf and xds.ldf files. The master database location is referenced by a service control point (SCP) in Active Directory Domain Services. All tools that use the Central Management Server to manage and configure Skype for Business Server use the SCP to locate the Central Management store.
  
After you have successfully moved the Central Management Server, you should remove the Central Management Server databases from the original Front End Server. For information on removing the Central Management Server databases, see [Remove the SQL Server database for a Front End pool](remove-the-sql-server-database-for-a-front-end-pool.md).
  
You use the Windows PowerShell cmdlet **Move-CsManagementServer** in the Skype for Business Server Management Shell to move the database from the legacy install SQL Server database to the Skype for Business Server 2019 SQL Server database, and then update the SCP to point to the Skype for Business Server 2019 Central Management Server location. 
  
Use the procedures in this section to prepare the Skype for Business Server 2019 Front End Servers before you move the Central Management Server.
  
## To prepare an Enterprise Edition Front End pool

1. On the Skype for Business Server 2019 Enterprise Edition Front End pool where you want to relocate the Central Management Server, log on to the computer where the Skype for Business Server Management Shell is installed as a member of the **RTCUniversalServerAdmins** group. You must also have SQL Server database sysadmin user rights and permissions on the database where you want to install the Central Management store. 
    
2. Open the Skype for Business Server Management Shell.
    
3. To create the new Central Management store in the Skype for Business Server 2019 SQL Server database, in the Skype for Business Server Management Shell, type:
    
   ```
   Install-CsDatabase -CentralManagementDatabase -SQLServerFQDN <FQDN of your SQL Server> -SQLInstanceName <name of instance>
   ```

4. Confirm that the status of the **Skype for Business Server Front-End** service is **Started**.
    
## To prepare a Standard Edition Front End Server

1. On the Skype for Business Server 2019 Standard Edition Front End Server where you want to relocate the Central Management Server, log on to the computer where the Skype for Business Server Management Shell is installed as a member of the **RTCUniversalServerAdmins** group. 
    
2. Open the Skype for Business Server Deployment Wizard.
    
3. In the Skype for Business Server Deployment Wizard, click **Prepare first Standard Edition server**.
    
4. On the **Executing Commands** page, SQL Server Express is installed as the Central Management Server. Necessary firewall rules are created. When the installation of the database and prerequisite software is completed, click **Finish**.
    
    > [!NOTE]
    > The initial installation may take some time with no visible updates to the command output summary screen. This is due to the installation of SQL Server Express. If you need to monitor the installation of the database, use Task Manager to monitor the setup. 
  
5. To create the new Central Management store on the Skype for Business Server 2019 Standard Edition Front End Server, in the Skype for Business Server Management Shell, type: 
    
   ```
   Install-CsDatabase -CentralManagementDatabase -SQLServerFQDN <FQDN of your Standard Edition Server> -SQLInstanceName <name of instance - RTC by default>
   ```

6. Confirm that the status of the **Skype for Business Server Front-End** service is **Started**.
    
## To move the legacy installs Central Management Server to Skype for Business Server 2019

1. On the Skype for Business Server 2019 server that will be the Central Management Server, log on to the computer where the Skype for Business Server Management Shell is installed as a member of the **RTCUniversalServerAdmins** group. You must also have the SQL Server database administrator user rights and permissions. 
    
2. Open Skype for Business Server Management Shell.
    
3. In the Skype for Business Server Management Shell, type: 
    
   ```
   Enable-CsTopology
   ```

    > [!CAUTION]
    > If `Enable-CsTopology` is not successful, resolve the problem preventing the command from completing before continuing. If **Enable-CsTopology** is not successful, the move will fail and it may leave your topology in a state where there is no Central Management store. 
  
4. On the Skype for Business Server 2019 Front End Server or Front End pool, in the Skype for Business Server Management Shell, type: 
    
   ```
   Move-CsManagementServer
   ```

5. Skype for Business Server Management Shell displays the servers, file stores, database stores, and the service connection points of the Current State and the Proposed State. Read the information carefully and confirm that this is the intended source and destination. Type **Y** to continue, or **N** to stop the move. 
    
6. Review any warnings or errors generated by the **Move-CsManagementServer** command and resolve them. 
    
7. On the Skype for Business Server 2019 server, open the Skype for Business Server Deployment Wizard. 
    
8. In Skype for Business Server Deployment Wizard, click **Install or Update Skype for Business Server System**, click **Step 2: Setup or Remove Skype for Business Server Components**, click **Next**, review the summary, and then click **Finish**. 
    
9. On the legacy install server, open the Deployment Wizard. 
    
10. In Skype for Business Server Deployment Wizard, click **Install or Update Skype for Business Server System**, click **Step 2: Setup or Remove Skype for Business Server Components**, click **Next**, review the summary, and then click **Finish**. 
    
11. Reboot the Skype for Business Server 2019 server. This is required because of a group membership change to access Central Management Server database.
    
12. To confirm that replication with the new Central Management store is occurring, in the Skype for Business Server Management Shell, type: 
    
    ```
    Get-CsManagementStoreReplicationStatus
    ```

    > [!NOTE]
    > The replication may take some time to update all current replicas. 
  
## To remove legacy install Central Management store files after a move

1. On the legacy install server, log on to the computer where the Skype for Business Server Management Shell is installed as a member of the **RTCUniversalServerAdmins** group. You must also have the SQL Server database administrator user rights and permissions. 
    
2. Open Skype for Business Server Management Shell
    
    > [!CAUTION]
    > Do not proceed with the removal of the previous database files until replication is complete and is stable. If you remove the files prior to completing replication, you will disrupt the replication process and leave the newly moved Central Management Server in an unknown state. Use the cmdlet **Get-CsManagementStoreReplicationStatus** to confirm the replication status. 
  
3. To remove the Central Management store database files from the legacy install Central Management Server, type:
    
   ```
   Uninstall-CsDatabase -CentralManagementDatabase -SqlServerFqdn <FQDN of SQL Server> -SqlInstanceName <Name of source server>
   ```

    For example:
    
   ```
   Uninstall-CsDatabase -CentralManagementDatabase -SqlServerFqdn sql.contoso.net -SqlInstanceName rtc
   ```

    Where the  _\<FQDN of SQL Server\>_ is either the legacy install Back End Server in an Enterprise Edition deployment or the FQDN of the Standard Edition server. 
    

