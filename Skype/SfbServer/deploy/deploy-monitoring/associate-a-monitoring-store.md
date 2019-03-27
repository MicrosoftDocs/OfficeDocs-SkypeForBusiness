---
title: "Associate a monitoring store with a Front End pool in Skype for Business Server"
ms.reviewer: 
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: d3a20d5e-3f24-4cff-bc9b-4f84fea30e6b
description: "Summary: Learn how to associate Front End pools with a monitoring store used by Skype for Business Server."
---

# Associate a monitoring store with a Front End pool in Skype for Business Server 
**Summary:** Learn how to associate Front End pools with a monitoring store used by Skype for Business Server.
  
In Skype for Business Server, monitoring data can only be collected on Front End pools that have been associated with a monitoring store, a task typically carried out when you define a Front End pool in Topology Builder.
  
## Associate a monitoring store with a Front End pool

 To associate a monitoring store with a new Front End pool, make sure that you select the option **Monitoring (call detail recording and logging of quality of experience metrics)** on the **Select Features** page of the Define New Front End Pool wizard. Note that, if you select this option, you must also specify a SQL store in order to complete the wizard; however, this store does not have to exist at the time you run the wizard. That means that you can first associate a pool with a monitoring store, then later setup and configure that store.
  
Alternatively, you can associate an existing Front End pool with a new or different monitoring store by completing the following procedure:
  
1. Click **Start**, click **All Programs**, click **Skype for Business Server 2015**, and then click **Skype for Business Server Topology Builder**.
    
2. In the **Topology Builder** dialog box, select **Download Topology from existing deployment** and then click **OK**.
    
3. In the **Save As** dialog box, enter a file name for your current topology and then click **Save**. The saved topology can later be retrieved and re-published in case there are problems with the new topology.
    
4. In Topology Builder, expand **Skype for Business Server**, expand the name of the site containing the Front End pool, then click expand **Enterprise Edition Front End pools**.
    
5. Right-click the name of the pool to be associated with the monitoring store and then click **Edit Properties**.
    
6. In the **Edit Properties** dialog box, on the **General** tab, select the option **Monitoring (CDR and QoE metrics)** and then select an existing SQL Server database from the **Monitoring SQL Server store** dropdown list. (Or, click **New** to associate the pool with a new database store.) If you choose to use a new database store then, in the **Define New SQL Store** dialog box, enter the fully qualified domain name of the SQL Server computer in the **Sql Server FQDN** box. If you want to use the default SQL Server instance for that store select **Default Instance**; otherwise select **Named Instance** and enter the instance name in the **Named Instance** box.
    
    The **Edit Properties** dialog box also gives you the option of creating a SQL mirror for your monitoring database (a SQL mirror enables you to maintain two copies of your monitoring database, one copy stored on the monitoring store computer and the other on the SQL mirror computer). To enable mirroring, select T **his SQL instance is in mirroring relation** and enter the port number for the mirror server in the **Mirroring port number** box.
    
7. In the **Edit Properties** dialog box, click **OK**.
    
After associating the monitoring store with a Front End pool you must publish the new topology before the changes take effect. To publish your new topology, complete the following steps in Topology Builder:
  
1. Click **Action**, point to **Topology**, and then click **Publish**.
    
2. In the Publish Topology wizard, on the **Publish the topology** page, click **Next**.
    
3. On the **Publishing wizard complete** page, click **Finish**.
    
After the topology has been published you can then install the monitoring database on the computer that will host the monitoring store. The monitoring database can be installed by using the Skype for Business Server Management Shell and Windows PowerShell. To install the database locally (that is, to install the database on the same computer where you are running the Skype for Business Server Management Shell), start the Management Shell on the appropriate computer, then type in the following command and press ENTER:
  
```
Install-CsDatabase -LocalDatabases
```

When you run the preceding command, Install-CsDatabase will read the current Skype for Business Server topology, determine which databases need to be installed on the local computer, and then automatically install and configure each of those databases.
  
To install the database on a remote computer (that is, a computer other than the computer where the Management Shell is running) you must include at least two parameters: the ConfiguredDatabases parameter and the SqlServerFqdn parameter. These parameters tell the Install-CsDatabase cmdlet to retrieve the Skype for Business Server topology and then install and configure the required databases on the computer specified by the SqlServerFqdn parameter. The SqlServerFqdn parameter must use a parameter value representing the fully qualified domain name of the computer where the databases are to be installed.
  
For example, this command installs the monitoring database on the computer atl-sql-001.litwareinc.com:
  
```
Install-CsDatabase -ConfiguredDatabases -SqlServerFqdn atl-sql-001.litwareinc.com
```

Alternatively, you can install the monitoring database by running the Skype for Business Server Deployment Wizard on the computer that will host the monitoring store. To do this, log on to the appropriate computer and complete the following procedure:
  
1. Click **Start**, click **All Programs**, click **Skype for Business Server 2015**, and then click **Skype for Business Server Deployment Wizard**.
    
2. In the Deployment Wizard, click **Install or Update Skype for Business Server System**.
    
3. On the **Deploy** page, under **Step 2: Setup or Remove Skype for Business Server Components**, click **Run Again**.
    
4. In the Setup Skype for Business Server components wizard, on the **Setup Skype for Business Server components** page, click **Next**.
    
5. On the **Specify path to MSIs** page, type the path to the file Ocscore.msi (a file included with your Skype for Business Server installation media) and then click **Next**.
    
6. On the **Executing Commands** page, click **Finish**.
    
To ensure that all the required Skype for Business Server services have started, click **Run** under the heading **Step 4: Start Services** on the **Deploy** page
  

