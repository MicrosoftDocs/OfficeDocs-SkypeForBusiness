---
title: "Exchange Unified Messaging (UM) support in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 0da62b8d-7416-4fb8-a405-381ca805c53a
description: "Lync Server 2013 supports integration with Exchange Unified Messaging (UM) for combining voice messaging and email messaging into a single messaging infrastructure. In Exchange 2013, Exchange UM consists of the Exchange UM service, which is installed and runs on the Mailbox server, and the UM Call Router, which is installed and runs on the Client Access server. For Lync Server 2013 Enterprise Voice deployments, Exchange UM combines voice messaging and email messaging into a single store that is accessible from a telephone (that is, Outlook Voice Access) or a computer. Exchange UM and Lync Server 2013 work together to provide call answering, Outlook Voice Access, and auto attendant services to users of Enterprise Voice."
---

# Exchange Unified Messaging (UM) support in Lync Server 2013
[]
Lync Server 2013 supports integration with Exchange Unified Messaging (UM) for combining voice messaging and email messaging into a single messaging infrastructure. In Exchange 2013, Exchange UM consists of the Exchange UM service, which is installed and runs on the Mailbox server, and the UM Call Router, which is installed and runs on the Client Access server. For Lync Server 2013 Enterprise Voice deployments, Exchange UM combines voice messaging and email messaging into a single store that is accessible from a telephone (that is, Outlook Voice Access) or a computer. Exchange UM and Lync Server 2013 work together to provide call answering, Outlook Voice Access, and auto attendant services to users of Enterprise Voice.
  
In addition to the support for integration with on-premises deployments of Exchange UM, Lync Server 2013 supports integration with hosted Exchange UM. This enables you to provide voice messaging to your users if you migrate some or all of them to a hosted Exchange service provider such as Microsoft Exchange Online.
  
Lync Server 2013 supports the following versions:
  
- Microsoft Exchange 2013
    
- Microsoft Exchange Server 2010 (required) or with latest service pack (recommended)
    
- Microsoft Exchange Server 2007 with Service Pack 1 (SP1) (required) or latest service pack (recommended)
    
You cannot collocate Exchange UM with Lync Server 2013 or a Lync Server 2013 database. You can install Exchange UM and Lync Server 2013 in separate forests.
  
> [!NOTE]
> Exchange UM may not be required for Enterprise Voice deployments that have a PBX deployed, because the PBX can continue to provide voice mail and related services to all users. If you eventually retire the PBX (for example, if you deploy SIP trunking for public switched telephone network (PSTN) connectivity), you must reconfigure Exchange UM to provide voice mail to users who previously used the PBX voice mail system. 
  
## In this section

- [Components and topologies for on-premises Unified Messaging in Lync Server 2013](components-and-topologies-for-on-premises-unified-messaging.md)
    
- [Support for hosted Exchange UM integration in Lync Server 2013](support-for-hosted-exchange-um-integration.md)
    

