---
title: "Support for hosted Exchange UM integration in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c7573ec3-013c-48d9-b59b-2a5427e6da35
description: "The Lync Server 2013 ExUM Routing application supports integration with Exchange Unified Messaging (UM) in an on-premises environment, where Lync Server 2013 and Exchange UM are both installed locally within your enterprise, or in with Exchange UM hosted by a service provider, as shown in the following diagram."
---

# Support for hosted Exchange UM integration in Lync Server 2013
[]
The Lync Server 2013 ExUM Routing application supports integration with Exchange Unified Messaging (UM) in an on-premises environment, where Lync Server 2013 and Exchange UM are both installed locally within your enterprise, or in with Exchange UM hosted by a service provider, as shown in the following diagram.
  
![On-premises Lync Server Exchange UM Deployment](media/HEXUMArch.jpg)
  
The following modes are supported:
  
- **On-premises Mode** Lync Server 2013 and Exchange UM are both deployed on local servers within your enterprise. 
    
- **Cross-premises Mode** Lync Server 2013 is deployed on local servers within your enterprise and Exchange UM is hosted in an online service provider's facility, such as a Microsoft Exchange Online data center. 
    
- **Mixed Mode** Your Lync Server 2013 deployment has some user mailboxes homed on local servers running Microsoft Exchange Server within your enterprise and some mailboxes homed in a hosted Exchange service data center. 
    
    > [!NOTE]
    > Mixed mode can be used as a transitional solution during evaluation and stepwise migration of users to hosted Exchange UM, or as a permanent solution if you opt to keep some users' Exchange UM services on-premises after migrating others. 
  
To integrate Lync Server 2013 with hosted Exchange UM, you must configure a shared SIP address space (also called a split domain). In this configuration, both Lync Server 2013 and the third-party hosted Exchange UM service provider can access the same SIP domain address space. For details, see [Hosted Exchange UM integration architecture in Lync Server 2013](hosted-exchange-um-integration-architecture.md) in the Planning documentation. 
  

