---
title: Migration process
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Migration process
ms:assetid: b2bd9c76-2f4b-4d14-a5c4-157bbff75de0
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205181(v=OCS.15)
ms:contentKeyID: 48185157
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Migration process

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-24_

The recommended and supported migration procedure for Lync Server 2013 is the side-by-side migration procedure. This topic describes why you should use side-by-side migration and also includes information about coexistence.

<div>

## Side-by-Side Migration

In nearly every migration, you should use the side-by-side migration path. In a side-by-side migration, you deploy a new server with Lync Server 2013 alongside a corresponding server that is running Office Communications Server 2007 R2, and then you transfer operations to the new server. If it becomes necessary to roll back to Office Communications Server 2007 R2, you have only to shift operations back to the original servers. Be aware that in this situation any new meetings scheduled with upgraded clients will not work, and the clients would also need to be downgraded.

</div>

<div>

## Coexistence Testing

After you have deployed Lync Server 2013 in parallel with Office Communications Server 2007 R2, the topology represents a coexistence testing state of Lync Server 2013 and Office Communications Server 2007 R2. While in this state, it is important to test and ensure services are started, each site can be administered, and clients can communicate with current and legacy users. Prior to the migration of all users, it is very important that you understand the state of each deployment and ensure that each deployment is functional and working properly. Typically, the coexistence testing phase exists throughout the pilot testing of Lync Server 2013. Legacy users are moved to Lync Server 2013 for a period of time to ensure that application compatibility and features and functions are working properly. After pilot testing, users and applications are moved to the production version of Lync Server 2013, and the legacy pools and applications of Office Communications Server 2007 R2 are retired.

</div>

</div>

<span> </span>

</div>

</div>

</div>

