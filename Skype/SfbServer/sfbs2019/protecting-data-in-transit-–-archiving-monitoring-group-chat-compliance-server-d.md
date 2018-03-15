---
title: "Protecting data in transit - archiving, monitoring, group chat compliance server databases in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ea219705-1015-43a7-890b-e7e67b451e7c
description: "Microsoft Lync Server 2013 Archiving Server and Monitoring Server both use the Message Queuing (also known as MSMQ) service to collect and reliably move data messages from the collection point to the repository servers. Compliance service collects data in conjunction with the Group Chat Server, which also uses Message Queuing."
---

# Protecting data in transit - archiving, monitoring, group chat compliance server databases in Lync Server 2013
[]
Microsoft Lync Server 2013 Archiving Server and Monitoring Server both use the Message Queuing (also known as MSMQ) service to collect and reliably move data messages from the collection point to the repository servers. Compliance service collects data in conjunction with the Group Chat Server, which also uses Message Queuing.
  
In Lync Server 2013, there is no internal protection for data on the wire; however, if there is a requirement to secure this traffic, the Message Queuing service can provide encryption at a message level on the sending message queue. This is accomplished using certificates that are managed by the Active Directory Domain Services. For details, see Appendix D: Message Queuing and Internet Communication in Windows Server 2008 at [https://go.microsoft.com/fwlink/p/?LinkId=145238](https://go.microsoft.com/fwlink/p/?LinkId=145238) or Appendix I: Message Queuing and Internet Communication in Windows Server 2008 R2 at [https://go.microsoft.com/fwlink/p/?LinkId=211883](https://go.microsoft.com/fwlink/p/?LinkId=211883) for Windows Server 2008 R2. 
  

