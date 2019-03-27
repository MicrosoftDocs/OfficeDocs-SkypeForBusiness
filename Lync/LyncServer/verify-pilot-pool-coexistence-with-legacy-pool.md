---
title: Verify pilot pool coexistence with legacy pool
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Verify pilot pool coexistence with legacy pool
ms:assetid: fe7e14bb-c7eb-4719-b154-009e99360520
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205420(v=OCS.15)
ms:contentKeyID: 48185964
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Verify pilot pool coexistence with legacy pool

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-29_

After you deploy the pilot pool, you need to verify the coexistence of the two pools by using the administrative tools to view the pool information. For the Lync Server 2013 pools and legacy pools, you must use the Lync Server 2013 Control Panel and Topology Builder tools.

<div>

## Verify that Lync Server 2013 services have started

1.  From the Lync Server 2013 Front End Server, navigate to the Administrative Tools\\Services applet.

2.  Verify that the following services are running on the Front End Server:

**Lync Server 2013 services**

![List of Lync Server Services Started](images/JJ205420.cfff9385-6bf6-461c-982c-e727c9f20b70(OCS.15).png "List of Lync Server Services Started")

</div>

<div>

## Open the Lync Server 2013 Control Panel

From the Front End Server in your Lync Server 2013 deployment, open the Lync Server 2013 Control Panel and select the Lync Server 2010 pool. Repeat the procedure to open the Lync Server 2013 pool.

**Open Lync Server 2013 Control Panel**

![Select URL dialog box](images/JJ205420.b1f8e650-9c3c-4563-a403-5069f198342f(OCS.15).png "Select URL dialog box")

<div>


> [!IMPORTANT]  
> On Lync Server 2013, you must upgrade Silverlight to Silverlight version 5 prior to using the Lync Server Control Panel.



</div>

This topology now includes Lync Server 2010 and Lync Server 2013 server roles.

**Lync Server 2013 Control Panel Topology page**

![Lync Server Control Panel - Topology page](images/JJ205420.4ed1cc7a-cb3e-42f6-82e2-6d4d71d19352(OCS.15).jpg "Lync Server Control Panel - Topology page")

</div>

<div>

## Don’t attempt to open the topology in Lync Server 2010 Topology Builder

If you attempt to open the topology using Lync Server 2010 Topology Builder, you will encounter the error below. The topology can only be viewed using Lync Server 2013 Topology Builder. The Lync Server 2013 Topology Builder must be used to create pools for both Lync Server 2013 and Lync Server 2010.

**Lync Server 2010 Topology Builder error message**

![Lync Server Topology Builder MMC Snap Error](images/JJ205420.f6666343-c348-4d81-ae0e-6ba5a44e16c4(OCS.15).png "Lync Server Topology Builder MMC Snap Error")

</div>

</div>

<span> </span>

</div>

</div>

</div>

