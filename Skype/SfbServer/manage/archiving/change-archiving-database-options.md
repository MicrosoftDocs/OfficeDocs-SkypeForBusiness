---
title: "Change Archiving database options in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: dbebaa0a-f3a2-4dbd-b64e-07a62370f899
description: "Summary: Learn how to change archiving database options for Skype for Business Server."
---

# Change Archiving database options in Skype for Business Server

**Summary:** Learn how to change archiving database options for Skype for Business Server.
  
If you deploy archiving using SQL Server storage for archiving storage for any of your users, you can make the following database storage changes:
  
- Use a different SQL Server database for archiving storage. This includes the primary Archiving database and any database you use for SQL Server mirroring.
    
- Switch to Microsoft Exchange integration to store archiving data and files on Exchange servers. If all your users are homed on your Exchange servers and you want to use Microsoft Exchange storage for all users in your deployment, you should remove the SQL Server store databases from your topology. 
    
To make either of these changes, you must run Topology Builder, make the changes, and then publish the topology again. Do not specify **Archiving SQL Server store** or **Enable SQL Server store mirroring** information, unless you have Skype for Business users who are not homed on Exchange servers.
  
## Change Archiving database options

1. On a computer that is running Skype for Business Server, or on which the Skype for Business Server administrative tools are installed, log on by using an account that is a member of the local Users group (or an account with equivalent user rights).
    
    > [!NOTE]
    > You can define a topology by using an account that is a member of the local Users group, but to publish a topology, which is required to add a component to the topology, you must use an account that is a member of the **Domain Admins** group and the **RTCUniversalServerAdmins** group, and that has full control permissions (that is, read, write, and modify) on the file share that you are using for the Skype for Business Server file store (that is, so that Topology Builder can configure the required discretionary access control lists (DACLs), or an account with equivalent rights.
  
2. Start Topology Builder.
    
3. In the console tree, navigate to the Front End pool in which you deployed Archiving, and then click the name of the Front End pool where you want to change the database options.
    
4. In the **Action** menu, click **Edit Properties**. 
    
5. In the **Edit Properties** dialog box, click **General**.
    
6. Scroll down to **Archiving**.
    
7. In **Archiving**, do the following:
    
   - To change to a different existing SQL Server store, under **Archiving SQL Server store**, in the drop-down list box, do the following:
    
   - To use an existing SQL Server store, in the drop-down list box, click the name of the SQL Server store that you want to use.
    
   - To specify a new SQL Server store, click **New**, and then in the **Define New SQL Server store** dialog box, do the following:
    
     - To use an existing SQL Server store, in the drop-down list box, click the name of the SQL Server store that you want to use.
    
     - To specify a new SQL Server store, click **New**, and then in the **Define New SQL Server Store** dialog box, do the following:
    
       - In **SQL Server FQDN**, specify the FQDN of the server on which you want to create the new SQL Server store.
    
       - Either click **Default Instance** to use the default instance, or, to specify a different instance, click **Named instance**, and then specify the instance you want to use.
    
       - If the specified SQL Server instance is in a mirroring relationship, select the **This SQL instance is in mirroring relation** check box, and then, in **Mirror port number**, specify the port number.
    
   - To add SQL Server store for mirroring or change to a different existing SQL Server store for SQL Server store mirroring, select **Enable SQL Server store mirroring**, and then do the following:
    
     - To use an existing SQL Server store for mirroring, in the **Archiving SQL Server store mirror** drop-down list box, click the name of the SQL Server store that you want to use for mirroring.
    
     - To specify a new SQL Server store for mirroring, click **New**, and then in the **Define New SQL Server Store** dialog box, do one of the following:
    
       a. In **SQL Server FQDN**, specify the FQDN of the SQL Server on which you want to create the new SQL Server store.
    
       b. Either click **Default Instance** to use the default instance, or, to specify a different instance, click **Named Instance**, and then specify the instance you want to use.
    
       c. If the specified SQL Server instance is in a mirroring relationship, select the **This SQL instance is in mirroring relation** check box, and then, in **Mirror port number**, specify the port number.
    
   - If you enable SQL Server mirroring and want to add or change a SQL Server mirroring witness (a third, separate SQL Server instance that can detect the health of the primary SQL Server server and mirror instances), select the **Use SQL Server mirroring witness to enable automatic failover** check box, and then do one of the following:
    
      a. In **SQL Server FQDN**, specify the FQDN of the server on which you want to create the new SQL Server mirroring witness.
    
      b. Either click **Default Instance** to use the default instance, or, to specify a different instance, click **Named Instance**, and then specify the instance you want to use for the mirroring witness.
    
      c. If the specified SQL Server instance is in a mirroring relationship, select the **This SQL instance is in mirroring relation** check box, and then, in **Mirror port number**, specify the port number.
    
   - To switch to Microsoft Exchange integration to store archiving data and files on Exchange servers (if all users in your deployment are homed on your Exchange servers), delete all information for Archiving databases.
    
     > [!IMPORTANT]
     > If you have any Skype for Business users who are not homed on Exchange servers, do not delete the SQL Server store information. 
  
8. To save the configuration, click **OK**.
    
    > [!IMPORTANT]
    > The changes you make in Topology Builder do not take effect until you publish the new topology. For details, see [Add archiving databases to an existing deployment in Skype for Business Server](../../deploy/deploy-archiving/add-archiving-databases.md). 
  
## Change the location of the Archiving database by using Windows PowerShell

In most cases, you will not need to change the location of the Archiving database, which is specified when you install Archiving Server. However, if a hardware failure or other problem should occur, you can point Archiving Server to a new database by using the **Set-CsArchivingServer** cmdlet.
  
The following example changes the location of the Archiving database for the ArchivingServer:atl-cs-001.contoso.com Archiving Server. In this example, the new database is located at ArchivingDatabase:atl-sql-001.contoso.com:
  
```
Set-CsArchivingServer -Identity "ArchivingServer:atl-cs-001.contoso.com" -ArchivingDatabase "ArchivingDatabase:atl-sql-001.contoso.com"
```


