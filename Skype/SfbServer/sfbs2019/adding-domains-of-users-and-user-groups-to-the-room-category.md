---
title: "Adding domains of users and user groups to the room category in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ee03f2cf-1c84-41c4-b524-d0729be33b8c
description: "To add larger groups of users to a chat room, see Configure categories in Lync Server 2013 and Manage categories in the Deployment documentation. For example, this command adds all the users from the NorthAmericaUsers OU in active Directory to the NorthAmerica chat room:"
---

# Adding domains of users and user groups to the room category in Lync Server 2013
[]
To add larger groups of users to a chat room, see [Configure categories in Lync Server 2013](configure-categories.md) and [Manage categories](manage-categories.md) in the Deployment documentation. For example, this command adds all the users from the NorthAmericaUsers OU in active Directory to the NorthAmerica chat room: 
  
```
Set-CsPersistentChatRoom -PersistentChatPoolFqdn "atl-cs-001.litwareinc.com\NorthAmerica" -Members @{Add="OU=NorthAmericaUsers,DC=litwareinc,DC=com"}
```

His command adds all the members from the Finance distribution group to the same chat room:
  
```
Set-CsPersistentChatRoom -PersistentChatPoolFqdn "atl-cs-001.litwareinc.com\NorthAmerica" -Members @{Add="CN=Finance,OU=ExternalUsers,DC=litwareinc,DC=com"}
```


