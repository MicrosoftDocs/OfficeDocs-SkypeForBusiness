---
title: "Remove-CsPersistentChatRoom"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 04cadd5d-13dc-4de5-b0b5-8c2f9bbbc7a7
description: "In this articleExamplesDetailed DescriptionInput TypesReturn Types"
---

# Remove-CsPersistentChatRoom
[]
 **In this article**
  
[Examples](#Examples)
  
[Detailed Description](#DetailedDescription)
  
[Input Types](#InputTypes)
  
[Return Types](#ReturnTypes)
  
Removes one or more Persistent Chat chat rooms. A chat room is a discussion forum that typically revolves around a specific topic. This cmdlet was introduced in Lync Server 2013.
  
```
Remove-CsPersistentChatRoom -Identity <String> <COMMON PARAMETERS>
```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 removes the Persistent Chat chat room RedmondChatRoom.
  
```
Remove-CsPersistentChatRoom -Identity "atl-gc-001.litwareinc.com\RedmondChatRoom"
```

### Example 2

In Example 2, all the Persistent Chat chat rooms in use in the organization are removed. To do this, the command first calls the **Get-CsPersistentChatRoom** cmdlet without any parameters in order to return a collection of all the available chat rooms. This collection is then piped to the **Remove-CsPersistentChatRoom** cmdlet, which deletes each room in the collection. 
  
```
Get-CsPersistentChatRoom  | Remove-CsPersistentChatRoom
```

### Example 3

Example 3 removes all the "closed" chat rooms. (A closed chat room means that any user can locate the chat room by doing a directory search, but only members can participate in chat room activities.) To accomplish this task, the command first uses the **Get-CsPersistentChatRoom** cmdlet and the Privacy parameter to return a collection of all the closed chat rooms. This collection is then piped to the **Remove-CsPersistentChatConfiguration** cmdlet, which deletes each room in the collection. 
  
```
Get-CsPersistentChatRoom -Privacy "Closed"  | Remove-CsPersistentChatRoom
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Persistent Chat service (which replaces the Group Chat service used in Microsoft Lync Server 2010) provides organizations with messaging and collaboration capabilities similar to those found in Internet discussion forums: users can exchange messages in real-time, yet can also revisit and restart those conversations at any time. Conversations can be based around specific topics, and these conversations can be made available to everyone or to only a selected set of users. Likewise, individual chat rooms can be configured so that anyone can post a message or configured so that only designated presenters can post messages.
  
Persistent Chat discussions take the form of messages posted in individual chat rooms; chat rooms are discussion forums based on specific topics. By design, messages posted in a chat room remain there forever; at any time, users can return to the room and review all the messages that have been previously posted. 
  
The **Remove-CsPersistentChatRoom** cmdlet provides a way for administrators to remove one or more of the Persistent Chat chat rooms that have been configured for use in the organization. 
  
To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt
  
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Remove-CsPersistentChatRoom"}
  
 **Lync Server Control Panel:** To delete an existing Persistent Chat chat room using the Lync Server Control Panel, click **Persistent Chat**, click **Room**, and then select the room to be deleted. To delete the room, click **Edit**, and then click **Delete**.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |System.String  <br/> |Unique Identifier for the Persistent Chat chat room being removed. The Identity for a chat room consists of the Persistent Chat pool where the room has been configured plus the name of the room; for example:  <br/> -Identity "atl-gc-001.litwareinc.com\RedmondChatRoom"  <br/> |
| _Instance_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Chat.Cmdlets.ChatRoom  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The **Remove-CsPersistentChatRooms** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.PersistentChat.Cmdlets.ChatRoomObject object. 
  
## Return Types
<a name="ReturnTypes"> </a>

None. Instead, the **Remove-CsPersistentChatRoom** cmdlet deletes existing instances of the Microsoft.Rtc.Management.PersistentChat.Cmdlets.ChatRoomObject object. 
  
## See also
<a name="ReturnTypes"> </a>

#### 

[Clear-CsPersistentChatRoom](clear-cspersistentchatroom.md)
  
[Get-CsPersistentChatRoom](get-cspersistentchatroom.md)
  
[New-CsPersistentChatRoom](new-cspersistentchatroom.md)
  
[Set-CsPersistentChatRoom](set-cspersistentchatroom.md)

