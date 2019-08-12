---
title: 'Lync Server 2013: Migration and coexistence considerations for IPv6'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Migration and coexistence considerations for IPv6
ms:assetid: 8c769c4f-c8a9-4cbf-9080-beee3be9848a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205068(v=OCS.15)
ms:contentKeyID: 48184751
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Migration and coexistence considerations for IPv6 in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-06-14_

IP version 6 (IPv6) is not supported on Lync Server 2010 or Office Communications Server. For piloting purposes, you can test Lync Server 2010 and Lync Server 2013 dual-stack coexistence. We recommend that all pools for a given central site are upgraded to Lync Server 2013 before you enable IPv6 (dual-stack network) for any of the pools. If you need to configure a pool for IPv6 only, we recommend that you set up an IPv6-only pool in your lab environment for testing.

The following scenarios are supported during migration and coexistence:

  - Lync Server 2013, Lync Server 2010, and Office Communications Server 2007 R2 pools in IPv4 mode, coexisting with Lync Server 2013 in dual-stack mode.

  - Lync Server 2013 pool in IPv6-only mode, if the IPv6-only pool is siloed.

</div>

<span> </span>

</div>

</div>

</div>

