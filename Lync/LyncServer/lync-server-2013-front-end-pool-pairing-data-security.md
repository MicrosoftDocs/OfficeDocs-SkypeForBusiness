---
title: 'Lync Server 2013: Front End pool pairing data security'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Front End pool pairing data security
ms:assetid: edb852b8-ea86-4948-b756-60fe6ee876d2
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ721930(v=OCS.15)
ms:contentKeyID: 49733865
ms.date: 10/07/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Front End pool pairing data security in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-10-07_

The Backup Service is a data replication mechanism introduced in Lync Server 2013 that transfers user data and conference content between two paired Front End pools continuously across two data centers for disaster recovery purposes. The user data contains user SIP URIs as well as contact lists and settings. Conference content includes Microsoft PowerPoint 2010 uploads, as well as whiteboards used in conferences. From the source pool, user data and conference content are exported from the local storage, zipped, transferred to the target Pool, where it is unzipped and imported to local storage. The Backup Service assumes that the communications link between the two data centers is within the corporate network that is protected from the Internet. It does not encrypt the transferred data between the two data centers, nor is it natively encapsulated within a secure protocol, such as HTTPS. Therefore, man-in-the-middle attack from internal personnel within the corporate network is possible.

<div>

## Evaluating Security Risks

Any enterprise which deploys Lync Server 2013 across multiple data centers and uses the disaster recovery feature must ensure that cross-data center traffic is protected by their corporate Intranet. Enterprises which care about internal attack protection must secure the communication links among the data centers.

The assumption that data centers of an enterprise are protected behind the corporate Intranet is standard. There are many other types of corporate sensitive data transferred among these data centers. The enterprise’s IT infrastructure is at dire risk if these cross-data center links are not protected.

While the risk of man-in-the-middle attacks within the corporate network exists, it is relatively contained as compared to exposing the traffic to the Internet. Specifically, the user data exposed by Backup Service (such as SIP URIs) are generally available to all employees within the company via other means such as the Global Address Book by Exchange or other directory software. Hence, the focus should be on securing the WAN between the two data centers when the Backup Service is used to copy data between the two paired Pools.

</div>

<div>

## Mitigating Security Risks

There are many ways to enhance security protection for the Backup Service traffic, ranging from restricting access to the data centers to securing the WAN transport between the two data centers. In most cases, enterprises deploying Lync Server 2013 might already have the required security infrastructure in place. For enterprises looking for guidance, Microsoft provides solution as an example of how to build a secure IT infrastructure. However, this does not imply that it is the only solution, nor does it imply that it is the preferred solution for Lync Server. We recommend that enterprise customers choose the solution suits their specific needs, based on their IT security infrastructure and requirements.The example Microsoft solution employs IPSec and Group Policy for Server and Domain Isolation. For details, see [http://go.microsoft.com/fwlink/p/?LinkId=268544](http://go.microsoft.com/fwlink/p/?linkid=268544). For questions and comments, contact secwish@microsoft.com.

Another possible solution is to use IPSec just to help secure the data sent by the Backup Service itself. If you choose this method, you should configure the IPSec rules for the SMB protocol for the following servers, where Pool A and Pool B are two paired Front End pools.

  - The SMB Service (TCP/445) from each Front End Server in Pool A to the File Store used by Pool B.

  - The SMB Service (TCP/445) from each Front End Server in Pool B to the File Store used by Pool A.

<div>


> [!WARNING]  
> IPsec is not intended as a replacement for application-level security, such as SSL/TLS. One advantage of using IPsec is that it can provide network traffic security for existing applications without having to change them. Enterprises that want to just secure the transport between the two data centers should consult their respective networking hardware vendors about ways to set up secure WAN connections by using the vendor’s equipment.



</div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

