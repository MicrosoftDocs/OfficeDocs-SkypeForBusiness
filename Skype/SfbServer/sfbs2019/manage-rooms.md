---
title: "Manage rooms"
ms.author: crowe
author: CarolynRowe
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d4835cf4-cd09-4769-a08e-e92706861b64
description: "To create a new Persistent Chat Server room"
---

# Manage rooms
[]
To create a new Persistent Chat Server room
  
```
New-CsPersistentChatRoom -Name Foo1 -PersistentChatPoolFqdn client.contoso.com -Category client.contoso.com\Foo [other parameters]
```

> [!IMPORTANT]
>  -PersistentChatPoolFqdn is not needed if one of the following is true: >  There is only one Persistent Chat Server pool. >  You provide a pool FQDN to the category. >  You provide a pool FQDN to adding the room. 
  
To make changes to an existing Persistent Chat Server room
  
```
Set-CsPersistentChatRoom -Identity testCat -Members @{Add="sip:user1@contoso.com", "CN=container,DC=contoso,DC=com"}
Set-CsPersistentChatRoom -Identity testCat -Managers @{Add="sip:user2@contoso.com"}
Set-CsPersistentChatRoom -Identity testCat -Presenters @{Add="sip:user1@contoso.com"}
```

Windows PowerShell: Members, Managers and Presenters can be set simultaneously. They all should be the subset of AllowedMembers minus DeniedMembers of the host Category. A room that is type=normal cannot include Presenters.
  
## Create, Get, Set, Clear, or Remove a Room

To create a new room
  
```
New-CsPersistentChatRoom -Name <String> [-PersistentChatPoolFqdn <String>]-Category <String> [-Description <String>] [-Disabled <Switch Parameter>] [-Type <Normal | Auditorium>] [-AddIn <String>] [-Privacy <ChatRoomPrivacy> {Open | Closed | Secret}] [-Invitations <Switch Parameter>]
```

To set a room
  
```
Set-CsPersistentChatRoom -Identity <String> [-Name <String>] [-Category <String>] [-Description <String>] [-Disabled <boolean>] [-Type <Normal | Auditorium>] [-AddIn <String>] [-Privacy <ChatRoomPrivacy> {Open | Closed | Secret}] [-Invitations <Enum>] [-Members <PSListModifier<String>>] [-Managers <PSListModifier<String>>] [-Presenters <PSListModifier<String>>] [-Force < Switch Parameter >] [-Confirm <Switch Parameter>][-WhatIf <Switch Parameter>]
```

To get a room
  
```
Get-CsPersistentChatRoom -Identity <String>
```

or
  
```
Get-CsPersistentChatRoom -filter <String> [-PersistentChatPoolFqdn <String>] [-SearchDescription] [-Member <String>] [-Manager <string>] [-Category <string>] [-Addin <string>] [-Disabled <bool>] [-Privacy <ChatRoomPrivacy> {Open | Closed | Secret}] [-Type <ChatRoomType> {Normal | Auditorium}] [-Invitations <ChatRoomInvitations> {False | Inherit}] [-ChatContentExceedsMB <int>] [-ResultSize <int>]
```

where -filter supports only Name and Description and helps you find rooms whose Name/Description matches the keyword string. PoolFqdn searches in a given Persistent Chat Server pool.
  
To clear a room and clear messages from a room
  
```
Clear-CsPersistentChatRoom [-Identity] <string> -EndDate <DateTime> [-WhatIf] [-Confirm]  [<CommonParameters>]
```

or
  
```
Clear-CsPersistentChatRoom [-Instance] <ChatRoomObject> -EndDate <DateTime> [-WhatIf] [-Confirm] [<CommonParameters>]
```

To remove a room
  
```
Remove-CsPersistentChatRoom [-Identity] <string> [-Force] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

or
  
```
Remove-CsPersistentChatRoom [-Instance] <ChatRoomObject> [-Force] [-WhatIf] [-Confirm]  [<CommonParameters>]
```


