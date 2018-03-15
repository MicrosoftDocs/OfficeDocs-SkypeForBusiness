---
title: "Replacing the XmlAdapter with a customized Persistent Chat Server Compliance adapter in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 2cb70db2-663f-40a6-abcf-89ea7d4a8b65
description: "You can write a custom adapter instead of using the XmlAdapter that is installed with Persistent Chat Server. To accomplish this, you must provide a .NET Framework assembly that contains a public class that implements the IComplianceAdapter interface. You must place this assembly in the Persistent Chat Server installation folder of each server in your Persistent Chat Server pool. Any one of the Compliance servers can provide compliance data to your adapter, but the compliance servers will not provide duplicate compliance data to multiple instances of your adapter."
---

# Replacing the XmlAdapter with a customized Persistent Chat Server Compliance adapter in Lync Server 2013
[]
You can write a custom adapter instead of using the XmlAdapter that is installed with Persistent Chat Server. To accomplish this, you must provide a .NET Framework assembly that contains a public class that implements the **IComplianceAdapter** interface. You must place this assembly in the Persistent Chat Server installation folder of each server in your Persistent Chat Server pool. Any one of the Compliance servers can provide compliance data to your adapter, but the compliance servers will not provide duplicate compliance data to multiple instances of your adapter. 
  
## Implementing the IComplianceAdapter interface

The interface is defined in the Compliance.dll assembly in the namespace  `Microsoft.Rtc.Internal.Chat.Server.Compliance`. The interface defines two methods that your custom adapter must implement.
  
```
void SetConfig(AdapterConfig config)
```

The Persistent Chat Compliance server will call this method when the adapter first loads. The  `AdapterConfig` contains the Persistent Chat compliance configuration that is relevant to the compliance adapter. 
  
```
void Translate(ConversationCollection conversations)
```

The Persistent Chat Compliance server calls this method at periodic intervals as long as there is new data to translate. This time interval is equal to the  `RunInterval` as set in the Persistent Chat Compliance configuration. 
  
The  `ConversationCollection` contains the conversation information that was collected from the last time this method was called. 
  

