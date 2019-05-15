---
title: Lync Server 2013 wildcard certificate support
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Wildcard certificate support
ms:assetid: 0bae2aa8-b6dc-46f5-a3be-3fe7581809d4
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Hh202161(v=OCS.15)
ms:contentKeyID: 48183382
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Wildcard certificate support in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-21_

Lync Server 2013 uses certificates to provide communications encryption and server identity authentication. In some cases, such as web publishing through the reverse proxy, strong subject alternative name (SAN) entry matching to the fully qualified domain name (FQDN) of the server presenting the service is not required. In these cases, you can use certificates with wildcard SAN entries (commonly known as “wildcard certificates”) to reduce the cost of a certificate requested from a public certification authority and to reduce the complexity of the planning process for certificates.

<div>


> [!WARNING]  
> To retain the functionality of unified communications (UC) devices (for example, desk phones), you should test the deployed certificate carefully to ensure that devices function properly after you implement a wildcard certificate.



</div>

There is no support for a wildcard entry as the subject name (also referred to as the common name or CN) for any role. The following server roles are supported when using wildcard entries in the SAN:

  - <span></span>  
    **Reverse proxy.**   Wildcard SAN entry is supported for Simple URL (meet and dialin) publishing certificate.

  - <span></span>  
    **Reverse proxy.**   Wildcard SAN entry is supported for the SAN entries for LyncDiscover on the publishing certificate.

  - <span></span>  
    **Director.**   Wildcard SAN entry is supported for Simple URLs (meet and dialin) and for SAN entries for LyncDiscover and LyncDiscoverInternal in Director web components.

  - <span></span>  
    **Front End Server (Standard Edition) and Front End pool (Enterprise Edition).** Wildcard SAN entry is supported for Simple URLs (meet and dialin) and for SAN entries for LyncDiscover and LyncDiscoverInternal in Front End web components.

  - <span></span>  
    **Exchange Unified Messaging (UM).**   The server does not use SAN entries when deployed as a stand-alone server.

  - <span></span>  
    **Microsoft Exchange Server Client Access server.**   Wildcard entries in the SAN are supported for internal and external clients.

  - <span></span>  
    **Exchange Unified Messaging (UM) and Microsoft Exchange Server Client Access server on same server.**   Wildcard SAN entries are supported.

Server roles that are not addressed in this topic:

  - Internal server roles (including, but not limited to the Mediation Server, Archiving and Monitoring Server, Survivable Branch Appliance, or Survivable Branch Server)

  - External Edge Server interfaces

  - Internal Edge Server
    
    <div>
    

    > [!NOTE]  
    > For the internal Edge Server interface, a wildcard entry can be assigned to the SAN, and is supported. The SAN on the internal Edge Server is not queried, and a wildcard SAN entry is of limited value.

    
    </div>

For details about certificate configurations, including the use of wildcards in certificates, see the following topics:

  - [Certificate requirements for internal servers in Lync Server 2013](lync-server-2013-certificate-requirements-for-internal-servers.md)

  - [Certificate requirements for external user access in Lync Server 2013](lync-server-2013-certificate-requirements-for-external-user-access.md)

  - [Certificate summary - DNS and HLB load balanced in Lync Server 2013](lync-server-2013-certificate-summary-dns-and-hlb-load-balanced.md)

  - [Certificate summary - Single Director in Lync Server 2013](lync-server-2013-certificate-summary-single-director.md)

  - [Certificate summary - Scaled Director pool, hardware load balancer in Lync Server 2013](lync-server-2013-certificate-summary-scaled-director-pool-hardware-load-balancer.md)

  - [Certificate summary - Reverse proxy in Lync Server 2013](lync-server-2013-certificate-summary-reverse-proxy.md)

  - [Guidelines for integrating on-premises Unified Messaging and Lync Server 2013](lync-server-2013-guidelines-for-integrating-on-premises-unified-messaging.md)

For details about configuring certificates for Exchange, including the use of wildcards, see the Exchange 2013 product documentation.

</div>

<span> </span>

</div>

</div>

</div>

