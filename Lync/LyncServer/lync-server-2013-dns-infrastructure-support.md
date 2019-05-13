---
title: 'Lync Server 2013: DNS infrastructure support'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Domain Name System (DNS) infrastructure support
ms:assetid: 37777c16-94ce-436d-b517-bcf53a564513
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425850(v=OCS.15)
ms:contentKeyID: 48183878
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# DNS infrastructure support in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-08_

Lync Server 2013 requires Domain Name System (DNS) and uses it in the following ways:

  - To discover internal servers or pools for server-to-server communications.

  - To enable clients to discover the Front End pool or Standard Edition server used for various SIP transactions.

  - To associate the simple URLs for conferences with the servers hosting those conferences.

  - To enable external servers and clients to connect to Edge Servers or the HTTP reverse proxy for instant messaging (IM) or conferencing.

  - To enable unified communications (UC) devices that are not logged in to discover the Front End pool or Standard Edition server running Device Update Web service, obtain updates, and send logs.

  - To enable mobile clients to automatically discover Web Services resources without requiring users to manually enter URLs in device settings.

  - For DNS load balancing.

<div>


> [!NOTE]  
> Lync Server 2013 does not support internationalized domain names (IDNs).



</div>

<div>


> [!IMPORTANT]  
> The name you specify must be identical to the computer name configured on the server. By default, the computer name of a computer that is not joined to a domain is a short name, not a fully qualified domain name (FQDN). Topology Builder uses FQDNs, not short names. So, you must configure a DNS suffix on the name of the computer to be deployed as an Edge Server that is not joined to a domain. <STRONG>Use only standard characters</STRONG> (including A–Z, a–z, 0–9, and hyphens) when assigning FQDNs of your Lync Servers, Edge Servers, and pools. Do not use Unicode characters or underscores. Nonstandard characters in an FQDN are often not supported by external DNS and public CAs (that is, when the FQDN must be assigned to the SN in the certificate).



</div>

</div>

<span> </span>

</div>

</div>

</div>

