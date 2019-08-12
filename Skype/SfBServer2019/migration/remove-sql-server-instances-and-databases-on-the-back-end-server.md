---
title: "Remove SQL Server instances and databases on the Back End Server"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
audience: ITPro
ms.topic: quickstart
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "You remove the Microsoft SQL Server databases and instances after you remove the servers running that are dependent on them, or after you reconfigure the servers to use another database. You need to perform the procedure in this topic when you retire the current SQL Server or reconfigure the current server in such a way that it renders the databases obsolete or unavailable."
---

# Remove SQL Server instances and databases on the Back End Server

You remove the Microsoft SQL Server databases and instances after you remove the servers running that are dependent on them, or after you reconfigure the servers to use another database. You need to perform the procedure in this topic when you retire the current SQL Server or reconfigure the current server in such a way that it renders the databases obsolete or unavailable.
  
To remove the databases or instances for the Archiving Server or Monitoring Server, you must first remove the server role. Similarly, to remove the instances or databases for Front End pool, you must first remove or reconfigure the dependent server role. These procedures make no distinction between collocated databases or separate instances for servers. The procedures are unaffected by the collocation of databases.
  
## In this section

- [Remove the SQL Server database for a Front End pool](remove-the-sql-server-database-for-a-front-end-pool.md)
    
- [Remove the SQL Server database for a Monitoring server](remove-the-sql-server-database-for-a-monitoring-server.md)
    
- [Remove the SQL Server database for an Archiving server](remove-the-sql-server-database-for-an-archiving-server.md)
    

