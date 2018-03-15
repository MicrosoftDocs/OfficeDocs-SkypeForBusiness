---
title: "Restoring the server hosting the Central Management store in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3bd6c82c-07fb-4798-b8f9-e7c78a5a83d5
description: "A Lync Server deployment has a single Central Management store, a copy of which is replicated to each server running a Lync Server server role. This topic describes how to restore a Back End Server or Standard Edition server that hosts the Central Management store."
---

# Restoring the server hosting the Central Management store in Lync Server 2013
[]
A Lync Server deployment has a single Central Management store, a copy of which is replicated to each server running a Lync Server server role. This topic describes how to restore a Back End Server or Standard Edition server that hosts the Central Management store.
  
To find the pool where the Central Management Server is located, open Topology Builder, click **Lync Server**, and look in the right pane under **Central Management Server**.
  
If the Back End Server that hosts the Central Management store is in a mirrored setup and the mirror database is still functional, we recommend that you make a backup of this still-functioning mirror, and then perform a full restore on both the primary database and the mirror database, using this backup, by following the restoration procedure below. This is necessary because Back End restore requires modifying and publishing the topology, and this can be done only if the primary database hosting CMS is operational. Also note that the primary and mirror database roles cannot be interchanged if the topology cannot be published.
  
> [!NOTE]
> If a Back End Server or Standard Edition server that does not host the Central Management store failed, see [Restoring an Enterprise Edition Back End Server in Lync Server 2013](restoring-an-enterprise-edition-back-end-server.md) or [Restoring a Standard Edition server in Lync Server 2013](restoring-a-standard-edition-server.md). If a Back End Server that hosts the Central Management store is in a mirrored configuration and only the mirror failed, see [Restoring a mirrored Enterprise Edition Back End Server in Lync Server 2013 - mirror](restoring-a-mirrored-enterprise-edition-back-end-servermirror.md). If any other server failed, see [Restoring an Enterprise Edition member server in Lync Server 2013](restoring-an-enterprise-edition-member-server.md). 
  
> [!TIP]
> We recommend that you take an image copy of the system before you start restoration. You can use this image as a rollback point, in case something goes wrong during restoration. You might want to take the image copy after you install the operating system and SQL Server, and restore or reenroll the certificates. 
  
### To restore the Central Management store

1. Start with a clean or new server that has the same fully qualified domain name (FQDN) as the failed computer, install the operating system, and then restore or reenroll the certificates. 
    
    > [!NOTE]
    > Follow your organization's server deployment procedures to perform this step. 
  
2. From a user account that is a member of the RTCUniversalServerAdmins group and the Local Administrators group, log on to the server that you are restoring.
    
3. If you are restoring a Standard Edition server, restore the File Store by copying the appropriate File Store from $Backup to the File Store location on the server, and then share the folder.
    
    > [!IMPORTANT]
    > The path and file name for the restored File Store should be exactly the same as the backed up File Store so that components that use the files can access them. 
  
4. Do one of the following:
    
  - If you are installing a Standard Edition server, browse to the Lync Server installation folder or media, and then start the Lync Server Deployment Wizard located at \setup\amd64\Setup.exe. In the Deployment Wizard, click **Prepare first Standard Edition server** and follow the wizard to install the Central Management store. 
    
  - If you are installing an Enterprise Back End Server, install SQL Server 2012 or SQL Server 2008 R2, keeping the instance names the same as before the failure.
    
    > [!NOTE]
    > Depending on the server that you are restoring and on your deployment, the server might include multiple collocated or separate databases. Follow the same procedure to install SQL Server that you used originally to deploy the server, including SQL Server permissions and logins. 
  
5. From a Front End Server, Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
6. Re-create the Central Management store. At the command line, type:
    
  ```
  Install-CsDatabase -CentralManagementDatabase -Clean -SqlServerFqdn <FQDN> -SqlInstanceName <instance name> -Verbose
  ```

    For example:
    
  ```
  Install-CsDatabase -CentralManagementDatabase -Clean -SqlServerFqdn Server01.contoso.com -SqlInstanceName cms -Verbose
  ```

