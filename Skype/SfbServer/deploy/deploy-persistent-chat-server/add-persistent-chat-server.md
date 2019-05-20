---
title: "Add Persistent Chat Server to your Skype for Business Server 2015 topology"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/28/2016
audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 6b4f4d69-3c9d-4bc7-bc9b-46427a095de2
description: "Summary: Read this topic to learn how to add Persistent Chat Server to your Skype for Business Server 2015 topology."
---

# Add Persistent Chat Server to your Skype for Business Server 2015 topology
 
**Summary:** Read this topic to learn how to add Persistent Chat Server to your Skype for Business Server 2015 topology.
  
After you install the prerequisite software on each server on which you plan to deploy Persistent Chat Server, you use Topology Builder to: 
  
- Update your topology to include Persistent Chat Server
    
- Publish the updated topology
    
> [!NOTE] 
> Persistent chat is available in Skype for Business Server 2015 but is no longer supported in Skype for Business Server 2019. The same functionality is available in Teams. For more information, see [Journey from Skype for Business to Microsoft Teams](/microsoftteams/journey-skypeforbusiness-teams). If you need to use Persistent chat, your choices are to either migrate users requiring this functionality to Teams, or to continue using Skype for Business Server 2015. 

## Update your topology to include Persistent Chat Server

Perform the following steps for installing a single Persistent Chat Server pool without a disaster recovery configuration. For configuring a stretched Persistent Chat Server pool for high availability and disaster recovery, see [Configure high availability and disaster recovery for Persistent Chat Server in Skype for Business Server 2015](../../deploy/deploy-high-availability-and-disaster-recovery/configure-hadr-for-persistent-chat.md).
  
To deploy multiple Persistent Chat Server pools, repeat the same process for each pool.
  
1. On a computer that is running Skype for Business Server or on which the Skype for Business Server administrative tools are installed, log on using an account that is a member of the local Users group (or an account with equivalent user rights).
    
    > [!NOTE]
    > You can define a topology by using an account that is a member of the local Users group, but to publish a topology, which is required to install Skype for Business Server, you must use an account that is a member of the **Domain Admins** group and the **RTCUniversalServerAdmins** group, and that has full control permissions (read, write, and modify) on the file store that you are going to use for the Persistent Chat Server file store (so that Topology Builder can configure the required DACLs), or an account with equivalent rights.
  
2. Start Topology Builder.
    
3. In the console tree, navigate to the **Persistent Chat Pools** node and expand it to select a Skype for Business Server pool, or right-click the node and select **New Persistent Chat Pool**. You must define the pool's fully qualified domain name (FQDN), and indicate whether the pool will be a single-server pool or multiple-server pool deployment.
    
    You can choose a **Multiple Computer Pool** or a **Single Computer Pool**. Choose the former if you are planning to have more than one Front End Server in your Persistent Chat Server pool. Make this choice now, or at a later point, because after you create a single computer pool, you cannot add additional servers to it later. If you choose a multiple computer pool, enter the names of the individual Front End Servers that comprise the pool.
    
    > [!IMPORTANT]
    > If the Persistent Chat Server role is being installed on a Standard Edition server, the FQDN needs to match the FQDN of the Standard Edition server. 
  
4. Define a simple **Display Name** for the Persistent Chat Server pool. The display name can be used by custom clients, particularly when there are multiple Persistent Chat Server pools to differentiate rooms.
    
5. Define the port used by the Persistent Chat Server to communicate with Skype for Business Server Front End Servers. The default port is 5041.
    
6. If your organization requires compliance support, select the **Enable compliance** check box. If chosen, the Persistent Chat Server Compliance service is installed on the same computer as the Persistent Chat Server Front End Server. You are prompted to select a SQL Server Back End Server for Persistent Chat Server Compliance later.
    
