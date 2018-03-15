---
title: "Test Persistent Chat Server with a synthetic transaction"
ms.author: crowe
author: CarolynRowe
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 414e43f3-0074-4ecf-a232-398de972cb24
description: "To test Persistent Chat Server for sending and receiving messages in a chat room between two users"
---

# Test Persistent Chat Server with a synthetic transaction
[]
To test Persistent Chat Server for sending and receiving messages in a chat room between two users
  
```
Test-CsPersistentChatMessage [-Authentication <TrustedServer | Negotiate | ClientCertificate | 
    LiveID>] [-ReceiverSipAddress <String>] [-RegistrarPort <Int32>] [-SenderSipAddress <String>] -TargetFqdn <String> [-Force <SwitchParameter>] [-OutLoggerVariable <String>] 
    [-OutVerboseVariable <String>] [<CommonParameters>]
```

or
  
```
Test-CsPersistentChatMessage [-Authentication <TrustedServer | Negotiate | ClientCertificate | 
    LiveID>] -ReceiverCredential <PSCredential> -ReceiverSipAddress <String> [-RegistrarPort 
    <Int32>] -SenderCredential <PSCredential> -SenderSipAddress <String> [-TargetFqdn <String>] [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>] [<CommonParameters>]
```

or
  
```
Test-CsPersistentChatMessage [-Authentication <TrustedServer | Negotiate | ClientCertificate | 
    LiveID>] [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable 
    <String>] [<CommonParameters>]
```


