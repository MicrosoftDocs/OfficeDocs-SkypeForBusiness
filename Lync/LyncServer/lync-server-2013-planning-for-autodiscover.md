---
title: 'Lync Server 2013: Planning for Autodiscover'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Planning for Autodiscover
ms:assetid: 51f1ff94-1d64-4e6d-a878-b86fa07edc2d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ945628(v=OCS.15)
ms:contentKeyID: 51541474
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Planning for Autodiscover in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-16_

Autodiscover was introduced for Lync Server in the Cumulative Update for Lync Server 2010: November 2011. The primary purpose for this initial implementation of Autodiscover was to provide a means for Lync Mobile to locate the Mobility service (Mcx). The Autodiscover service in Lync Server 2013 is now a service used by all clients to locate server and user services. The Microsoft Lync Server 2013 Autodiscover service runs on Directors and Front End Servers.

<div>


> [!TIP]  
> For a more technical understanding of Autodiscover and what is communicated to clients, see <A href="lync-server-2013-understanding-autodiscover.md">Understanding Autodiscover in Lync Server 2013</A>.<BR>Mobility is still a distinct scenario and the Mobility services still require some special planning. For additional details, see <A href="lync-server-2013-planning-for-mobility.md">Planning for mobility in Lync Server 2013</A>.



</div>

When Autodiscover was introduced in Lync Server 2010, there were compromises that needed to be made in order to implement a service that required potential certificate changes to existing server deployments. Autodiscover could be used over port TCP 443 for HTTPS or over port TCP 80 for HTTP. If the decision was made to use HTTPS, certificates on reverse proxies, Directors, and Front End Servers needed to be reissued in order to accommodate the required `lyncdiscover.<domain>` and `lyncdiscoverinternal.<domain>` DNS records. If the decision was to use HTTP, the reissue of certificates could be avoided by using DNS CNAME (or alias) records to use existing names on the certificates. Using HTTP did mean that the initial communications were unencrypted.

Because Lync Server 2013 uses Autodiscover for all clients, the main scenario is to use HTTPS exclusively and to create certificates with lyncdiscover.\<domain\> as part of the configuration of reverse proxies, Directors and Front End Servers. If you are implementing Autodiscover into an upgraded deployment from Lync Server 2010, you may want to use HTTP to avoid reissuing certificates. Guidance for both scenarios is provided in the following sections.

<div>


> [!IMPORTANT]  
> The subject alternative name list on certificates used by the external web services publishing rule must contain a <EM>lyncdiscover.&lt;sipdomain&gt;</EM> entry for each SIP domain within your organization. For details about the subject alternative name entries that are required for Directors, Front End Servers, and reverse proxies, see <A href="lync-server-2013-certificate-summary-autodiscover.md">Certificate summary - Autodiscover in Lync Server 2013</A>.



</div>

<div>

## In This Section

  - [Certificate summary - Autodiscover in Lync Server 2013](lync-server-2013-certificate-summary-autodiscover.md)

  - [Port summary - Autodiscover in Lync Server 2013](lync-server-2013-port-summary-autodiscover.md)

  - [DNS summary - Autodiscover in Lync Server 2013](lync-server-2013-dns-summary-autodiscover.md)

  - [Hybrid and split-domain - Autodiscover in Lync Server 2013](lync-server-2013-hybrid-and-split-domain-autodiscover.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

