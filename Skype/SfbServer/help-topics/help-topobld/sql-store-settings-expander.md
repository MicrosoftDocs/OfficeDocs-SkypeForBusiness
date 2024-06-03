---
title: "SQL Store Settings Expander"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 11/17/2018
audience: ITPro
ms.topic: article
f1.keywords:
- CSH
ms.custom:
- ms.lync.tb.SqlStoreSettingsExpander
ms.service: skype-for-business-server
ms.localizationpriority: medium
ms.assetid: bd269d52-6f87-4433-b9b0-2b543fea845d
description: "To edit the properties of a SQL Server database, you must change the SQL Server database instance. You can't use the Edit Properties dialog box to perform tasks such as moving your Archiving Server database from one computer to another. In addition, you can't use the Edit Properties dialog box to change the instance of SQL Server that hosts the Central Management store."
---

# SQL Store Settings Expander
 
To edit the properties of a SQL Server database, you must change the SQL Server database instance. You can't use the **Edit Properties** dialog box to perform tasks such as moving your Archiving Server database from one computer to another. In addition, you can't use the **Edit Properties** dialog box to change the instance of SQL Server that hosts the Central Management store.
  
## Editing the Properties of a SQL Server Database

To change the instance of SQL Server that is used by any database other than the Central Management store, complete the following procedure in Topology Builder:
  
### To modify an instance of SQL Server

1. Select the appropriate database under the **SQL stores** node, and then select **Edit Properties**.
    
2. In the **Edit Properties** dialog box, do one of the following:
    
   - To use the default SQL Server instance, select **Default Instance** and then select **OK**.
    
   - To use a named database instance, select **Named Instance**, enter the instance name in the text box, and then select **OK**. You should enter only the instance name (for example, ArchivingInstance), and not the entire SQL Server path.
    
When you are working in the **Edit Properties** dialog box, Topology Builder won't verify that the database instance that you have entered is a valid instance. For example, if you inadvertently typeArchivingInstanec as the instance name and then select **OK**, Topology Builder accepts that invalid instance. Before you can publish this topology, you must correct this mistake: if a SQL Server instance can't be found, Topology Builder won't create that instance for you.
  

