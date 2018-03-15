---
title: "Restoring an Enterprise Edition Back End Server in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 1450eb4e-3315-4d02-8f02-6e1791fb1550
description: "Use the procedure described in this topic in the following two cases:"
---

# Restoring an Enterprise Edition Back End Server in Lync Server 2013
[]
Use the procedure described in this topic in the following two cases:
  
- Both the primary and mirror databases of a mirrored Enterprise Edition Back End Server fail.
    
- An Enterprise Edition Back End Server that is not mirrored fails.
    
If you have a mirrored Enterprise Edition Back End and only the mirror or primary database fails, see [Restoring a mirrored Enterprise Edition Back End Server in Lync Server 2013 - primary](restoring-a-mirrored-enterprise-edition-back-end-serverprimary.md) for restoring the primary database, and [Restoring a mirrored Enterprise Edition Back End Server in Lync Server 2013 - mirror](restoring-a-mirrored-enterprise-edition-back-end-servermirror.md) for restoring the mirror. 
  
If the Central Management store fails, see [Restoring the server hosting the Central Management store in Lync Server 2013](restoring-the-server-hosting-the-central-management-store.md). If an Enterprise Edition member server that is not the Back End Server fails, see [Restoring an Enterprise Edition member server in Lync Server 2013](restoring-an-enterprise-edition-member-server.md).
  
> [!TIP]
> We recommend that you take an image copy of the system before you start restoration. You can use this image as a rollback point, in case something goes wrong during restoration. You might want to take the image copy after you install the operating system and SQL Server, and restore or reenroll the certificates. 
  
### To restore an Enterprise Edition Back End Server

1. Start with a clean or new server that has the same fully qualified domain name (FQDN) as the failed computer, install the operating system, and then restore or reenroll the certificates. 
    
    > [!NOTE]
    > Follow your organization's server deployment procedures to perform this step. 
  
2. From a user account that is a member of the RTCUniversalServerAdmins group, log on to the server that you are restoring.
    
3. Install SQL Server 2012 or SQL Server 2008 R2, keeping the instance names the same as before the failure.
    
    > [!NOTE]
    > Depending on your deployment, the Back End Server might include multiple collocated or separate databases. Follow the same procedure to install SQL Server that you used originally to deploy the server, including SQL Server permissions and logins. 
  
4. After you install SQL Server, perform the following:
    
1. Start Topology Builder: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Topology Builder**.
    
2. Click **Download Topology from existing deployment**, and then click **OK**. 
    
3. Select the topology, and then click **Save**. Click **Yes** to confirm your selection. 
    
4. Right-click the **Lync Server 2013** node, and then click **Publish Topology**.
    
5. Follow the **Publish the Topology** wizard. On the **Create databases** page, select the databases that you want to re-create. 
    
    > [!NOTE]
    > Only stand-alone databases are displayed on the **Create databases** page. 
  
6. If you are restoring a Back End that was mirrored, continue to follow the rest of the wizard until the prompt **Create Mirror Database** appears. Select the database that you want to install, and complete the process. 
    
7. Follow the rest of the wizard, and then click **Finish**.
    
    > [!TIP]
    > Instead of running Topology Builder, you can use the **Install-CsDatabase** cmdlet to create each database, and the **Install-CsMirrorDatabase** cmdlet to configure mirroring. For details, see the Lync Server Management Shell documentation. 
  
5. Restore user data by performing the following: 
    
1. Copy ExportedUserData.zip from $Backup\ to a local directory.
    
2. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
3. Before you restore the user data, you must stop Lync services. To do so, type:
    
  ```
  Stop-CsWindowsService
  ```

4. To restore the user data, at the command line, type:
    
  ```
  Import-CsUserData -PoolFqdn <Fqdn> -FileName <String>
  ```

    For example:
    
  ```
  Import-CsUserData -PoolFqdn "atl0cs-001.litwareinc.com" -FileName "C:\Logs\ExportedUserDatal.zip"
  ```

5. Restart Lync Services by typing:
    
  ```
  Start-CsWindowsService
  ```

6. If you deployed Response Group on this pool, restore the Response Group configuration data. For details, see [Restoring Response Group settings in Lync Server 2013](restoring-response-group-settings.md).
    
7. If you are restoring a Back End Server that included Archiving or Monitoring databases, restore the Archiving or Monitoring data by using a SQL Server tool, such as SQL Server Management Studio. For details, see [Restoring monitoring or archiving data in Lync Server 2013](restoring-monitoring-or-archiving-data.md).
    

