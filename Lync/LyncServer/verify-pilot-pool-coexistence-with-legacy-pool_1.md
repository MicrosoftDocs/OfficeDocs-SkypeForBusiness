---
title: Verify pilot pool coexistence with legacy pool
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Verify pilot pool coexistence with legacy pool
ms:assetid: 597d0fa6-ca04-4521-b1c2-72d7f35ecd08
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204914(v=OCS.15)
ms:contentKeyID: 48184209
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

_**Topic Last Modified:** 2012-09-28_

<div>

## Verify the Pool in Office Communications Server 2007 R2 Administrative Tool

1.  Open the Office Communications Server 2007 R2 administrative tool.

2.  Expand the **Forest** node, expand the **Standard Edition Servers** or **Enterprise pools** node, and then expand the pool or server name.

3.  Ensure that the Office Communications Server 2007 R2 services are running on the pool.
    
    ![Office Communications Server 2007 R2 Admin Console](images/JJ721906.76897b6d-f433-47d2-930d-0816fc30a3c2(OCS.15).jpg "Office Communications Server 2007 R2 Admin Console")  

</div>

<div>

## Verify the Pilot Pool in Lync Server 2013 Control Panel

1.  From a user account that is a member of the CsAdministrator role, log on to the Lync Server 2013 Front End server.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Click **Topology**.

4.  Verify that the servers you deployed are present in your pilot pool.
    
    ![Lync Server Control Panel Topology page](images/JJ204914.a3d1ba5f-c1a7-45e8-b9a5-7cb07b01af8c(OCS.15).jpg "Lync Server Control Panel Topology page")  

</div>

<div>

## Verify Lync Server 2013 services have started

1.  On the Lync Server 2013 Front End Server, open the **Services** applet from the **Administrative Tools** group.

2.  Verify that the services listed match the list in the following figure.
    
    ![Services page showing Lync services started](images/JJ204914.fd35d54a-2ab6-4c09-b5e9-fd5bf10f6f51(OCS.15).jpg "Services page showing Lync services started")  

</div>

</div>

<span> </span>

</div>

</div>

</div>

