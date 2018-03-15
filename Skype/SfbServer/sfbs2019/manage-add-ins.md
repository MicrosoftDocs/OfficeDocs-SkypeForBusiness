---
title: "Manage add-ins"
ms.author: crowe
author: CarolynRowe
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b84f868e-b36e-4ab4-b284-7db212d401c3
description: "To create a new Persistent Chat Server Add-in"
---

# Manage add-ins
[]
To create a new Persistent Chat Server Add-in
  
```
New-CsPersistentChatAddin -Name Contoso -PersistentChatPoolFqdn client.contoso.com -Url http://contoso.com 
```

## Create, Get, Set, or Remove an Add-in

To create a new Add-in
  
```
New-CsPersistentChatAddin -PersistentChatPoolFqdn <String> -Name <String> -Url<String>
```

> [!IMPORTANT]
> PersistentChatPoolFqdn \<String\> is required only if there is more than one Persistent Chat Server pool. 
  
To get an Add-in
  
```
Get-CsPersistentChatAddin -Identity <String>]
```

or
  
```
Get-CsPersistentChatAddin -PersistentChatPoolFqdn <String>
```

To set an Add-in
  
```
Set-CsPersistentChatAddIn -Instance <AddinObject> [-Force <Switch Parameter>] [-Confirm <Switch Parameter>]
```

or
  
```
Set-CsPersistentChatAddIn -Identity <String> [-Name <String>] [-Url<String>] [-Force <Switch Parameter>] [-Confirm <Switch Parameter>]
```

To remove an Add-in
  
```
Remove-CsPersistentChatAddIn -Instance <AddinObject> [-Force <Switch Parameter>] [-Confirm <Switch Parameter>]
```

or
  
```
Remove-CsPersistentChatAddIn -Identity <String> [-Force <Switch Parameter>] [-Confirm <Switch Parameter>]
```


