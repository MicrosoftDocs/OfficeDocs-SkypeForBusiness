---
title: "Add archiving databases to an existing deployment in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 3b67df85-181d-45ca-ba48-bb74a439f242
description: "Summary: Read this topic to learn how to add archiving databases to your Skype for Business Server deployment."
---

# Add archiving databases to an existing deployment in Skype for Business Server
 
**Summary:** Read this topic to learn how to add archiving databases to your Skype for Business Server deployment.
  
You must incorporate archiving into your topology before you can configure your deployment to support archiving. The information in this topic explains how to use Topology Builder to:
  
- Add an archiving database to your topology.
    
- Publish the updated topology to add the archiving database to your Skype for Business Server deployment.
    
> [!NOTE]
> If you want to use Microsoft Exchange integration to store archiving data and files on Exchange servers for all your users in your deployment, do not specify **Archiving SQL Server store** or **Use SQL Server Store mirroring** information.
  
### Add an archiving database to your topology

1. On a computer that is running Skype for Business Server, or on which the Skype for Business Server administrative tools are installed, log on by using an account that is a member of the local Users group (or an account with equivalent user rights).
    
2. Start Topology Builder.
    
3. In the console tree, navigate to the Front End pool in which you want to deploy Archiving, and then click the name of the Front End pool where you want to deploy archiving.
    
4. In the **Action** menu, click **Edit Properties**. 
    
5. In the **Edit Properties** dialog box, click **General**.
    
6. Scroll down to **Archiving**.
    
7. Select the **Archiving** check box.
    
8. Under **Archiving SQL Server store,** do one of the following:
    
   - To use an existing SQL Server store, in the drop-down list box, click the name of the SQL Server store that you want to use. If all of your users are homed on Microsoft Exchange Server 2013 or above, you can archive Skype for Business communications for all your users in Exchange. In this case, you don't need to configure SQL Server Archiving store.
    
   - To specify a new SQL Server store, click **New**, and then in the **Define New SQL Server Store** dialog box, do the following:
    
   - In **SQL Server FQDN**, specify the FQDN of the server on which you want to create the new SQL Server store.
    
   - Either click **Default Instance** to use the default instance, or, to specify a different instance, click **Named instance**, and then specify the instance you want to use.
    
   - If the specified SQL Server instance is in a mirroring relationship, select the **This SQL instance is in mirroring relation** check box, and then, in **Mirror port number**, specify the port number.
    
9. If you want to use SQL Server store mirroring, select **Enable SQL Server Store mirroring**, and then do the following:
    
   - To use an existing SQL Server store for mirroring, in the **Archiving SQL Server store mirror** drop-down list box, click the name of the SQL Server store that you want to use for mirroring.
    
   - To specify a new SQL Server store for mirroring, click **New**, and then in the **Define New SQL Server Store** dialog box, do one of the following:
    
     a. In **SQL Server FQDN**, specify the FQDN of the SQL Server on which you want to create the new SQL Server store.
    
     b. Either click **Default Instance** to use the default instance, or, to specify a different instance, click **Named Instance**, and then specify the instance you want to use.
    
     c. If the specified SQL Server instance is in a mirroring relationship, select the **This SQL instance is in mirroring relation** check box, and then, in **Mirror port number**, specify the port number.
    
   - If you enable SQL Server mirroring and want to include a SQL Server mirroring witness (a third, separate SQL Server instance that can detect the health of the primary SQL Server and mirror instances), select the **Use SQL Server mirroring witness to enable automatic failover** check box, and then do one of the following:
    
     a. In **SQL Server FQDN**, specify the FQDN of the server on which you want to create the new SQL Server mirroring witness.
    
     b. Either click **Default Instance** to use the default instance, or, to specify a different instance, click **Named Instance**, and then specify the instance you want to use for the mirroring witness.
    
     c. If the specified SQL Server instance is in a mirroring relationship, select the **This SQL instance is in mirroring relation** check box, and then, in **Mirror port number**, specify the port number.
    
10. To save the configuration, click **OK**.
    
### Publish the updated topology to add an archiving database to your deployment

1. On a computer that is running Skype for Business Server, or on which the Skype for Business Server administrative tools are installed, log on using an account that is a member of the local Users group (or an account with equivalent user rights).
    
    > [!NOTE]
    > You can define a topology by using an account that is a member of the local Users group, but to publish a topology, which is required to add a server to the topology, you must use an account that is a member of the **Domain Admins** group and the **RTCUniversalServerAdmins** group, and that has full control permissions (read, write, and modify) on the file share that you are using for the Skype for Business Server file store (so that Topology Builder can configure the required discretionary access control list (DACLs), or an account with equivalent rights.
  
2. Open the topology you created in the previous section using Topology Builder.
    
3. In the console tree, right-click **Skype for Business Server**, and then click **Publish Topology**.
    
4. On the **Publish the topology** page, click **Next**.
    
5. On the **Create databases** page, verify that the database is selected, and then click **Next**. 
    
    > [!NOTE]
    > If you do not have the appropriate permissions to create databases, you can cancel the selection of the database and someone with appropriate permissions can create the database. > Only databases on dedicated SQL Servers can be installed by using Topology Builder. Databases on SQL Servers that are collocated with other server components must be installed by running local setup on that computer. 
  
6. On the **Publishing wizard complete** page, verify that the topology was successfully published, and then click **Finish**.
    
    > [!IMPORTANT]
    > After publishing the topology, you must configure options and policies for Archiving before any content can be archived. For details, see [Configure archiving options for Skype for Business Server](configure-archiving-options.md) and [Configure archiving policies for Skype for Business Server](configure-archiving-policies.md). 
  