7. Assign site affinity for the Persistent Chat Server pool. Select the **Use this pool as default for site \<SiteName\>** check box or **Use this pool as default for all sites** to designate this Persistent Chat Server pool as the default pool for the current site or all sites. When the Skype for Business client is used to create and manage rooms, the default pool associated with the user's site is used by the room creation and management experience so that it can route room creation and management operations to that pool. This only applies when you have multiple Persistent Chat Server pools deployed, and want to use the room creation and management features of Persistent Chat Server.
    
    > [!IMPORTANT]
    > You can customize the room creation and management features using the Persistent Chat Server Software Development Kit (SDK). 
  
8. Define the **SQL store for the Persistent Chat Server Back End (where chat room content is stored)** by doing one of the following:
    
   - To use an existing SQL Server store, in the drop-down list, click the name of the SQL Server store that you want to use.
    
   - To specify a new SQL Server database, click **New**, and in **Define New SQL Store**, perform the following:
    
   - In **SQL Server FQDN**, specify the FQDN of the SQL Server on which you want to create the new SQL Server database.
    
   - Either select **Default Instance** to use the default instance or, to specify a different instance, select **Named Instance**, and specify the instance that you want to use.
    
     > [!NOTE]
     > For details about how to configure SQL Server backup databases for disaster recovery, see [Configure high availability and disaster recovery for Persistent Chat Server in Skype for Business Server 2015](../../deploy/deploy-high-availability-and-disaster-recovery/configure-hadr-for-persistent-chat.md). 
  
9. Define the SQL Server compliance store if you enabled Compliance.
    
    > [!IMPORTANT]
    > For details about how to configure SQL Server mirrors for high availability for the Persistent Chat Server database and the Persistent Chat Server compliance database, see [Configure high availability and disaster recovery for Persistent Chat Server in Skype for Business Server 2015](../../deploy/deploy-high-availability-and-disaster-recovery/configure-hadr-for-persistent-chat.md). 
  
10. Define the file store. A file store is a folder where a copy of any file uploaded to the file repository is stored (for example, storing file attachments posted to a chat room). In the case of a multiple-server Persistent Chat Server topology, this must be a Universal Naming Convention (UNC) path; and for a single-server Persistent Chat Server topology, it can be a local file path.
    
    To use an existing file store, perform the following steps:
    
    - In **File Server FQDN**, specify the FQDN of the machine on which you want to create the new file store.
    
    - In **File Share**, specify the file store that you want to use.
    
      > [!IMPORTANT]
      > You can define the file store in Topology Builder before you create the file store, but you must create the file store in the defined location you define before you publish the topology. If the file store doesn't already exist, attempts to publish the topology will fail. 
  
11. Select the Front End Server pool to be used as a next hop for this Persistent Chat Server pool. This is the Front End Server pool that will be able to route Persistent Chat Server requests to this pool.
    
12. To save the configuration, click **Finish**. The Persistent Chat Server pool appears in Topology Builder accompanied by your specific pool settings.
    
    To publish your updated topology to which you've added Persistent Chat Server, see Publish the updated topology.
    
    > [!NOTE]
    > With Topology Builder already open, you can proceed to step 3 in Publish the updated topology to begin publishing your updated topology. 
  
## Publish the updated topology
<a name="BKMK_PublishTopology"> </a>

After updating your topology in Topology Builder, you must publish the topology to the Central Management store before you can configure and use Skype for Business Server. Read-only copies of the data are replicated to all servers in the topology to keep all servers in sync with topology and other configuration changes.
  
Before you publish your topology, install the databases for Persistent Chat Server. Use Topology Builder to install databases by selecting **Action** and **Install Database**.
  
1. On a computer that is running Skype for Business Server or on which the Skype for Business Server administrative tools are installed, log on using an account that is a member of both the **Domain Admins** group and the **RTCUniversalServerAdmins** group, and that has full control permissions (read, write, and modify) on the file store to be used for the Persistent Chat Server file store (so that Topology Builder can configure the required discretionary access control lists (DACLs)), or an account with equivalent user rights.
    
2. Start Topology Builder. Select **Open Topology from a local file** if you saved it locally.
    
3. In the console tree, right-click **Skype for Business Server 2015**, and then click **Publish Topology**.
    
4. On the **Publish the topology** page, click **Next**.
    
5. On the **Publishing wizard complete** page, verify that the topology was successfully published, and then click **Finish**.
    

