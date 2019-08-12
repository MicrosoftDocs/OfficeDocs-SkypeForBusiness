---
title: 'Lync Server 2013: Failing over the Edge pool used for XMPP federation'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Failing over the Edge pool used for XMPP federation
ms:assetid: 587e7829-a26b-46f8-8aad-b78a7b325b55
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ688065(v=OCS.15)
ms:contentKeyID: 49733659
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Failing over the Edge pool used for XMPP federation in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-19_

In your organization, there is one Edge pool designated as the pool to use for XMPP federation. If this pool goes down, you must fail over XMPP federation to use a different Edge pool before XMPP federation can work again.

When you first install Edge pools and enable XMPP Federation, you can simplify the disaster recovery process by setting up external DNS SRV records for all of your Edge pools for XMPP federation, instead of just one. Each of these SRV records must have a different priority set. All XMPP federation traffic goes through the pool with the SRV record with the highest priority. For more information on enabling and setting up XMPP federation, see [Setting up XMPP federation in Lync Server 2013](lync-server-2013-setting-up-xmpp-federation.md).

In the following procedure, EdgePool1 is the pool which originally hosted XMPP federation, and EdgePool2 is the pool which will now host XMPP federation.

<div>

## Failing Over the Edge Pool Used for XMPP Federation

1.  If you don’t already have another Edge pool deployed (besides the one which is currently down), deploy that pool. For details, see [Deploying external user access in Lync Server 2013](lync-server-2013-deploying-external-user-access.md).

2.  On each Edge Server in the new Edge pool which will now host XMPP federation (EdgePool2), run the following cmdlet:
    
        Stop-CsWindowsService

3.  Run the following cmdlet to repoint the XMPP federation route to EdgePool2:
    
        Set-CsSite Site2 -XmppExternalFederationRoute EdgeServer2.contoso.com
    
    In this example, Site2 is the site containing the Edge pool which will now host the XMPP federation route, and EdgeServer2.contoso.com is the FQDN of an Edge Server in that pool.

4.  On the external DNS server, change the DNS A record for XMPP federation to point to EdgeServer2.contoso.com.

5.  If you do not already have a DNS SRV record for XMPP federation which resolves to the Edge pool which will now host XMPP federation, you must add it, as in the following example. This SRV record must have a port value of 5269.
    
        _xmpp-server._tcp.contoso.com

6.  Verify that the Edge pool which will now host XMPP federation has port 5269 open externally.

7.  Start the services on all Edge Servers in the Edge pool which will now host XMPP federation:
    
        Start-CsWindowsService

</div>

</div>

<span> </span>

</div>

</div>

</div>

