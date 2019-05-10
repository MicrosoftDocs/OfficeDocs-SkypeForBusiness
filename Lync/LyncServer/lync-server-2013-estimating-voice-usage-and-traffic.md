---
title: 'Lync Server 2013: Estimating voice usage and traffic'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Estimating voice usage and traffic
ms:assetid: 621b08fb-f894-4d91-ac38-e443401b098b
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398439(v=OCS.15)
ms:contentKeyID: 48184332
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Estimating voice usage and traffic for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-08-07_

The Microsoft Lync Server 2013, Planning Tool uses the following metric to estimate user traffic at each site and the number of ports that are required to support that traffic.

  - <span></span>  
    For **Light traffic** (one PSTN call per user per hour), figure 15 users per port.

  - <span></span>  
    For **Medium traffic** (2 PSTN calls per user per hour), figure 10 users per port.

  - <span></span>  
    For **Heavy traffic** (3 or more PSTN per user calls per hour), figure 5 users per port.

The number of ports in turn determines the number of Mediation Servers and gateways that will be required. The public switched telephone network (PSTN) gateways that most organizations consider deploying range in size from 2 ports to as many as 960 ports. (There are even larger gateways, but these are used mainly by telephony service providers.)

For example, an organization with 10,000 users and medium traffic would require 1000 ports. The number of gateways required would equal the total number of ports required as determined by the total capacity of the gateways.

</div>

<span> </span>

</div>

</div>

</div>

