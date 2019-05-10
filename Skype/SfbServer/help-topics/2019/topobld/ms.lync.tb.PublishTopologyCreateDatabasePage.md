---
title: "Create Database"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.tb.PublishTopologyCreateDatabasePage
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 4d391619-1cab-4265-ae8a-2519993705bc
ROBOTS: NOINDEX, NOFOLLOW
description: "Topology Builder provides a way to install databases on a SQL Server store. When you install databases by using Topology Builder, the application reads information from the topology and then installs the required databases on the specified SQL Server computer or SQL Server cluster. This is the only type of database installation available by using Topology Builder. If you need to install a specific database on a specific computer, or if you must install a collocated database, you must use Windows PowerShell command-line interface and the Install-CsDatabase cmdlet instead."
---

# Create Database
 
Topology Builder provides a way to install databases on a SQL Server store. When you install databases by using Topology Builder, the application reads information from the topology and then installs the required databases on the specified SQL Server computer or SQL Server cluster. This is the only type of database installation available by using Topology Builder. If you need to install a specific database on a specific computer, or if you must install a collocated database, you must use Windows PowerShell command-line interface and the [Install-CsDatabase](https://docs.microsoft.com/powershell/module/skype/install-csdatabase?view=skype-ps) cmdlet instead.
  
### Creating a Database

1. Click the Skype for Business Server node and then click **Install Database**.
    
2. In the **Install Databases** dialog box, on the **Create Database** page, select the fully qualified domain name (FQDN) of the SQL Server store where the new databases are to be created.
    
3. Click **Advanced**. In the **Select Database File Location** dialog box, select one of the following options:
    
   - **Automatically determine database file location**. If you select this option, Topology Builder uses a built-in algorithm to choose the storage location for the database logs and data files.
    
   - **Use SQL Server instance defaults**. If you select this option, the built-in algorithm is not used to choose the storage locations for the database logs and data files. Instead, log and data files are stored in the locations specified by the SQL Server defaults path (these paths must be configured in advanced by a SQL Server administrator). Data files will be stored in the default SQL Server data file location while log files will be stored in the default SQL Server log file location.
    
4. Click **OK**.
    
5. On the **Create Database** page, click **Next**.
    
6. On the **Database Creation Complete** page, click **Finish**.
    

