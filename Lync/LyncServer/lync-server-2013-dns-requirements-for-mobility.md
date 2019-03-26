---
title: 'Lync Server 2013: DNS requirements for mobility'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: DNS requirements for mobility
ms:assetid: df6962bc-2a16-440e-a333-022ebd14f957
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Hh690040(v=OCS.15)
ms:contentKeyID: 48185624
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# DNS requirements for mobility with Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-11-13_

When you deploy the Lync Server 2013 mobility feature, you can use the new URLs that are available with the Microsoft Lync Server 2013 Autodiscover Service, or you can use your existing Web Services URLs. If you use your existing URLs, users need to manually enter the URLs in their mobile device settings. This option is typically used for troubleshooting. When you use the new URLs, mobile clients can automatically discover Lync Server 2013 resources. When you support automatic discovery, you need to add new Domain Name System (DNS) records. This section describes the DNS records that are required for automatic discovery.

To support automatic discovery, you need to create the following DNS records for each SIP domain:

  - An internal DNS record to support mobile users who connect from within your organization's network

  - An external, or public, DNS record to support mobile users who connect from the Internet

The internal automatic discovery URL should not be addressable from outside your network. The external automatic discovery URL should not be addressable from within your network. However, if you cannot meet this requirement for the external URL, mobile client functionally should not be affected.

The DNS records can be either CNAME records or A (host) records.

**Internal DNS records**

You need to create one of the following internal DNS records:


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Record type</th>
<th>Host name or SRV definition</th>
<th>Resolves to</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CNAME</p></td>
<td><p>lyncdiscoverinternal.&lt;sipdomain&gt;</p></td>
<td><p>Internal Web Services fully qualified domain name (FQDN) for your Director pool, if you have one, or for your Front End pool if you do not have a Director</p></td>
</tr>
<tr class="even">
<td><p>A (host)</p></td>
<td><p>lyncdiscoverinternal.&lt;sipdomain&gt;</p></td>
<td><p>Internal Web Services IP address (virtual IP (VIP) address if you use a load balancer) of your Director pool, if you have one, or of your Front End pool if you do not have a Director</p></td>
</tr>
</tbody>
</table>


**External DNS records**

You need to create one of the following external DNS records:


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Record type</th>
<th>Host name</th>
<th>Resolves to</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CNAME</p></td>
<td><p>lyncdiscover. &lt;sipdomain&gt;</p></td>
<td><p>External Web Services FQDN for your Director pool, if you have one, or for your Front End pool if you do not have a Director</p></td>
</tr>
<tr class="even">
<td><p>A (host)</p></td>
<td><p>lyncdiscover. &lt;sipdomain&gt;</p></td>
<td><p>External or public IP address (VIP address if you use a load balancer) of the reverse proxy</p></td>
</tr>
<tr class="odd">
<td><p>SRV</p></td>
<td><p>_sipfederationtls._tcp. &lt;sipdomain&gt;</p>
<p>Resolves to host (A or AAAA) record for the Access Edge service</p></td>
<td><p>To support Push Notification Service and Apple Push Notification service, you create one SRV record for each SIP domain that has Microsoft Lync Mobile clients.</p>
<div>

> [!IMPORTANT]  
> This requirement applies only to Microsoft Lync Mobile clients on Apple or Microsoft based mobile devices. Andriod and Nokia Symbian devices do not use push notification.


</div></td>
</tr>
</tbody>
</table>


<div>


> [!NOTE]  
> Lyncdiscover, also known as autodiscover, traffic goes through the reverse proxy. SRV record points to a record that resolves through the Access Edge service.



</div>

</div>

<span> </span>

</div>

</div>

</div>

