---
title: "Manage categories"
ms.author: crowe
author: CarolynRowe
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 1b118d91-b4c4-4b2f-b842-b451417ec2c6
description: "To create a new Persistent Chat Server Category"
---

# Manage categories
[]
To create a new Persistent Chat Server Category
  
```
New-CsPersistentChatCategory -Name Foo -PersistentChatPoolFqdn client.contosomanage-categories.com [other parameters]
```

> [!IMPORTANT]
> PersistentChatPoolFqdn is needed only if there is more than one Persistent Chat Server pool. 
  
To make changes to existing Persistent Chat Server Category
  
```
Set-CsPersistentChatCategory -Identity testCat -AllowedMembers @{Add="sip:user1@contoso.com", "CN=container,DC=contoso,DC=com"}  -DeniedMembers @{Add="sip:user2@contoso.com"}
Set-CsPersistentChatCategory -Identity testCat -Creators @{Add="sip:user1@contoso.com"}
```

Windows PowerShell: AllowedMembers, DeniedMembers, and Creators can be set simultaneously. Creators should be the subset of AllowedMembers minus DeniedMembers. You can also set the properties of a category at the same time as the members and creators.
  
## Create, Get, Set, or Remove a Category

To create a new Category
  
```
New-CsPersistentChatCategory -Name <String> [-PersistentChatPoolFqdn <String>] [-Description <String>] [-EnableInvitations<Switch Parameter>] [-EnableFileUpload <Switch Parameter>] [-RemoveChatHistory <Switch Parameter>] [-MaxContentSize <Integer>]
```

To get a Category
  
```
Get-CsPersistentChatCategory -Identity <String>
```

or
  
```
Get-CsPersistentChatCategory -PersistentChatPoolFqdn <String>
```

To set a Category
  
```
Set-CsPersistentChatCategory -Instance <CategoryObject> [-WhatIf] [-Confirm] [<CommonParameters>]
```

or
  
```
Set-CsPersistentChatCategory [-Identity] <string> [-Name <string>] [-Description <string>] [-Invitations <bool>] [-FileUpload <bool>] [-ChatHistory <bool>] [-AllowedMembers <PSListModifier[string]>] [-DeniedMembers <PSListModifier[string]>] [-Creators <PSListModifier[string]>] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

To remove a Category
  
```
Remove-CsPersistentChatCategory -Instance <CategoryObject> [-Force <Switch Parameter>] [-Confirm <Switch Parameter>]
```

or
  
```
Remove-CsPersistentChatCategory -Identity <String> [-Force <Switch Parameter>] [-Confirm <Switch Parameter>]
```


