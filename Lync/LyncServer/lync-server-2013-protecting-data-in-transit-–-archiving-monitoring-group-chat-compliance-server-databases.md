---
title: 'Lync Server 2013: Protecting data in transit – archiving, monitoring, group chat compliance server databases'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Protecting data in transit – archiving, monitoring, group chat compliance server databases in Lync Server 2013
ms:assetid: ea219705-1015-43a7-890b-e7e67b451e7c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn518336(v=OCS.15)
ms:contentKeyID: 62625494
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Protecting data in transit – archiving, monitoring, group chat compliance server databases in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-12-05_

Microsoft Lync Server 2013 Archiving Server and Monitoring Server both use the Message Queuing (also known as MSMQ) service to collect and reliably move data messages from the collection point to the repository servers. Compliance service collects data in conjunction with the Group Chat Server, which also uses Message Queuing.

In Lync Server 2013, there is no internal protection for data on the wire; however, if there is a requirement to secure this traffic, the Message Queuing service can provide encryption at a message level on the sending message queue. This is accomplished using certificates that are managed by the Active Directory Domain Services. For details, see Appendix D: Message Queuing and Internet Communication in Windows Server 2008 at [http://go.microsoft.com/fwlink/p/?LinkId=145238](http://go.microsoft.com/fwlink/p/?linkid=145238) or Appendix I: Message Queuing and Internet Communication in Windows Server 2008 R2 at [http://go.microsoft.com/fwlink/p/?LinkId=211883](http://go.microsoft.com/fwlink/p/?linkid=211883) for Windows Server 2008 R2.

</div>

<span> </span>

</div>

</div>

</div>

