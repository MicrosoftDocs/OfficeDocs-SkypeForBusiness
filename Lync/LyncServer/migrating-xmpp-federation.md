---
title: Migrating XMPP federation
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Migrating XMPP federation
ms:assetid: b8d2b4b9-d0ed-4b48-820a-2c257fbdd2fb
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ721861(v=OCS.15)
ms:contentKeyID: 49733794
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Migrating XMPP federation

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-19_

Previous versions of Lync Server and Office Communications Server provided an extensible messaging and presence protocol (XMPP) gateway that could be deployed as a separate server role to allow federating with XMPP deployments. In Lync Server 2013, the XMPP functionality can be deployed as a feature. XMPP functionality is installed in two parts: as an XMPP proxy that runs on the Lync Server 2013 Edge Server, and the XMPP Gateway that runs on the Lync Server 2013 Front End Server.

From a migration perspective, a Lync Server user account can be moved to a Lync Server 2013 pool and continue to use the legacy XMPP gateway. This is possible only when the XMPP federated partner is not configured in Lync Server 2013.

In summary, if Lync Server 2010 has been deployed with the Office Communications Server 2007 R2 XMPP Gateway and XMPP federation has been enabled for legacy Lync Server 2010 users, to migrate the XMPP federation to Lync Server 2013:

1.  Deploy a Lync Server 2013 pool.

2.  Deploy a Lync Server 2013 Edge server.

3.  Move all users to the Lync Server 2013 pool

4.  Create XMPP access policies and certificates for the Edge Server.

5.  Enable XMPP federation in Lync Server 2013. 

6.  Update the DNS entries to point to the Lync Server 2013 XMPP Gateway.

</div>

<span> </span>

</div>

</div>

</div>

