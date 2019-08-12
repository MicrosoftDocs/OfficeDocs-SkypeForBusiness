---
title: "SQL Store Settings Expander"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.tb.SqlStoreSettingsExpander
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: bd269d52-6f87-4433-b9b0-2b543fea845d
ROBOTS: NOINDEX, NOFOLLOW
description: "To edit the properties of a SQL Server database, you must change the SQL Server database instance. You cannot use the Edit Properties dialog box to perform tasks such as moving your Archiving Server database from one computer to another. In addition, you cannot use the Edit Properties dialog box to change the instance of SQL Server that hosts the Central Management store."
---

# SQL Store Settings Expander
 
To edit the properties of a SQL Server database, you must change the SQL Server database instance. You cannot use the **Edit Properties** dialog box to perform tasks such as moving your Archiving Server database from one computer to another. In addition, you cannot use the **Edit Properties** dialog box to change the instance of SQL Server that hosts the Central Management store.
  
## Editing the Properties of a SQL Server Database

To change the instance of SQL Server that is used by any database other than the Central Management store, complete the following procedure in Topology Builder:
  
### To modify an instance of SQL Server

1. Select the appropriate database under the **SQL stores** node, and then click **Edit Properties**.
    
2. In the **Edit Properties** dialog box, do one of the following:
    
   - To use the default SQL Server instance, select **Default Instance** and then click **OK**.
    
   - To use a named database instance, select **Named Instance**, enter the instance name in the text box, and then click **OK**. You should enter only the instance name (for example, ArchivingInstance), and not the entire SQL Server path.
    
When you are working in the **Edit Properties** dialog box, Topology Builder will not verify that the database instance that you have entered is a valid instance. For example, if you inadvertently typeArchivingInstanec as the instance name and then click **OK**, Topology Builder will accept that invalid instance. Before you can publish this topology, you must correct this mistake: if a SQL Server instance cannot be found, Topology Builder will not create that instance for you.
  

