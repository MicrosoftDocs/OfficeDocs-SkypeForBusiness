---
title: 'Lync Server 2013: Prerequisites for enabling Kerberos authentication'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Prerequisites for enabling Kerberos authentication
ms:assetid: 3f276a21-7476-4bc0-9fd1-59e844d2e9c1
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425909(v=OCS.15)
ms:contentKeyID: 48183945
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Prerequisites for enabling Kerberos authentication in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

Before enabling Kerberos authentication, make sure that you complete all prerequisite configuration and infrastructure preparations:

  - Active Directory schema is extended for Lync Server 2013.

  - Active Directory forest preparation is completed for Lync Server 2013.

  - Active Directory domain preparation is completed for Lync Server 2013.

  - Central Management store is successfully installed and available.

  - The topology has been created and published by using Topology Builder.

  - Servers and roles that require Web Services have been defined and deployed, including Front End Servers, Standard Edition servers, and Directors.

  - Internet Information Services (IIS) is configured and deployed with the recommended role services to support Web Services in Lync Server 2013.

After the prerequisites have been met, you should be ready to create one or more accounts for Web Services to use for Kerberos authentication for your deployment. At a minimum, you need to create one Kerberos authentication account for each deployment. However, you can create an account for each site to provide local Kerberos authentication at the site. You can only specify one Kerberos authentication account per site.

</div>

<span> </span>

</div>

</div>

</div>

