---
title: 'Lync Server 2013: Configuring support for Autodiscover'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configuring support for Autodiscover
ms:assetid: 3a266456-69a0-4539-ba99-d388b83799a8
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ945622(v=OCS.15)
ms:contentKeyID: 51541463
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring support for Autodiscover in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-01-21_

The Lync Server web services **Autodiscover service** first appeared in the Lync Server 2010 Cumulative Update: November 2011. This update was accompanied by the initial release of Lync Mobile clients. The autodiscover service exposed the mobility services, known as the Mcx service.

The autodiscover service acts as a single location for all clients to request information on what services and features are available, and how to contact the sevices – either by a fully qualified domain name or a web uniform resource locator reference. Autodiscover exposes a number of features, and each client will make requests based on the features that the client can use. For example, a desktop Lync 2013 client will use autodiscvoer to determine the external web services, but will not use the mobility (Mcx) services. To properly define and enable your clients to use the features available to them, the scenarios that allow a client to effectively find and use autodiscover entries should be defined. To use autodoscover, your deployment requires that a reverse proxy publishes the Lync Server web services, that DNS records are configured to resolve DNS queries for the Lync Server autodiscover service and Lync Server web services, and that certificate services are properly configured for your specific scenario.

<div>


> [!TIP]  
> For technical details on what the elements within the autodiscover request/response do, see <A href="lync-server-2013-understanding-autodiscover.md">Understanding Autodiscover in Lync Server 2013</A>.



</div>

The following information and tables define, per scenario, what configurations (if any) you need to implement to provide the full and effective use of the autodiscover service. The information in the following topics is specific to Microsoft Lync Server 2013. If you are looking for guidance on how to plan Mobility for Lync Server 2010, see [http://go.microsoft.com/fwlink/?LinkId=275113](http://go.microsoft.com/fwlink/?linkid=275113). To deploy Mobility for Lync Server 2010, see [http://go.microsoft.com/fwlink/?LinkId=275114](http://go.microsoft.com/fwlink/?linkid=275114)

<div>

## In This Section

  - [Configuring DNS for Autodiscover in Lync Server 2013](lync-server-2013-configuring-dns-for-autodiscover.md)

  - [Configuring certificates for Autodiscover in Lync Server 2013](lync-server-2013-configuring-certificates-for-autodiscover.md)

  - [Configuring a reverse proxy for Autodiscover in Lync Server 2013](lync-server-2013-configuring-a-reverse-proxy-for-autodiscover.md)

  - [Configuring Autodiscover in Lync Server 2013 for hybrid deployments](lync-server-2013-configuring-autodiscover-for-hybrid-deployments.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

