---
title: 'Lync Server 2013: Network regions'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Network regions
ms:assetid: 1818e9d2-bbb7-420a-93ea-4c3da3a55ad3
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ687979(v=OCS.15)
ms:contentKeyID: 49733567
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Network regions in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

*Network regions* are the network hubs or backbones used in the configuration of call admission control, E9-1-1, and media bypass. Use the following procedures to view, create, or modify network regions. For example, if you have already created network regions for one Voice feature, you do not need to create new network regions; other advanced Enterprise Voice features will use those same network regions. You may, however, need to modify an existing network region definition to apply feature-specific settings. For example, if you have created network regions for E9-1-1 (which do not require an associated central site) and you then deploy call admission control, you need to modify the network region definitions to specify a central site. For details, see [Configure network regions for CAC in Lync Server 2013](lync-server-2013-configure-network-regions-for-cac.md).

<div>


> [!NOTE]  
> Any feature-specific requirements for network region definitions are documented in the Deployment topics for the feature.



</div>

<div>

## In This Section

  - [Viewing network region information in Lync Server 2013](lync-server-2013-viewing-network-region-information.md)

  - [Creating or modifying network regions in Lync Server 2013](lync-server-2013-creating-or-modifying-network-regions.md)

  - [Deleting existing network regions in Lync Server 2013](lync-server-2013-deleting-existing-network-regions.md)

</div>

<div>

## Reference

[Deploying advanced Enterprise Voice features in Lync Server 2013](lync-server-2013-deploying-advanced-enterprise-voice-features.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

