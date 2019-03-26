---
title: Coexistence considerations
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Coexistence considerations
ms:assetid: 9d1a3c0f-492a-4e37-bc2f-63509e328785
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205131(v=OCS.15)
ms:contentKeyID: 48184990
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Coexistence considerations

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-06_

After migration, only a Lync Server 2013, Persistent Chat Server pool will exist, and you can decommission your legacy deployment.

Before migration completes and before you have decommissioned your current Group Chat Server deployment completely, you may have any of the following deployments:

  - Lync Server 2013, Persistent Chat Server pool, which must be homed on a Lync Server 2013 pool.

  - Lync Server 2010, Group Chat pool, which must be homed on a Lync Server 2010 pool.

  - Office Communications Server 2007 R2 Group Chat pool, which must be homed on an Office Communications Server 2007 R2 pool.

These deployments can exist side by side. However the categories, rooms, and add-ins in one deployment do not interact with those in the accompanying deployment.

Using manual configuration, a legacy client (Group Chat client) can connect to one pool at a time for Office Communications Server 2007 R2, Lync Server 2010, Group Chat, or Lync Server 2013.

The Lync 2013 (client) can interact only with the Lync Server 2013, Persistent Chat Server pool, not with legacy Group Chat Server pools. To use Persistent Chat in a Lync 2013 (client), the user must be homed on Lync 2013 and enabled by policy.

</div>

<span> </span>

</div>

</div>

</div>

