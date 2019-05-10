---
title: "Install Mirror Database Option Page"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 11/17/2018
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.tb.InstallMirrorDatabaseOptionPage
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 7500896a-14ea-4b11-aaee-be3d81314536
description: "You configure Mirror Database Settings by defining the following:"
---

# Install Mirror Database Option Page
 
You configure **Mirror Database Settings** by defining the following:
  
- Type the **Path to file share** to define the location for the backup SQL Server files for the database being mirrored.
    
    > [!NOTE]
    > The primary SQL Server instance (either named instance or default instance) must have write permissions to the file share you define here. The mirror SQL Server instance (either named instance or default instance) must have read permissions to the same file share. 
  
  **OK** Accepts and commits changes to the dialog.
  
  **Cancel** Discards changes and closes the dialog.
  
  **Help** Displays this help screen.
  
## See also

[Deploy SQL mirroring for Back End Server high availability in Skype for Business Server 2015](../../deploy/deploy-high-availability-and-disaster-recovery/sql-mirroring-for-high-availability.md)
