---
title: "Remove the SQL Server database for a Monitoring server"
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "After you remove a Monitoring Server, you can remove the SQL Server databases that hosted the server data. Use the following procedures to remove the definitions from Topology Builder, and then remove the database and log files from the database server."
---

# Remove the SQL Server database for a Monitoring server

After you remove a Monitoring Server, you can remove the SQL Server databases that hosted the server data. Use the following procedures to remove the definitions from Topology Builder, and then remove the database and log files from the database server.
  
## To remove the SQL Server database using Topology Builder

1. On the Skype for Business Server 2019 Front End Server, open Topology Builder.
    
2. In Topology Builder, navigate to **Shared Components** and then **SQL Server Stores**, right-click the SQL Server instance associated with the removed or reconfigured Monitoring Server, and then click **Delete**.
    
3. Publish the topology, and then check replication status.
    
## To remove the database files from the SQL Server

1. To remove the databases on the SQL Server-based server, you must be a member of the SQL Server sysadmins group for the SQL Server server where you are removing the database files.
    
2. Open the Skype for Business Server Management Shell.
    
3. At the command line, type the following:
    
   ```
   Uninstall-CsDataBase -DatabaseType Monitoring -SqlServerFqdn <FQDN> [-SqlInstanceName <instance>]
   ```

    Where  _\<FQDN\>_ is the fully qualified domain name (FQDN) of the database server, and  _\<instance\>_ is the optional named database instance. 
    
4. When the **Uninstall-CsDataBase** cmdlet prompts you to confirm actions, read the information, and then press Y (or Enter) to proceed, or press N and then Enter if you want to stop the cmdlet (if there are errors). 
    

