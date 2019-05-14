---
title: "Deploy an Always On Availability Group on a Back End Server in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: c93c01e6-626c-40ad-92dd-373b0fe9189f
description: "Deploy (install) an Always On Availability Group in your Skype for Business Server deployment."
---

# Deploy an Always On Availability Group on a Back End Server in Skype for Business Server
 
Deploy (install) an Always On Availability Group (AG) in your Skype for Business Server deployment.
  
How you deploy an AG depends on whether you are deploying it in a new pool, an existing pool that uses mirroring, or an existing pool that currently has no high availability for the Back End database.
  
> [!NOTE]
> Using an AG with a Persistent Chat Server role is not supported. 
  
- [Deploy an Always On Availability Group on a new Front End pool](alwayson-availability-group.md#BKMK_NewPool_CreateAlwaysOnGroup)
    
- [Deploy an Always On Availability Group on an existing pool that uses database mirroring](alwayson-availability-group.md#BKMK_MirroredPool_CreateAlwaysOnGroup)
    
- [Deploy an Always On Availability Group on an existing pool that does not use database mirroring](alwayson-availability-group.md#BKMK_NoHAPool_CreateAlwaysOnGroup)
    
## Deploy an Always On Availability Group on a new Front End pool
<a name="BKMK_NewPool_CreateAlwaysOnGroup"> </a>

1. Enable the Failover Clustering feature on all the database servers which will be part of the AG. On each server, do the following
    
   - Open Server Manager and click **Add roles and features**.
    
   - Click **Next** until you reach the **Select features** box. Here, select the **Failover Clustering** check box.
    
   - In the **Add features that are required for Failover Clustering?** box, click **Add Features**.
    
   - Click **Install**.
    
2. Validate the cluster configuration.
    
   - In Server Manager, click the **Tools** menu and then click **Failover Cluster Manager**.
    
   - Under **Actions** on the right side of the screen, click **Validate Configuration**.
    
   - On the **Before You Begin** page, click **Next**.
    
   - Select the servers to add to the cluster, and then click **Run all tests**.
    
   - In the **Summary** box, check any errors that the wizard reports. Then click **Finish** to complete the validation.
    
     The wizard will probably report several warnings, especially if you are not using shared storage. You are not required to use shared storage. However, if you see any **Error** messages, you must fix those issues before continuing.
    
3. Create the Windows Server Failover Cluster (WSFC).
    
   - In the **Failover Cluster Management** wizard, right-click **Failover Cluster Management**, then click **Create Cluster**.
    
   - On the **Before You Begin** page, click **Next**.
    
   - Add the cluster name and IP address. When the settings are validated, click **Next**.
    
   - On the Confirmation page, click **Next**.
    
   - After the cluster is created, click **Finish**.
    
4. We recommend that you configure the cluster quorum settings to use a file share witness. To do so, use these steps:
    
   - Right-click the cluster name, click **More Actions**, and click **Configure Cluster Quorum Settings**.
    
   - In the **Select Quorum Configuration Option** page, click **Select the quorum witness**.
    
   - In the **Select Quorum Witness** page, click **Configure a file share witness**.
    
   - In the **Configure File Share Witness** page, type the path of the file share you want to use, and then click **Next**.
    
   - On the **Confirmation** page, click **Next**.
    
5. On each server in the cluster, enable the AG feature in SQL Server Configuration Manager.
    
   - Open SQL Server Configuration Manager. In the tree on the left side of the screen, click **SQL Server Services**, then double-click the SQL Server service. 
    
   - In the **Properties** box, select the **AlwaysOn High Availability** tab. Select the **Enable AlwaysOn Availability Groups** check box. Restart the SQL Server service when prompted.
   
6. Use Topology Builder to create the Front End pool, as explained in [Create and publish new topology in Skype for Business Server](../../deploy/install/create-and-publish-new-topology.md). When you do, specify the AG as the SQL store for the pool.
    
7. Create the availability group.
    
   - Open SQL Server Management Studio, and connect to the SQL Server instance.
    
   - In Object Explorer, expand the **Always On High Availability** folder. Right-click the **Availability Groups** folder and click **New Availability Group Wizard**.
    
   - If the **Introduction** page appears, click **Next**.
    
   - In the **Specify Availability Group Name** page, type the name of the Availability group, and click **Next**.
    
   - In the Select Databases page, select the databases that you want to include in the AlwaysOn Availability Group. Then click **Next**.
    
     Do not include the **ReportServer**, **ReportServerTempDB**, or Persistent Chat databases in the AlwaysOn Availability Group, as these are not supported in this scenario. You can include all other Skype for Business Server databases in the AlwaysOn Availability Group.
    
   - In the **Specify Replicas** page, click the **Replicas** tab. Then click the **Add Replicas** button, and connect to the other SQL instances that you joined as nodes of the Windows Server Failover Cluster.
    
   - For each instance, select the **Automatic Failover** and **Synchronous Commit** options. Do not select the **Readable Secondary** option.
    
   - Click the **Endpoints** tab and verify that **Port Number** is set to 5022.
    
   - Click the **Listener** tab, and select the **Create an availability group listener** option. Under that option, type a name for the listener, and set the **Port** to 1433 (other ports are not supported for this option).
    
   - Click **Add**, and then in the **IPv4 Address** box, provide your preferred virtual IP address, and then click **OK**.
    
   - In the **Select Initial Data Synchronization** page, select Full, and specify a folder that is accessible to the replicas, and that the SQL Server service account used by both replicas has Write permissions for. Then click **Next**.
    
     This file share will be used temporarily when you initialize the databases. If you are dealing with large databases, we recommend that you manually initialize them in case your network bandwidth cannot accommodate the size of the database backups.
    
   - In the Validation page, verify that all validation checks are successful, then click **Next**.
    
   - In the **Summary** page, verify all settings and click Finish.
      
8. After the pool and the AG are deployed, perform some final steps to make sure that the SQL logins are on each of the replicas in the AlwaysOn Availability Group. 
    
   - Open Topology Builder, select **Download topology from existing deployment**, and click **OK**.
    
   - Expand Skype for Business Server, expand your topology, and expand **SQL Server Stores**. Right-click the SQL store of the new AlwaysOn Availability Group, and click **Edit Properties**.
    
     - At the bottom of the page, in the **SQL Server FQDN** box, change the value to the FQDN of the Listener of the AG.
    
   - Publish the topology. From the **Action** menu click **Topology** and then **Publish**. Then in the confirmation page click **Next**. Then wait a few minutes for the new topology to replicate.
    
   - Open SQL Server Management Studio, and navigate to the AG. Fail it over to a secondary replica.
    
   - Open Skype for Business Server Management Shell and type the following cmdlet to create the SQL logins on this replica:
    
   ```
   Install-CsDatabase -Update
   ```

   - Repeat the previous two steps (fail over the group to a secondary replica, then use  `Install-CsDatabase -Update`) for each replica in the group.
    
## Deploy an Always On Availability Group on an existing pool that uses database mirroring
<a name="BKMK_MirroredPool_CreateAlwaysOnGroup"> </a>

> [!NOTE]
> If the pool you are upgrading to an AG hosts the Central Management store for your organization, you must first move the CMS to another pool before you upgrade this pool. Use the Move-CsManagementServer cmdlet to move the pool. If you do not have another pool in your organization, you can deploy a Standard Edition server temporarily and move the CMS to this server before you upgrade your pool to the AG. 
  
1. Fail over all data from the mirror to the principal node by opening Skype for Business Server Management Shell and typing the following cmdlet.
    
   ```
   Invoke-CsDatabaseFailover -PoolFqdn <Pool FQDN> -DatabaseType <DatabaseType> -NewPrincipal "Primary"
   ```

    Repeat this cmdlet for each database type in the pool. You can use the following cmdlet to find all the database types stored in this pool.
     
   ```
   Get-CsPool -Identity <Pool FQDN>
   ```

2. Use Topology Builder to remove database mirroring from the pool.
    
   - Open Topology Builder. In your topology, expand **Enterprise Edition Front End Pools**, right-click the name of the pool, and click **Edit Properties**.
    
   - For each type of SQL store in the pool, clear the **Enable SQL Store Mirroring** check box.
    
3. Publish the changed topology. From the **Action** menu click **Topology** and then **Publish**. Then in the confirmation page click **Next**
    
4. Use SQL Server Management Studio to break the mirror.
    
   - Open SQL Server Management Studio, navigate to your databases, right-click **Tasks** and click **Mirror**. Then click **Remove Mirroring** and click **OK**.
    
   - Repeat this for all databases in the pool which will be converted to an AG.
    
5. Set up the Failover Clustering feature on all the database servers which will be part of the AG. On each server, do the following
    
   - Open Server Manager and click **Add roles and features**.
    
   - Click **Next** until you reach the **Select features** box. Here, select the **Failover Clustering** check box.
    
   - In the **Add features that are required for Failover Clustering?** box, click **Add Features**.
    
   - Click **Install**.
    
6. Validate the cluster configuration.
    
   - In Server Manager, click the **Tools** menu and then click **Failover Cluster Manager**.
    
   - Under **Actions** on the right side of the screen, click **Validate Configuration**.
    
   - On the **Before You Begin** page, click **Next**.
    
   - Select the servers to add to the cluster, and then click **Run all tests**.
    
   - In the **Summary** box, check any errors that the wizard reports. Then click **Finish** to complete the validation.
    
     The wizard will probably report several warnings, especially if you are not using shared storage. You are not required to use shared storage. However, if you see any **Error** messages, you must fix those issues before continuing.
    
7. Create the Windows Server Failover Cluster.
    
   - In the **Failover Cluster Management** wizard, right-click **Failover Cluster Management**, then click **Create Cluster**.
    
   - On the **Before You Begin** page, click **Next**.
    
   - Add the cluster name and IP address. When the settings are validated, click **Next**.
    
   - On the Confirmation page, click **Next**.
    
   - After the cluster is created, click **Finish**.
    
8. We recommend that you configure the cluster quorum settings to use a file share witness. To do so, use these steps:
    
   - Right-click the cluster name, click **More Actions**, and click **Configure Cluster Quorum Settings**.
    
   - In the **Select Quorum Configuration Option** page, click **Select the quorum witness**.
    
   - In the **Select Quorum Witness** page, click **Configure a file share witness**.
    
   - In the **Configure File Share Witness** page, type the path of the file share you want to use, and then click **Next**.
    
   - On the **Confirmation** page, click **Next**.
    
9. On each server in the cluster, enable the AG feature in SQL Server Configuration Manager.
    
   - Open SQL Server Configuration Manager. In the tree on the left side of the screen, click **SQL Server Services**, then double-click the SQL Server service. 
    
   - In the **Properties** box, select the **AlwaysOn High Availability** tab. Select the **Enable AlwaysOn Availability Groups** check box. Restart the SQL Server service when prompted.
    
10. Create the availability group.
    
    - Open SQL Server Management Studio, and connect to the SQL Server instance.
    
    - In Object Explorer, expand the **Always On High Availability** folder. Right-click the **Availability Groups** folder and click **New Availability Group Wizard**.
    
    - If the **Introduction** page appears, click **Next**.
    
    - In the **Specify Availability Group Name** page, type the name of the Availability group, and click **Next**.
    
    - In the Select Databases page, select the databases that you want to include in the AlwaysOn Availability Group. Then click **Next**.
    
    Do not include the **ReportServer**, **ReportServerTempDB**, or Persistent Chat databases in the AlwaysOn Availability Group, as these are not supported in this scenario. You can include all other Skype for Business Server databases in the AlwaysOn Availability Group.
    
    - In the **Specify Replicas** page, click the **Replicas** tab. Then click the **Add Replicas** button, and connect to the other SQL instances that you joined as nodes of the Windows Server Failover Cluster.
    
    - For each instance, select the **Automatic Failover** and **Synchronous Commit** options. Do not select the **Readable Secondary** option.
    
    - Click the **Endpoints** tab and verify that **Port Number** is set to 5022.
    
      - Click the **Listener** tab, and select the **Create an availability group listener** option. Under that option, type a name for the listener, and set the **Port** to 1433 (other ports are not supported for this option).
    
    - Click **Add**, and then in the **IPv4 Address** box, provide your preferred virtual IP address, and then click **OK**.
    
    - In the **Select Initial Data Synchronization** page, select Full, and specify a folder that is accessible to the replicas, and that the SQL Server service account used by both replicas has Write permissions for. Then click **Next**.
    
    This file share will be used temporarily when you initialize the databases. If you are dealing with large databases, we recommend that you manually initialize them in case your network bandwidth cannot accommodate the size of the database backups.
    
    - In the Validation page, verify that all validation checks are successful, then click **Next**.
    
    - In the **Summary** page, verify all settings and click Finish.
    
11. Create a new store specifying the AG listener, and specifying the principal of the old mirror as the primary node of the AG.
    
    - Open Topology Builder. In your topology, expand **Shared Components**, right-click **SQL Server Stores**, and click **New SQL Server Store**.
    
    - In the **Define New SQL Store** page, first select the **High Availability Settings** check box, and then make sure that SQL AlwaysOn Availability Groups appears in the drop-down box.
    
    - In the **SQL Server Availability Listener FQDN** box, type the FQDN of the listener you created when you created the availability group.
    
    - In the **SQL Server FQDN** box, type the FQDN of the primary node of the AG, and then click **OK**. This should be the principal of the old mirror for this store.
    
12. Associate the new AG with the Front End pool.
    
    - In Topology Builder, right-click the pool to associate with the AG, and click **Edit Properties**.
    
    - Under **Associations**, in the **SQL Server Store** box, select the AG. Select the same group for any other databases in the pool which you want to move to the AG.
    
    - When you're sure that all needed databases are set to the AG, click **OK**.
    
13. Publish the topology. From the **Action** menu click **Topology** and then **Publish**. Then in the confirmation page click **Next**.
    
14. Perform some final steps to make sure that the SQL logins are on each of the replicas in the AlwaysOn Availability Group.
    
    - Open Topology Builder, select **Download topology from existing deployment**, and click **OK**.
    
    - Expand Skype for Business Server, expand your topology, and expand **SQL Server Stores**. Right-click the SQL store of the new AG, and click **Edit Properties**.
    
    - At the bottom of the page, in the **SQL Server FQDN** box, change the value to the FQDN of the Listener of the AG.
    
    - Publish the topology. From the **Action** menu click **Topology** and then **Publish**. Then in the confirmation page click **Next**. Then wait a few minutes for the new topology to replicate.
    
    - Open SQL Server Management Studio, and navigate to the AG. Fail it over to a secondary replica.
    
    - Open Skype for Business Server Management Shell and type the following cmdlet to create the SQL logins on this replica:
    
    ```
    Install-CsDatabase -Update
    ```

    - Repeat the previous two steps (fail over the group to a secondary replica, then use  `Install-CsDatabase -Update`) for each replica in the group.
    
## Deploy an Always On Availability Group on an existing pool that does not use database mirroring
<a name="BKMK_NoHAPool_CreateAlwaysOnGroup"> </a>

> [!NOTE]
> If the pool you are upgrading to an AG hosts the Central Management store for your organization, you must first move the CMS to another pool before you upgrade this pool. Use the Move-CsManagementServer cmdlet to move the pool. If you do not have another pool in your organization, you can deploy a Standard Edition server temporarily and move the CMS to this server before you upgrade your pool to the AG. 
  
1. Set up the Failover Clustering feature on all the database servers which will be part of the AG. On each server, do the following
    
   - Open Server Manager and click **Add roles and features**.
    
   - Click **Next** until you reach the **Select features** box. Here, select the **Failover Clustering** check box.
    
   - In the **Add features that are required for Failover Clustering?** box, click **Add Features**.
    
   - Click **Install**.
    
2. Validate the cluster configuration.
    
   - In Server Manager, click the **Tools** menu and then click **Failover Cluster Manager**.
    
   - Under **Actions** on the right side of the screen, click **Validate Configuration**.
    
   - On the **Before You Begin** page, click **Next**.
    
   - Select the servers to add to the cluster, and then click **Run all tests**.
    
   - In the **Summary** box, check any errors that the wizard reports. Then click **Finish** to complete the validation.
    
     The wizard will probably report several warnings, especially if you are not using shared storage. You are not required to use shared storage. However, if you see any **Error** messages, you must fix those issues before continuing.
    
3. Create the Windows Server Failover Cluster (WSFC).
    
   - In the **Failover Cluster Management** wizard, right-click **Failover Cluster Management**, then click **Create Cluster**.
    
   - On the **Before You Begin** page, click **Next**.
    
   - Add the cluster name and IP address. When the settings are validated, click **Next**.
    
   - On the Confirmation page, click **Next**.
    
   - After the cluster is created, click **Finish**.
    
4. We recommend that you configure the cluster quorum settings to use a file share witness. To do so, use these steps:
    
   - Right-click the cluster name, click **More Actions**, and click **Configure Cluster Quorum Settings**.
    
   - In the **Select Quorum Configuration Option** page, click **Select the quorum witness**.
    
   - In the **Select Quorum Witness** page, click **Configure a file share witness**.
    
   - In the **Configure File Share Witness** page, type the path of the file share you want to use, and then click **Next**.
    
   - On the **Confirmation** page, click **Next**.
    
5. On each server in the cluster, enable AG in SQL Server Configuration Manager.
    
   - Open SQL Server Configuration Manager. In the tree on the left side of the screen, click **SQL Server Services**, then double-click the SQL Server service. 
    
   - In the **Properties** box, select the **AlwaysOn High Availability** tab. Select the **Enable AlwaysOn Availability Groups** check box. Restart the SQL Server service when prompted.
    
6. Create the availability group.
    
   - Open SQL Server Management Studio, and connect to the SQL Server instance.
    
   - In Object Explorer, expand the **Always On High Availability** folder. Right-click the **Availability Groups** folder and click **New Availability Group Wizard**.
    
   - If the **Introduction** page appears, click **Next**.
    
   - In the **Specify Availability Group Name** page, type the name of the Availability group, and click **Next**.
    
   - In the Select Databases page, select the databases that you want to include in the AG. Then click **Next**.
    
     Do not include the **ReportServer**, **ReportServerTempDB**, or Persistent Chat databases in the AG, as these are not supported in this scenario. You can include all other Skype for Business Server databases in the AG.
    
   - In the **Specify Replicas** page, click the **Replicas** tab. Then click the **Add Replicas** button, and connect to the other SQL instances that you joined as nodes of the WSFC.
    
   - For each instance, select the **Automatic Failover** and **Synchronous Commit** options. Do not select the **Readable Secondary** option.
    
   - Click the **Endpoints** tab and verify that **Port Number** is set to 5022.
    
   - Click the **Listener** tab, and select the **Create an availability group listener** option. Under that option, type a name for the listener, and set the **Port** to 1433 (other ports are not supported for this option).
    
   - Click **Add**, and then in the **IPv4 Address** box, provide your preferred virtual IP address, and then click **OK**.
    
   - In the **Select Initial Data Synchronization** page, select Full, and specify a folder that is accessible to the replicas, and that the SQL Server service account used by both replicas has Write permissions for. Then click **Next**.
    
     This file share will be used temporarily when you initialize the databases. If you are dealing with large databases, we recommend that you manually initialize them in case your network bandwidth cannot accommodate the size of the database backups.
    
     - In the Validation page, verify that all validation checks are successful, then click **Next**.
    
   - In the **Summary** page, verify all settings and click Finish.
    
7. Create a new store specifying the AG listener.
    
   - Open Topology Builder. In your topology, expand **Shared Components**, right-click **SQL Server Stores**, and click **New SQL Server Store**.
    
   - In the **Define New SQL Store** page, first select the **High Availability Settings** check box, and then make sure that SQL AlwaysOn Availability Groups appears in the drop-down box.
    
   - In the **SQL Server Availability Listener FQDN** box, type the FQDN of the listener you created when you created the availability group.
    
   - In the **SQL Server FQDN** box, type the FQDN of the primary node of the AG, and then click **OK**.
    
8. Associate the new Always On Availability Group with the Front End pool.
    
   - In Topology Builder, right-click the pool to associate with the AG, and click **Edit Properties**.
    
   - Under **Associations**, in the **SQL Server Store** box, select the AG. Select the same group for any other databases in the pool which you want to move to the AG.
    
   - When you're sure that all needed databases are set to the AG, click **OK**.
    
9. Publish the topology. From the **Action** menu click **Topology** and then **Publish**. Then in the confirmation page click **Next**.
    
10. Perform some final steps to make sure that the SQL logins are on each of the replicas in the AG.
    
    - Open Topology Builder, select **Download topology from existing deployment**, and click **OK**.
    
    - Expand Skype for Business Server, expand your topology, and expand **SQL Server Stores**. Right-click the SQL store of the new AG, and click **Edit Properties**.
    
    - At the bottom of the page, in the **SQL Server FQDN** box, change the value to the FQDN of the Listener of the AG.
    
    - Publish the topology. From the **Action** menu click **Topology** and then **Publish**. Then in the confirmation page click **Next**. Then wait a few minutes for the new topology to replicate.
    
    - Open SQL Server Management Studio, and navigate to the AG. Fail it over to a secondary replica.
    
    - Open Skype for Business Server Management Shell and type the following cmdlet to create the SQL logins on this replica:
    
      ```
      Install-CsDatabase -Update
      ```

      - Repeat the previous two steps (fail over the group to a secondary replica, then use  `Install-CsDatabase -Update`) for each replica in the group.
