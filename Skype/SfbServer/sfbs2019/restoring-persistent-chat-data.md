---
title: "Restoring Persistent Chat data in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c251a7fa-50da-434b-b39a-17f5978ce736
description: "Persistent Chat room content is stored in the Persistent Chat database (mgc.mdf). This is business-critical data that should be backed up regularly. In addition to the chat room content, principals (such as users and groups) and the roles and access that they have to chat rooms and chat room content, is also stored in the Persistent Chat database."
---

# Restoring Persistent Chat data in Lync Server 2013
[]
Persistent Chat room content is stored in the Persistent Chat database (mgc.mdf). This is business-critical data that should be backed up regularly. In addition to the chat room content, principals (such as users and groups) and the roles and access that they have to chat rooms and chat room content, is also stored in the Persistent Chat database.
  
How you restore your Persistent Chat data depends on the method that you used to back it up.
  
- If you used SQL Server backup procedures, you must use SQL Server restore procedures.
    
- If you used the **Export-CsPersistentChatData** cmdlet to back up Persistent Chat data, then you must use the **Import-CsPersistentChatData** cmdlet to restore the data. 
    

