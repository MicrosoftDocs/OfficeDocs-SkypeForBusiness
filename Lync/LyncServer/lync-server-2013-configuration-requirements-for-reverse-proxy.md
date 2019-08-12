---
title: 'Lync Server 2013: Configuration requirements for reverse proxy'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configuration requirements for reverse proxy
ms:assetid: c37d688a-28e4-4822-80cc-6add59c71052
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ945651(v=OCS.15)
ms:contentKeyID: 51541518
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuration requirements for reverse proxy in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-05_

Lync Server 2013 imposes a few requirements on communications from the external client that are then passed on to the external Web services hosted on the Director, Director pool, Front End Server or Front End pool. The reverse proxy is also responsible for publishing the Office Web Apps Server, if you are offering conferencing to your users.

<div>


> [!NOTE]  
> Lync Server 2013 does not specify a particular reverse proxy that you must use. Lync Server 2013 only defines operational requirements that the reverse proxy must be able to do. Typically, the reverse proxy that you already have deployed in your infrastructure may be able to meet the requirements.



</div>

<div>

## Reverse Proxy Requirements

The functional operations that Lync Server 2013 expect a reverse proxy to perform are:

  - Use secure socket layer (SSL) and transport layer security (TLS) implemented by using certificates acquired from a public certification authority to connect to the published external Web services of the Director, Director pool, Front End Server or Front End pool. The Director and the Front End Server can be in a load-balanced pool by using hardware load balancers.

  - Able to publish internal Web sites using certificates for encryption, or publish them over an unencrypted means, if needed.

  - Able to publish an internally hosted web site externally by using a fully qualified domain name (FQDN).

  - Able to publish all contents of the hosted web site. By default, you can use the **/\*** directive, which is recognized by most web servers to mean "Publish all content on the web server." You can also modify the directive—for example, **/Uwca/\***, which means "Publish all content under the virtual directory Ucwa."

  - Must be configurable to require Secure Sockets Layer (SSL) and/or Transport Layer Security (TLS) connections with clients that request content from a published website.

  - Must accept certificates with subject alternative name (SAN) entries.

  - Must be able to allow binding of a certificate to a listener or interface through which the external web services FQDN will resolve. Listener configurations are preferable to interfaces. Many listeners can be configured on a single interface.

  - Must allow for the configuration of host header handling. Often, the original host header sent by the requesting client must be passed transparently, instead of being modified by the reverse proxy.

  - Bridging of SSL and TLS traffic from one externally defined port (for example, TCP 443) to another defined port (for example, TCP 4443). The reverse proxy may decrypt the packet on receipt and then reencrypt the packet on sending.

  - Bridging of unencrypted TCP traffic from one port (for example, TCP 80) to another (for example, TCP 8080).

  - Allow configuration of, or accept, NTLM authentication, No authentication and Pass-through authentication.

</div>

</div>

<span> </span>

</div>

</div>

</div>