7. Set the Active Directory Domain Services control point for the Central Management store. At the command line, type:
    
  ```
  Set-CsConfigurationStoreLocation -SqlServerFqdn <FQDN> -SqlInstanceName <instance name> -Verbose
  ```

    For example:
    
  ```
  Set-CsConfigurationStoreLocation -SqlServerFqdn Server01.contoso.com -SqlInstanceName cms -Verbose
  ```

    > [!NOTE]
    > If you lose the connection point, you can rerun this cmdlet. 
  
8. Import the Central Management store data from $Backup. At the command line, type:
    
  ```
  Import-CsConfiguration -FileName <CMS backup file name>
  ```

    For example:
    
  ```
  Import-CsConfiguration -FileName "C:\Config.zip"
  ```

9. Enable the changes you have just made. At the command line, type:
    
  ```
  Enable-CsTopology
  ```

    > [!NOTE]
    > After you enable the topology, you can find the topology document in the database. 
  
10. If you are restoring an Enterprise Edition Back End Server that also hosted the CMS, or if you need to re-create a mirror of the CMS, then follow this step. Otherwise, skip to step 11. 
    
    Install the stand-alone databases by doing the following:
    
1. Start Topology Builder: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Topology Builder**.
    
2. Click **Download Topology from existing deployment**, and then click **OK**. 
    
3. Select the topology, and then click **Save**. Click **Yes** to confirm your selection. 
    
4. Right-click the **Lync Server 2013** node, and then click **Install Database**. 
    
5. Follow the **Install Database** wizard. If you are restoring a database other than the Central Management store on this server, on the **Create databases** page, select the databases you want to recreate. 
    
    > [!NOTE]
    > Only stand-alone databases are displayed on the **Create databases** page. Collocated databases are created when you run the Lync Server Deployment Wizard. 
  
6. If you are restoring a mirrored Back End Server, continue to follow the rest of the wizard until you come to a prompt of Create Mirror Database. Select the database you want to install, and complete the process.
    
7. Follow the rest of the wizard, and then click **Finish**.
    
    > [!TIP]
    > Instead of running Topology Builder, you can use the **Install-CsDatabase** cmdlet to create each database, and the **Install-CsMirrorDatabase** cmdlet to configure mirroring. For details, see [Install-CsDatabase](install-csdatabase.md) and [Install-CsMirrorDatabase](install-csmirrordatabase.md). 
  
11. If you are restoring a Standard Edition server, browse to the Lync Server installation folder or media, and start the Lync Server Deployment Wizard located at \setup\amd64\Setup.exe. Use the Lync Server Deployment Wizard to do the following:
    
1. Run **Step 1: Install Local Configuration Store** to install the local configuration files. 
    
2. Run **Step 2: Setup or Remove Lync Server Components** to install the Lync Server server roles. 
    
3. Run **Step 3: Request, Install or Assign Certificates** to assign the certificates. 
    
4. Run **Step 4: Start Services** to start services on the server. 
    
    For details about running the Deployment Wizard, see the Deployment documentation for the server role that you are restoring.
    
12. Restore user data by performing the following: 
    
1. Copy ExportedUserData.zip from $Backup\ to a local directory.
    
2. Before you restore the user data, you must stop Lync services. To do so, type:
    
  ```
  Stop-CsWindowsService
  ```

3. To restore the user data, at the command line, type:
    
  ```
  Import-CsUserData -PoolFqdn <Fqdn> -FileName <String>
  ```

    For example:
    
  ```
  Import-CsUserData -PoolFqdn "atl0cs-001.litwareinc.com" -FileName "C:\Logs\ExportedUserDatal.zip"
  ```

4. Restart Lync services by typing:
    
  ```
  Start-CsWindowsService
  ```

13. Restore Location Information data to the Central Management store. At the command line, type:
    
  ```
  Import-CsLisConfiguration -FileName <LIS backup file name>
  ```

    For example:
    
  ```
  Import-CsLisConfiguration -FileName "D:\E911Config.zip"
  ```

14. If you deployed Response Group on this pool or Standard Edition server, restore the Response Group configuration data. For details, see [Restoring Response Group settings in Lync Server 2013](restoring-response-group-settings.md).
    
15. If you are restoring a Back End Server that includes Archiving or Monitoring databases, restore the Archiving or Monitoring data by using a SQL Server management tool, such as SQL Server Management Studio. For details, see [Restoring monitoring or archiving data in Lync Server 2013](restoring-monitoring-or-archiving-data.md).
    

