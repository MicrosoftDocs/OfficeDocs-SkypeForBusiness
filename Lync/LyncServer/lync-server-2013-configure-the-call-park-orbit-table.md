---
title: 'Lync Server 2013: Configure the Call Park orbit table'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configure the Call Park orbit table
ms:assetid: e5cc0c19-7b2c-48e7-a21d-cfb23c842f0f
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg399020(v=OCS.15)
ms:contentKeyID: 48185666
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure the Call Park orbit table in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-10_

Call Park uses orbits for parking calls. Before users can park and retrieve calls, you must configure the Call Park orbit table. You need to specify the ranges of extension numbers (orbits) that your organization will reserve for parking calls and define the routing for those ranges by specifying which Call Park pool handles each range. When you define orbit ranges, the goal is to have enough orbits so that any one orbit is not reused too quickly, but not so many orbits that you limit the number of extensions available for users or other services. You can create multiple Call Park orbit ranges for each Lync Server pool where the Call Park application is deployed. Each Call Park orbit range must have a globally unique name and a unique set of extensions.

<div>


> [!IMPORTANT]  
> An orbit range typically encompasses 100 or fewer orbits. Each range can be much larger, as long as it is smaller than the maximum of 10,000 orbits per range and you have fewer than 50,000 orbits per pool. If a range is too small, the orbits are reused more quickly.



</div>

Use blocks of virtual extensions (extensions that have no user or phone assigned to them) for your orbit ranges.

<div>


> [!NOTE]  
> Assigning Direct Inward Dialing (DID) numbers as orbit numbers in the Call Park orbit table is not supported.



</div>

<div>

## In This Section

[Create or modify a Call Park orbit range in Lync Server 2013](lync-server-2013-create-or-modify-a-call-park-orbit-range.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

