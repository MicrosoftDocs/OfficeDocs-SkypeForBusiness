---
title: "Configure rooms in Lync Server 2013"
ms.author: crowe
author: CarolynRowe
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8956bd2c-c863-4704-bc65-5c0d83556258
description: "Configuring Persistent Chat rooms is commonly handled by users or other central teams by using Windows PowerShell command-line interface; an administrator typically does not manage chat rooms. However, if you have to create and manage chat rooms, you can use the Windows PowerShell command-line interface, or add yourself as a member to a chat room and use the Lync 2013 client."
---

# Configure rooms in Lync Server 2013
[]
Configuring Persistent Chat rooms is commonly handled by users or other central teams by using Windows PowerShell command-line interface; an administrator typically does not manage chat rooms. However, if you have to create and manage chat rooms, you can use the Windows PowerShell command-line interface, or add yourself as a member to a chat room and use the Lync 2013 client.
  
For details about configuring chat rooms by using the Windows PowerShell command-line interface, see "Room Management" in [Configuring Persistent Chat Server by using Windows PowerShell cmdlets](configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md).
  
## Managing Data in Chat Rooms

Persistent Chat Server lets users collaborate by posting messages into Persistent Chat rooms. The data is persisted on the server, and members of the room can have access to the data, including historical data. However, users with different roles have different access to the persisted data, as outlined in the following list.
  
- Administrators can delete earlier content (for example, content that was posted before a certain date) from any chat room to keep the database from growing too large. Or, they can remove or replace messages that are considered inappropriate for a particular chat room. 
    
- End users, including message authors, cannot delete content from any chat room.
    
- Chat room managers can disable rooms, but cannot delete rooms. Only administrators can delete a chat room after it has been created.
    
When a message is deleted, you cannot undo the action. However, deleted messages can be restored if there is a backup. If a Persistent Chat Compliance server is enabled, old messages are persisted in the compliance database.
  
> [!NOTE]
> This chat room data usage applies to the Lync Server 2013, Persistent Chat Server API application, except for the case when the administrator role is involved. The Persistent Chat Server API cannot be used to do any of the administrator's operations. You must perform these operations in the Lync Server Management Shell. 
  

