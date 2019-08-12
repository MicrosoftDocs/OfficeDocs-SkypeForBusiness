---
title: 'Lync Server 2013: Domain Name System (DNS) requirements'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Domain Name System (DNS) requirements
ms:assetid: 586cf18e-0080-4eb1-aee5-56843277fdfc
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398386(v=OCS.15)
ms:contentKeyID: 48184194
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Domain Name System (DNS) requirements for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-06-18_

To deploy Lync Server, you must create Domain Name System (DNS) records that enable the discovery of clients and servers, and, optionally, support for automatic client sign-in if your organization wants to support it.

Lync Server uses DNS in the following ways:

  - To discover internal servers or pools for server-to-server communications.

  - To allow clients to discover the Front End pool or Standard Edition server used for various SIP transactions.

  - To allow unified communications (UC) devices that are not logged on to discover the Front End pool or Standard Edition server running Device Update Web Service, obtain updates, and send logs.

  - To allow external servers and clients to connect to Edge Servers or the HTTP reverse proxy for instant messaging (IM) or conferencing.

  - To allow external UC devices to connect to Device Update Web service through Edge Servers or the HTTP reverse proxy and obtain updates.

  - To allow mobile clients to automatically discover Web Services resources without requiring users to manually enter URLs in device settings.

<div>

## In This Section

  - [Determine DNS requirements for Lync Server 2013](lync-server-2013-determine-dns-requirements.md)

  - [DNS requirements for Front End pools in Lync Server 2013](lync-server-2013-dns-requirements-for-front-end-pools.md)

  - [DNS requirements for Standard Edition servers in Lync Server 2013](lync-server-2013-dns-requirements-for-standard-edition-servers.md)

  - [DNS requirements for simple URLs in Lync Server 2013](lync-server-2013-dns-requirements-for-simple-urls.md)

  - [DNS requirements for automatic client sign-in in Lync Server 2013](lync-server-2013-dns-requirements-for-automatic-client-sign-in.md)

  - [DNS requirements for mobility with Lync Server 2013](lync-server-2013-dns-requirements-for-mobility.md)

  - [DNS load balancing in Lync Server 2013](lync-server-2013-dns-load-balancing.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

