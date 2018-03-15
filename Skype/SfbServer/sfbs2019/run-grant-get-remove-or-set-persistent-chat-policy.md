---
title: "Run, grant, get, remove, or set Persistent Chat Policy in Lync Server 2013"
ms.author: crowe
author: CarolynRowe
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 39ccdbe8-fb3d-47bc-96e2-9486b6d317e0
description: "To create a new Persistent Chat policy"
---

# Run, grant, get, remove, or set Persistent Chat Policy in Lync Server 2013
[]
To create a new Persistent Chat policy
  
```
New-CsPersistentChatPolicy -Identity <XdsIdentity> [-Enable <Switch Parameter>] [-Confirm <Switch Parameter>] [-Force <Switch Parameter>] [-WhatIf <Switch Parameter>] [-InMemory <Switch Parameter>]
```

To grant Persistent Chat policy
  
```
Grant-CsPersistentChatPolicy -Identity <UserIdParameter> -PolicyName <String> [-Confirm <Switch Parameter>] [-WhatIf <Switch Parameter>]
```

To get Persistent Chat policy
  
```
Get-CsPersistentChatPolicy [-Identity <XdsIdentity>] [-Filter <String>] [-LocalStore <Switch Parameter>]
```

To remove Persistent Chat policy
  
```
Remove-CsPersistentChatPolicy -Identity <XdsIdentity> [-Confirm <Switch Parameter>] [-Force <Switch Parameter>] [-WhatIf <Switch Parameter>]
```

To set Persistent Chat policy
  
```
Set-CsPersistentChatPolicy [-Identity <XdsIdentity>] [-Instance < PSObject>]
```


