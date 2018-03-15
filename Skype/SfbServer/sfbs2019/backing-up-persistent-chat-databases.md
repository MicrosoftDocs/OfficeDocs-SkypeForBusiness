---
title: "Backing up Persistent Chat databases in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b99ebdc0-a025-44d7-9d74-37a7365f330d
description: "Persistent Chat room content is stored in the Persistent Chat database (Mgc.mdf). This is business-critical data that should be backed up regularly. In addition to the chat room content, the Persistent Chat database also stores information about the principals (such as users and user groups), and the roles and access that they have to chat rooms and chat room."
---

# Backing up Persistent Chat databases in Lync Server 2013
[]
Persistent Chat room content is stored in the Persistent Chat database (Mgc.mdf). This is business-critical data that should be backed up regularly. In addition to the chat room content, the Persistent Chat database also stores information about the principals (such as users and user groups), and the roles and access that they have to chat rooms and chat room. 
  
There are two ways of backing up Persistent Chat data. 
  
- SQL Server Backup
    
- The  `Export-CsPersistentChatData` cmdlet, which exports Persistent Chat data as a file 
    
Data that is created by using SQL Server backup requires significantly more disk space—possibly 20 times more—than that created by  `Export-CsPersistentChatData`, but SQL Server backup is more likely to be a procedure that administrators are familiar with.
  

