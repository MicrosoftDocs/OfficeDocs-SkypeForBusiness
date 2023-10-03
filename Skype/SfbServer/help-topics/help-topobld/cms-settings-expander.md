---
title: "CMS Settings Expander"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 3/25/2015
audience: ITPro
ms.topic: article
f1.keywords:
- CSH
ms.custom:
- ms.lync.tb.CmsSettingsExpander
ms.service: skype-for-business-server
ms.localizationpriority: medium
ms.assetid: 4b882923-ed6f-44f3-ad9c-aabad5a3bc00
description: "The Central Management Server can be changed from one defined Front End pool to another defined Front End pool. To change the location of the Central Management Server, select the Front End pool from the drop-down list under Front End server to install Central Management Server on. A Front End Server can be an Enterprise Edition Front End pool or a Standard Edition Front End Server."
---

# CMS Settings Expander
 
The Central Management Server can be changed from one defined Front End pool to another defined Front End pool. To change the location of the Central Management Server, select the Front End pool from the drop-down list under **Front End server to install Central Management Server on**. A Front End Server can be an Enterprise Edition Front End pool or a Standard Edition Front End Server.
  
> [!IMPORTANT]
> If you have defined, published, and deployed the Central Management store for the infrastructure, you cannot change the location of the Central Management store without relocating the Central Management store to another Front End by an external process. 
  
For details about moving the Central Management Server store, see [Move-CsManagementServer](/powershell/module/skype/move-csmanagementserver?view=skype-ps) in the Windows PowerShell cmdlet reference.
