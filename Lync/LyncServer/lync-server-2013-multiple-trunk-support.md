---
title: 'Lync Server 2013: Multiple trunk support'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Multiple trunk support
ms:assetid: a1309c09-ad9a-4c54-9650-4e3f5b2a4a00
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205127(v=OCS.15)
ms:contentKeyID: 48184948
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Multiple trunk support in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-11-01_

Lync Server 2013 functionality supports multiple associations between gateways and Mediation Servers. These associations are made by defining a trunk, which is a logical association between a Mediation Server pool and a public switched telephone network (PSTN) gateway, Session Border Controller (SBC), or IP-PBX. Use the Topology Builder to associate gateways with Mediation Servers (that is, trunks).

  - To assign or remove a trunk in Lync Server 2013, you must first define a trunk in Topology Builder. A trunk consists of the following association: Mediation Server fully qualified domain name (FQDN), the Mediation Server listening port, the gateway FQDN, and the gateway listening port.

  - To configure multiple trunks, you can create multiple associations between the same gateway and the Mediation Server. This provides additional resiliency to the Enterprise Voice infrastructure, which is especially useful in private branch exchange (PBX) interoperational scenarios.

When a trunk is defined, it must be associated to a route. To associate a trunk to a route, you define a simple name for the trunk in Topology Builder. This simple name is used as the trunk name in the Lync Server Control Panel, where trunks can be associated with routes. The simple trunk name is used as the gateway name from the Lync Server Management Shell.

    New-CsVoiceRoute -Identity <RouteId> -NumberPattern <String> -PstnUsages @{add="<UsageString>"} -PstnGatewayList @{add="<TrunkSimpleName>"}

The administrator must select a default trunk associated with a Mediation Server. From the Topology Builder, right-click the associated Mediation Server, and then click **Properties**. Specify the default gateway for the Mediation Server.

The following diagram illustrates the multiple trunks that are defined for each Mediation Server and gateway.

**M-N Trunk Routing**

![Multiple trunk assignments.](images/JJ205127.c61cd9a7-d8d9-4e02-83b9-ab62519a48c4(OCS.15).jpg "Multiple trunk assignments.")

</div>

<span> </span>

</div>

</div>

</div>

