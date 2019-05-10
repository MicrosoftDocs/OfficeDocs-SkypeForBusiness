---
title: 'Lync Server 2013: Deploy IP address types on an Edge Server'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Deploy IP address types on an Edge Server
ms:assetid: 6e2fe7e8-6e90-4d1a-8fc5-e3be92c46571
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204984(v=OCS.15)
ms:contentKeyID: 48184435
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Deploy IP address types on an Edge Server for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-06-14_

Using Topology Builder, perform the steps in the following procedure to deploy IP address types on an Edge Server.

<div>

## To deploy IP address types on an Edge Server

1.  In Topology Builder, under **Edge pools**, right-click the server within a pool, and then select **Edit Properties**. (Alternatively, select the server, and then click **Edit Properties** from the **Action** menu.)

2.  In the **Edit Properties** window, select the IP address configuration that you want to support. The following figures show a dual stack configuration for the internal interface and the external interface.
    
    **Dual stacked Edge Server internal interface**
    
    ![Lync Server general properties page](images/JJ204984.5b0883ee-b9f2-4a21-91a9-3286d0beb63b(OCS.15).png "Lync Server general properties page")
    
    **Dual stacked Edge Server external interface**
    
    ![Lync Server next hop/external configuration page](images/JJ204984.2aa00ce2-ba50-40aa-bbf1-78636016daf9(OCS.15).png "Lync Server next hop/external configuration page")

3.  For each address type that you select, you must supply appropriate internal and external addresses.

</div>

</div>

<span> </span>

</div>

</div>

</div>

