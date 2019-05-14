---
title: Lync Server 2013 certificate infrastructure support
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Certificate infrastructure support
ms:assetid: 47aa5c95-eb60-4d4b-81d5-7fdaef1a1145
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425950(v=OCS.15)
ms:contentKeyID: 48184047
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Certificate infrastructure support in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-11-07_

Lync Server 2013 requires a public key infrastructure (PKI) to support Transport Layer Security (TLS) and mutual TLS (MTLS) connections. By default, Lync Server 2013 is configured to use TLS for client-to-server connections. MTLS is used for connections between servers.

MTLS certificates must be issued by trusted certification authorities (CAs) for Lync Server 2013. Lync Server supports certificates that are issued from the following CAs:

  - Certificates issued from an internal CA:
    
      - The Windows Server 2003 operating system CA
    
      - The Windows Server 2008 operating system CA
    
      - The Windows Server 2008 R2 operating system CA
    
      - The Windows Server 2012 operating system CA
    
      - The Windows Server 2012 R2 operating system CA

  - Certificates issued from a public CA

Communication with other applications and servers, such as Exchange 2013, requires a certificate that is supported by the other applications and products. For the 2013 release, Lync Server 2013 and other Microsoft server products, including Exchange 2013 and SharePoint Server, support the Open Authorization (OAuth) protocol for server-to-server authentication and authorization. For details, see [Managing server-to-server authentication (OAuth) and partner applications in Lync Server 2013](lync-server-2013-managing-server-to-server-authentication-oauth-and-partner-applications.md) in the Deployment documentation or the Operations documentation.

For connections from clients running Windows 7 operating system, Windows Server 2008 R2 operating system, and Microsoft Office Communicator 2007 Phone Edition, Lync Server 2013 includes support for (but does not require) certificates signed using the SHA-256 cryptographic hash function. To support external access using SHA-256, the external certificate is issued by a public CA using SHA-256.

For details about certificate requirements, see [Certificate infrastructure requirements for Lync Server 2013](lync-server-2013-certificate-infrastructure-requirements.md) in the Planning documentation. For details about use of wildcards with certificates, see [Wildcard certificate support in Lync Server 2013](lync-server-2013-wildcard-certificate-support.md) in the Supportability documentation.

</div>

<span> </span>

</div>

</div>

</div>

