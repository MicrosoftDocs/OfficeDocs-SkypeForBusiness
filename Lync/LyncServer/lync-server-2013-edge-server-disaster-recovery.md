---
title: 'Lync Server 2013: Edge Server disaster recovery'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Edge Server disaster recovery
ms:assetid: 05ec8d26-d167-4a6f-a966-a1f8873cf974
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ687960(v=OCS.15)
ms:contentKeyID: 49733545
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Edge Server disaster recovery in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-03-12_

As with other server roles, the best way for you to provide high availability for your Edge Servers is to deploy multiple Edge servers in pools in each site. If one Edge Server goes down, the other servers in the pool will continue to provide Edge services.

To enable disaster recovery procedures, you must have separate Edge Server pools deployed at separate sites. You do not need to explicitly pair Edge pools together as you do with Front End pools, but having multiple Edge pools still provides the availability to carry on if one entire Edge pool goes down. The following sections provide details on disaster recovery for the various functions of Edge Servers.

<div>

## Remote Access

If you have multiple sites, each with a pool of Edge servers, and one entire Edge pool fails, the remote access services will continue to function without needing administrator action. When creating Edge pools in different sites, you cannot use the same FQDN. Each Edge pool must have unique FQDNs (internal and external). The Edge pools do not use reverse proxy publishing rules to talk to the Front End servers. Automatic failover occurs when the client re-queries the remote access DNS service records, and remote users are routed to the Edge servers in another site. The client attempts each external Edge FQDN according to the priority of the DNS SRV records.

<div>


> [!NOTE]  
> For failover to work smoothly, ensure that the firewall allows the Front End servers from every pool to communicate with all Edge servers.



</div>

</div>

<div>

## Federation

For federation relationships with other organizations running Lync Server, inbound federation requests will continue to work as long as you have solutions like Geo-DNS GTM. It’s important to understand that federation failover does not provide failover with priority in SRV records. A solution provided earlier can help you provide disaster recovery capabilities for inbound federation.

Outbound federation is always set up through one published Edge pool or Edge Server in the organization. If this Edge pool has gone down, you must use Topology Builder to change the outbound federation route to use an Edge pool which is still running. For details, see [Failing over the Edge pool used for Lync Server federation in Lync Server 2013](lync-server-2013-failing-over-the-edge-pool-used-for-lync-server-federation.md)

</div>

<div>

## XMPP Federation

For XMPP federation, both outbound and inbound traffic will fail if the Edge pool which is designated as the XMPP federation gateway goes down. To make XMPP federation work again, you must change XMPP federation to use a different Edge pool. For details, see [Failing over the Edge pool used for XMPP federation in Lync Server 2013](lync-server-2013-failing-over-the-edge-pool-used-for-xmpp-federation.md).

</div>

<div>

## Edge Pool Fails But Front End Pool Is Still Running

If an Edge pool fails at a site, but the Front End pool at that site is still running, you will need to change the Front End pool to use a different Edge pool at a different site while that first Edge pool is down. For more information, see [Changing the Edge pool associated with a Front End pool in Lync Server 2013](lync-server-2013-changing-the-edge-pool-associated-with-a-front-end-pool.md).

</div>

</div>

<span> </span>

</div>

</div>

</div>

