---
title: 'Lync Server 2013: Assigning location policy scope'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Assigning location policy scope
ms:assetid: e4c66517-c593-4253-b900-7b4dd8bddf2f
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205360(v=OCS.15)
ms:contentKeyID: 48185734
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Assigning location policy scope in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-06-06_

As with other Lync Server policies, location policies can be assigned at multiple scope levels: global, site, and user. However, the scope of user-level location policies behaves a bit differently than with other Lync Server policies. Not only can per-user location policies be applied to endpoint objects (such as Users and Common Area Phone contact objects), they can also be applied to Lync Server network sites. Network sites are groupings of client subnets associated with a geographical location (but may not necessarily be all subnets in an entire central site or branch site). Any clients connected to the subnets in a network site automatically pick up the location policy assigned to that network site. In cases where a user-level location policy is assigned both to a user and to a network site, the network site-based location policy overrides any per-user policy setting.

Each network site has a location policy assigned to it, and each policy will have different PSTN Usages, Notification URIs, and Conference URIs values assigned to it.

<div>


> [!NOTE]  
> The reason for this special policy scoping behavior is so that when a user homed on a pool at one office site visits another site and has to make an emergency call, the E9-1-1 call routing settings appropriate to that network site will apply no matter what pool or site the user is assigned to.



</div>

</div>

<span> </span>

</div>

</div>

</div>

