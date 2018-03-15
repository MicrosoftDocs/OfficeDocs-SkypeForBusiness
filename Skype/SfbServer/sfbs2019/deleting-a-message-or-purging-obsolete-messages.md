---
title: "Deleting a message or purging obsolete messages in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3f0c612d-6dfd-41a4-a5fe-5ff3448eb0ce
description: "A Persistent Chat administrator can delete a message from a Persistent Chat room (and, optionally, can replace it with another message). Administrators can also purge obsolete messages as part of ongoing maintenance, to minimize growth of the database. For example, this Windows PowerShell command removes all the messages from the ITChatRoom chat room that were posted by the user kenmyer@litwareinc.com:"
---

# Deleting a message or purging obsolete messages in Lync Server 2013
[]
A Persistent Chat administrator can delete a message from a Persistent Chat room (and, optionally, can replace it with another message). Administrators can also purge obsolete messages as part of ongoing maintenance, to minimize growth of the database. For example, this Windows PowerShell command removes all the messages from the ITChatRoom chat room that were posted by the user kenmyer@litwareinc.com:
  
```
Remove-CsPersistentChatMessage -Identity "atl-persistentchat-001.litwareinc.com\ITChatRoom" -UserUri "sip:kenmyer@litwareinc.com"
```

And this example replaces any removed messages with the note that the message is no longer available:
  
```
Remove-CsPersistentChatMessage -Identity "atl-persistentchat-001.litwareinc.com\ITChatRoom" -UserUri "sip:kenmyer@litwareinc.com" -ReplaceMessage "This message is no longer available."
```

For more information, see the help topic for the [Remove-CsPersistentChatMessage](remove-cspersistentchatmessage.md) cmdlet. 
  

