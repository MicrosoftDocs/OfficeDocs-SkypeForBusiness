---
title: 'Lync Server 2013: Preparing the forest'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Preparing the forest
ms:assetid: 3d188fcb-c64e-46cf-a3a7-9e3ebefed7fd
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425898(v=OCS.15)
ms:contentKeyID: 48183926
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Preparing the forest for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

Forest preparation creates Active Directory global settings and objects and Active Directory universal groups for use by Lync Server 2013, and grants suitable access permissions on the Active Directory objects. For a description of the universal groups and the global settings and objects created by forest preparation, see [Changes made by forest preparation in Lync Server 2013](lync-server-2013-changes-made-by-forest-preparation.md).

Forest preparation also creates objects that contain property sets and display specifiers that are used by Lync Server 2013, and stores them in the Configuration container.

<div>


> [!IMPORTANT]  
> Make sure that schema preparation changes have replicated to all domain controllers before performing the forest preparation procedure. If replication is not completed, an error occurs.



</div>

If you are performing a new Lync Server deployment, you must store global settings in the Configuration container. If you are upgrading from an earlier version and you still store global settings in the System container, you can continue to use the System container.

You must be a member of the Enterprise Admins or Domain Admins group for the forest root domain to perform this procedure.

<div>

## In This Section

  - [Running forest preparation for Lync Server 2013](lync-server-2013-running-forest-preparation.md)

  - [Using cmdlets to reverse forest preparation for Lync Server 2013](lync-server-2013-using-cmdlets-to-reverse-forest-preparation.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

