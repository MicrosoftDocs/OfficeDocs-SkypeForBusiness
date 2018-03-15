---
title: "Configuring supported client versions in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: aebf7b48-9aa2-4a06-adc5-0c9d11b6358d
description: "In Lync Server 2013, you can set up client version policies to specify the versions of clients that are supported in your environment. Additionally, you can use the global client version configuration to specify a default action for clients that do not already have a version policy defined and, therefore, are not explicitly supported or restricted."
---

# Configuring supported client versions in Lync Server 2013
[]
In Lync Server 2013, you can set up client version policies to specify the versions of clients that are supported in your environment. Additionally, you can use the global client version configuration to specify a default action for clients that do not already have a version policy defined and, therefore, are not explicitly supported or restricted.
  
You can also use client version policies to manage client updates. When you set a client version policy and use the options **Allow and upgrade** and **Block and upgrade**, clients will receive updated software from the Windows Server Update Service (if you are using this service) or from Microsoft Update.
  
## Client Version Policy Settings

The default client version policy requires that all clients run Lync. If clients in your environment are running earlier versions of Communicator, you may need to reconfigure the Client Version rules to prevent clients and devices from being unexpectedly blocked or updated when connecting to Lync Server 2013. You can modify the default rule, or you can add a rule higher in the Client Version Policy list to override the default rule. Additionally, as Cumulative Updates (CUs) are released, you should configure the Client Version Policy to require the latest updates. For details, see [Specifying the client applications that can be used to log on to Lync Server 2013](specifying-the-client-applications-that-can-be-used-to-log-on-to-lync-server-201.md) in the Operations documentation. 
  

