---
title: "Install Mirror Database Option Page"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
f1_keywords:
- ms.lync.tb.InstallMirrorDatabaseOptionPage
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 7500896a-14ea-4b11-aaee-be3d81314536
description: "You configure Mirror Database Settings by defining the following:"
---

# Install Mirror Database Option Page
[]
You configure **Mirror Database Settings** by defining the following: 
  
- Type the **Path to file share** to define the location for the backup SQL Server files for the database being mirrored. 
    
    > [!NOTE]
    > The primary SQL Server instance (either named instance or default instance) must have write permissions to the file share you define here. The mirror SQL Server instance (either named instance or default instance) must have read permissions to the same file share. 
  
![Set path in Mirror Database Settings dialog box](media/Install_Mirror_Database_Option_Page.jpg)
  
 **OK** Accepts and commits changes to the dialog. 
  
 **Cancel** Discards changes and closes the dialog. 
  
 **Help** Displays this help screen. 
  
## See also

#### 

[Deploying SQL mirroring for Back End Server high availability in Lync Server 2013](deploying-sql-mirroring-for-back-end-server-high-availability.md)

