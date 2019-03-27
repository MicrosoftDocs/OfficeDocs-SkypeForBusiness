---
title: "Device Log Configuration Edit"
ms.reviewer: 
ms.author: SerdarS
author: SerdarSoysal
manager: serdars
ms.date: 11/17/2018
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.lscp.ClientDeviceUpdateEdit
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: e534e6a5-fb3e-40b1-a189-fce64c42f512
description: "You can add a device log configuration to the Edit Log Setting page that determines the maximum log cache size, maximum log file size, or length of time a log file is kept before it is purged. You can change these settings according to your organization's requirements."
---

# Device Log Configuration: Edit
 
You can add a device log configuration to the **Edit Log Setting** page that determines the maximum log cache size, maximum log file size, or length of time a log file is kept before it is purged. You can change these settings according to your organization's requirements.
  
> [!CAUTION]
> Purging files permanently removes them from the file system. After you purge a file, it cannot be recovered. 
  
## Tasks you can perform

You can perform the following tasks on the **Edit Log Setting** page:
  
- Add a device log configuration globally or for a particular site.
    
- Modify the options for an existing device log configuration.
    
## UI Reference

The following lists describe the menus, commands, fields, and properties on the page.
  
- **Scope** Identifies the scope (Global or Site) of the device log configuration.
    
- **Name** You can add or modify the name of the device log configuration.
    
- **Maximum file size (bytes)** You can specify the maximum size a log file can become before it is purged. The default is 1,024,000 bytes (1 MB).
    
- **Maximum cache size (bytes)** You can specify the maximum amount of information (in bytes) that can be held in the log file cache before that cache must be cleared and the data is written to a log file. The default is 512,000 bytes (0.5 MB).
    
- **Minutes to flush cache (1-60)** You can specify how often information stored in the log file cache is written to the actual log file. After the data is logged, the cache is cleared. The default is five minutes.
    
- **Days to keep log files (1-365)** You can specify the number of days the log files are kept before they are purged. The default is 10 days.
    
## See also

[Device Log Configuration](device-log-configuration.md)
