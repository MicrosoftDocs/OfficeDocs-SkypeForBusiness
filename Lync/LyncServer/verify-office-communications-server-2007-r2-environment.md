---
title: Verify Office Communications Server 2007 R2 environment
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Verify Office Communications Server 2007 R2 environment
ms:assetid: e051bdd5-e7ef-4754-8705-900b2c57f37c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ721906(v=OCS.15)
ms:contentKeyID: 49733840
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Verify Office Communications Server 2007 R2 environment

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-16_

Prior to deploying Lync Server 2013 in a coexistence state with Office Communications Server 2007 R2, you need to verify the Office Communications Server 2007 R2 services are configured and started.

**Verify the Pool is started using the Office Communications Server 2007 R2 Administrative Tool**

1.  Open the Office Communications Server 2007 R2 administrative tool.

2.  Expand the **Forest** node, expand the **Standard Edition Servers** or **Enterprise pools** node, and then expand the pool or server name.

3.  Ensure that the services are running on the Standard Edition server or Enterprise pool.
    
    ![Office Communications Server 2007 R2 Admin Console](images/JJ721906.76897b6d-f433-47d2-930d-0816fc30a3c2(OCS.15).jpg "Office Communications Server 2007 R2 Admin Console")

**Review Users configured for Office Communications Server 2007 R2**

1.  Open the Office Communications Server 2007 R2 administrative tool.

2.  Expand the **Forest** node, expand the **Standard Edition Servers** or **Enterprise pools** node, and then expand the pool or server name.

3.  Click **Users**.

4.  Verify the list of Office Communications Server 2007 R2 users.
    
    ![List fo users in OCS Admin tool](images/JJ721906.f6bb7c4f-cbed-4389-8d0a-69a28577f17a(OCS.15).jpg "List fo users in OCS Admin tool")

**Verify legacy XMPP Federated Partner Configuration**

1.  From the legacy XMPP server, navigate to the Administrative Tools\\Services applet.

2.  Verify that the Office Communications Server XMPP Gateway service is started.
    
    ![Office Communications Server XMPP Gateway Service](images/JJ721906.23223724-3c4b-4cb9-ace2-1cab2c3c91c3(OCS.15).jpg "Office Communications Server XMPP Gateway Service")

</div>

<span> </span>

</div>

</div>

</div>

