---
title: Lync Server 2013 Active Directory support
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Active Directory support
ms:assetid: 28ed9ac4-586d-4803-ad45-99c4fa793f54
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425756(v=OCS.15)
ms:contentKeyID: 48183679
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Active Directory support in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-12-04_

The Active Directory Domain Services on-premises topologies that are supported by Lync Server 2013 are as follows:

  - Single forest with single domain

  - Single forest with a single tree and multiple domains

  - Single forest with multiple trees and disjoint namespaces

  - Multiple forests in a central forest topology

  - Multiple forests in a resource forest topology

<div>


> [!NOTE]  
> Lync Server 2013 does not support single-label domains. For example, a forest with a root domain named <STRONG>contoso.local</STRONG> is supported, but a single-label root domain named <STRONG>local</STRONG> is not supported. For details, see Microsoft Knowledge Base article 300684, "Information about configuring Windows for domains with single-label DNS names," at <A href="http://go.microsoft.com/fwlink/p/?linkid=143752">http://go.microsoft.com/fwlink/p/?linkId=143752</A>.



</div>

<div>


> [!NOTE]  
> Lync Server 2013 does not support renaming domains. If you need to rename a domain where Lync Server is deployed, you need to first uninstall Lync Server, then rename the domain, and then reinstall Lync Server.



</div>

For details about supported topologies and requirements for on-premises deployments, see [Active Directory Domain Services requirements, support, and topologies in Lync Server 2013](lync-server-2013-active-directory-domain-services-requirements-support-and-topologies.md) in the Planning documentation.

</div>

<span> </span>

</div>

</div>

</div>

