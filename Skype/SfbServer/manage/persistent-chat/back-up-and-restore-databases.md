---
title: "Back up and restore Persistent Chat databases in Skype for Business Server"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 3/28/2016
audience: ITPro
ms.topic: article
ms.service: skype-for-business-server
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.assetid: 4f2b689b-7f15-48dc-a069-da7bc8527def
description: "Summary: Learn how to back up and restore Persistent Chat Server databases in Skype for Business Server."
---

# Back up and restore Persistent Chat databases in Skype for Business Server 
 
**Summary:** Learn how to back up and restore Persistent Chat Server databases in Skype for Business Server.
  
Persistent Chat Server requires SQL Server database software to store chat room data, such as history and content, configuration, user provisioning, and other relevant metadata. In addition, if your organization has regulations that require Persistent Chat activity to be archived, and the optional Compliance service is enabled, SQL Server database software is used to store compliance data, including chat content and events, such as joining and leaving rooms. Chat room content is stored in the Persistent Chat database (mgc). Compliance data is stored in the Compliance database (mgccomp). This is business-critical data that should be backed up regularly. 
  

## Back up the databases

There are two ways of backing up Persistent Chat data. 
  
- SQL Server Backup
    
- The **Export-CsPersistentChatData** cmdlet, which exports Persistent Chat data as a file
    
Data that is created by using SQL Server backup requires more disk space—possibly 20 times more—than that created by the **Export-CsPersistentChatData** cmdlet, but SQL Server backup is likely to be a procedure with which you're familiar.
  
For more information on how to use SQL Server backup procedures, see your SQL documentation.
  
If you want to use the **Export-CsPersistentChatData** cmdlet, you can specify the command as follows:
  
```PowerShell
Export-CsPersistentChatData [-FileName <String>] <COMMON PARAMETERS>
```

or
  
```PowerShell
Export-CsPersistentChatData [-AsBytes <SwitchParameter>] <COMMON PARAMETERS>
```

For example, the following command exports Persistent Chat data from the Persistent Chat database located on the server atl-sql-001.contoso.com; the exported data is stored in the file C:\Logs\PersistentChatData.zip. Because the Level parameter wasn't specified, the command does a full export of the Persistent Chat information:
  
```PowerShell
Export-CsPersistentChatData -DBInstance "atl-sql-001.contoso.com\rtc" -FileName "C:\Logs\PersistentChatData.zip"
```

## Restore the databases

How you restore your Persistent Chat data depends on the method that you used to back it up. If you used SQL Server backup procedures, you must use SQL Server restore procedures. If you used the **Export-CsPersistentChatData** cmdlet to back up Persistent Chat data, then you must use the **Import-CsPersistentChatData** cmdlet to restore the data:
  
```PowerShell
Import-CsPersistentChatData -FileName <String> <COMMON PARAMETERS>
```

or
  
```PowerShell
Import-CsPersistentChatData -ByteInput <Byte > <COMMON PARAMETERS>
```
