---
title: "Publish the topology in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3b5a744b-b3a8-4538-a55e-e2e4f72dff47
description: "To successfully publish, enable, or disable a topology when adding or removing a server role, you should be logged in as a user who is a member of the RTCUniversalServerAdmins and Domain Admins groups. It is also possible to delegate the proper administrator rights and permissions. For details, see Delegate setup permissions in Lync Server 2013. For other configuration changes, only membership in the RTCUniversalServerAdmins group is required."
---

# Publish the topology in Lync Server 2013
[]
To successfully publish, enable, or disable a topology when adding or removing a server role, you should be logged in as a user who is a member of the RTCUniversalServerAdmins and Domain Admins groups. It is also possible to delegate the proper administrator rights and permissions. For details, see [Delegate setup permissions in Lync Server 2013](delegate-setup-permissions.md). For other configuration changes, only membership in the RTCUniversalServerAdmins group is required.
  
After you define your topology in Topology Builder, you must publish the topology to the Central Management store. The Central Management store provides a robust, schematized storage of the data needed to define, set up, maintain, administer, describe, and operate a Lync Server 2013 deployment. It also validates the data to help ensure configuration consistency. All changes to this configuration data happen at the Central Management store, eliminating "out-of-sync" issues. Read-only copies of the data are replicated to all servers in the topology, including Edge Servers.
  
> [!NOTE]
> SQL Server needs a minimum of 20 GB of free disk space to successfully publish the initial topology and create the Central Management Server. 
  
> [!NOTE]
> For Enterprise Edition only: In order to publish the topology, the SQL Server-based Back End Server must be online and accessible with firewall exceptions in place. For details about specifying firewall exceptions, see [Understanding firewall requirements for SQL Server with Lync Server 2013](understanding-firewall-requirements-for-sql-server.md). For details about configuring SQL Server, see [Configure SQL Server for Lync Server 2013](configure-sql-server-for-lync-server-2013.md). 
  
### To publish a topology

1. Start Topology Builder: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Topology Builder**.
    
2. Select to open the topology from a local file. If you are on the computer where you defined the topology, this will be in the location where you saved it in earlier steps. Typically, this will be the Documents folder of the user who configured the topology.
    
3. Right-click the **Lync Server 2013** node, and then click **Publish Topology**.
    
4. On the **Publish the topology** page, click **Next**.
    
5. On the **Create databases** page, select the databases you want to publish. 
    
    > [!NOTE]
    > If you don't have the appropriate rights to create the databases, you can clear the check boxes next to those databases, and someone with appropriate rights can later create the databases. For details, see [Deployment permissions for SQL Server in Lync Server 2013](deployment-permissions-for-sql-server.md). 
  
6. Optionally click **Advanced**. The Advanced SQL Server data file placement options let you select between the following options: 
    
  - **Automatically determine database file location** - This option will determine the best operational performance based on the disk configuration on your SQL Server-based server by distributing the log and data files to the best location. 
    
  - **Use SQL Server instance defaults** - This option puts log and data files onto the SQL Server-based server by using the instance settings. This option does not use the operational functionality of the SQL Server-based server to determine optimal locations for logs and data. The SQL Server administrator would typically move the log and data files to locations that are appropriate for the SQL Server-based server and organization management procedures. 
    
    Click **OK**, and then click **Next**. 
    
7. On the **Select Central Management Server** page, select a Front End pool. 
    
8. Optionally click **Advanced**. The Advanced SQL Server data file placement options enables you to select between the following options: 
    
  - **Automatically determine database file location** - This option will determine the best operational performance based on the disk configuration on your SQL Server-based server by distributing the log and data files to the best location. 
    
  - **Use SQL Server instance defaults** - This option puts log and data files onto the SQL Server-based server by using the instance settings. This option does not use the operational functionality of the SQL Server-based server to determine optimal locations for logs and data. The SQL Server administrator would typically move the log and data files to locations that are appropriate for the SQL Server-based server and organization management procedures. 
    
    Click **OK**.
    
9. Click **Next** to complete the publishing process. 
    
10. When the publish process has completed, click **Finish**. 
    
    When the topology has been published successfully, you can begin installing a local replica of the Central Management store on each server running Lync Server 2013 in your topology. We recommend that you begin with the first Front End pool. 
    
## See also

#### 

[Setting up Front End Servers and Front End pools for Lync Server 2013](setting-up-front-end-servers-and-front-end-pools.md)

