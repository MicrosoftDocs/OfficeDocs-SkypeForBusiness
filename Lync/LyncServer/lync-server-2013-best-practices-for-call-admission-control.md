---
title: 'Lync Server 2013: Best practices for call admission control'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Best practices for call admission control
ms:assetid: 97173cca-8175-4ae2-a247-eb7ef809da93
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398770(v=OCS.15)
ms:contentKeyID: 48184913
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Best practices for call admission control in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-22_

To enhance performance and facilitate deployment, apply the following best practices when you deploy call admission control:

  - Ensure that WANs are adequately provisioned for current and anticipated media traffic.
    
    <div>
    

    > [!NOTE]  
    > We recommend that you factor in a buffer to your bandwidth limits. There are scenarios such as race conditions that affect the total bandwidth used and can result in situations where the bandwidth limit is exceeded. For example, if two calls try to start while media traffic is approaching a bandwidth limit, one of them may be denied because the other managed to start first.

    
    </div>

  - Monitor network usage and call detail records so that you can choose optimal CAC settings and update CAC settings as network usage changes.

  - Use CAC bandwidth policies to complement QoS settings.

  - If you want to re-route blocked calls onto the PSTN, verify PSTN functionality and capacity. For details, see [Planning outbound voice routing in Lync Server 2013](lync-server-2013-planning-outbound-voice-routing.md).
    
    <div>
    

    > [!NOTE]  
    > Capacity refers to the number of ports you need to open to support potential PSTN re-routing.

    
    </div>

</div>

<span> </span>

</div>

</div>

</div>

