---
title: "Configure Persistent Chat Server in Lync Server 2013"
ms.author: crowe
author: CarolynRowe
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 85028aff-a38e-4748-958e-59e707a47532
description: "To create a new Persistent Chat configuration"
---

# Configure Persistent Chat Server in Lync Server 2013
[]
To create a new Persistent Chat configuration
  
```
New-CsPersistentChatConfiguration -Identity <XdsIdentity> [-DefaultChatHistory <Integer>] [-MaxChatContentSizeMB <Integer>] [-MaxFileSizeKB <Integer>] [-ParticipantUpdateLimit <Integer>] [-FileServiceUrl <UrlForFileUpload>] [-RoomManagementUrl <RoomManagementUrl>] [-Instance <PSObject>] [-Force <Switch Parameter>] [-Confirm <Switch Parameter>] [-WhatIf <Switch Parameter>]
```

To get Persistent Chat configuration
  
```
Get-CsPersistentChatConfiguration [-LocalStore <Switch Parameter>] [-Identity <XdsIdentity>]
```

To remove Persistent Chat configuration
  
```
Remove-CsPersistentChatConfiguration -Identity <XdsIdentity>
```

To set Persistent Chat configuration
  
```
Set-CsPersistentChatConfiguration [-DefaultChatHistory <Integer>] [-MaxChatContentSizeMB <Integer>] [-MaxFileSizeKB <Integer>] [-ParticipantUpdateLimit <Integer>] [-FileServiceUrl <UrlForFileUpload>] [-RoomManagementUrl <RoomManagementUrl>] [-Instance <PSObject >] [-Force <Switch Parameter>] [-Confirm <Switch Parameter>] [-WhatIf <Switch Parameter>]
```

For Lync Server 2013, all web service traffic is supported on the Lync Server 2013, Front End Servers. Therefore, the gcweb01 address on Persistent Chat Server is not necessary. We still support internal web service access because we provide the File Upload/Download Web service to the  *internal*  website only (not to the  *external*  website for remote users). 
  

