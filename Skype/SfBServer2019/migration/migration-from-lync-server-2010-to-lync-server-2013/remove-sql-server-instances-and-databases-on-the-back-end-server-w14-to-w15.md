---
title: "Remove SQL Server instances and databases on the Back End Server [W14 to W15]"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 32457df9-7dd9-4fca-9362-ea4de26b0296
description: "You remove the Microsoft SQL Server databases and instances after you remove the servers running Lync Server 2010 that are dependent on them, or after you reconfigure the servers running Lync Server 2010 to use another database. You need to perform the procedure in this topic when you retire the current SQL Server or reconfigure the current server running Lync Server 2010 in such a way that it renders the databases obsolete or unavailable."
---

# Remove SQL Server instances and databases on the Back End Server [W14 to W15]
[]
You remove the Microsoft SQL Server databases and instances after you remove the servers running Lync Server 2010 that are dependent on them, or after you reconfigure the servers running Lync Server 2010 to use another database. You need to perform the procedure in this topic when you retire the current SQL Server or reconfigure the current server running Lync Server 2010 in such a way that it renders the databases obsolete or unavailable. 
  
To remove the databases or instances for the Archiving Server or Monitoring Server, you must first remove the server role. Similarly, to remove the instances or databases for Front End pool, you must first remove or reconfigure the dependent server role. These procedures make no distinction between collocated databases or separate instances for servers. The procedures are unaffected by the collocation of databases.
  
## In this section

- [Remove the SQL Server database for a Front End pool [W14 to W15]](remove-the-sql-server-database-for-a-front-end-pool-w14-to-w15.md)
    
- [Remove the SQL Server database for a Monitoring server [W14 to W15]](remove-the-sql-server-database-for-a-monitoring-server-w14-to-w15.md)
    
- [Remove the SQL Server database for an Archiving server [W14 to W15]](remove-the-sql-server-database-for-an-archiving-server-w14-to-w15.md)
    

