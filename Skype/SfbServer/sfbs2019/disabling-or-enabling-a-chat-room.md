---
title: "Disabling or enabling a chat room in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: db0908fc-aae3-46e8-bc0b-245e9adfa1e2
description: "If the topic of a Persistent Chat room is no longer relevant, you can make the chat room unavailable to users by disabling it. When a chat room is disabled, all members are immediately disconnected from the room. After a chat room is disabled, users cannot rejoin it or find it in chat room searches."
---

# Disabling or enabling a chat room in Lync Server 2013
[]
If the topic of a Persistent Chat room is no longer relevant, you can make the chat room unavailable to users by disabling it. When a chat room is disabled, all members are immediately disconnected from the room. After a chat room is disabled, users cannot rejoin it or find it in chat room searches.
  
A disabled chat room can be enabled later by a Persistent Chat administrator. If a chat room is disabled, its membership list and other settings are preserved. If you enable the room again, you do not need to manually re-create the settings.
  
If the chat room's history persists (chat room history persistence is an optional setting on a category that applies to all rooms within the category; the default is that it is persisted, but can be turned off by setting the category's **Enable Chat History** to false), the content is preserved when the chat room is disabled. However, that content will not appear in searches during the time that the chat room remains in a disabled state. If you later enable the chat room, users can search for messages that were posted before the chat room was disabled. 
  
For details about disabling and enabling chat rooms by using the Windows PowerShell command-line interface, see "Room Management" in [Configuring Persistent Chat Server by using Windows PowerShell cmdlets](configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md). To disable a chat room, use a command similar to this:
  
```
Set-CsPersistentChatRoom -Identity "atl-cs-001.litwareinc.com\ITChatRoom" -Disabled $True
```

To enabled a chat room, set the Disabled property to False:
  
```
Set-CsPersistentChatRoom -Identity "atl-cs-001.litwareinc.com\ITChatRoom" -Disabled $False

```

Note that chat rooms cannot be enabled or disabled by using the Lync Server Control Panel.
  
For details about configuring chat rooms, see [Configure rooms in Lync Server 2013](configure-rooms.md) in the Deployment documentation. 
  

