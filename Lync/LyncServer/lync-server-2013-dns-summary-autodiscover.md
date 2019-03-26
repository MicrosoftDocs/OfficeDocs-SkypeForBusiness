---
title: 'Lync Server 2013: DNS summary - Autodiscover'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: DNS summary - Autodiscover
ms:assetid: b336a2ae-0e58-4b74-b606-aedbbd411587
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ945644(v=OCS.15)
ms:contentKeyID: 51541504
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# DNS summary - Autodiscover in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-13_

Autodiscover is a flexible service in that it will accept communication over HTTP or HTTPS. To accomplish this, the domain name system (DNS) and the certificates used by servers that host the Autodiscover service must be configured correctly. Certificate requirements are covered in [Certificate summary - Autodiscover in Lync Server 2013](lync-server-2013-certificate-summary-autodiscover.md).

<div>


> [!IMPORTANT]  
> DNS lookup logic for the Lync Server clients uses a specific order of resolution. You should always include both the lyncdiscoverinternal.&lt;domain&gt; and the lyncdiscover.&lt;domain&gt; in your DNS. Excluding the lyncdiscoverinternal.&lt;domain&gt; record will cause internal clients to fail to connect to the intended services or receive the incorrect Autodiscover response.



</div>

### Internal DNS Records

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
<td><p>Lyncdiscoverinternal.&lt;internal domain name&gt;</p></td>
<td><p>Internal Web Services FQDN for your Director pool, if you have one, or for your Front End pool if you do not have a Director.</p></td>
</tr>
<tr class="even">
<td><p>A (host, if IPv6, AAAA)</p></td>
<td><p>lyncdiscoverinternal.&lt;internal domain name&gt;</p></td>
<td><p>Internal Web Services IP address (virtual IP (VIP) address if you use a load balancer) of your Director pool, if you have one, or of your Front End pool if you do not have a Director.</p></td>
</tr>
</tbody>
</table>


You need to create one of the following external DNS records:

### External DNS Records

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
<td><p>lyncdiscover.&lt;sipdomain&gt;</p></td>
<td><p>External Web Services FQDN for your Director pool, if you have one, or for your Front End pool if you do not have a Director.</p></td>
</tr>
<tr class="even">
<td><p>A (host, if IPv6, AAAA)</p></td>
<td><p>lyncdiscover.&lt;sipdomain&gt;</p></td>
<td><p>External or public IP address of the reverse proxy.</p></td>
</tr>
</tbody>
</table>


<div>


> [!NOTE]  
> External traffic goes through the reverse proxy.



</div>

<div>


> [!NOTE]  
> Mobile device clients do not support multiple Secure Sockets Layer (SSL) certificates from different domains. Therefore, CNAME redirection to different domains is not supported over HTTPS. For example, a DNS CNAME record for lyncdiscover.contoso.com that redirects to an address of director.contoso.net is not supported over HTTPS. In such a topology, a mobile device client needs to use HTTP for the first request, so that the CNAME redirection is resolved over HTTP. Subsequent requests then use HTTPS. To support this scenario, you need to configure your reverse proxy with a web publishing rule for port 80 (HTTP). For details, see "To create a web publishing rule for port 80" in <A href="lync-server-2013-configuring-the-reverse-proxy-for-mobility.md">Configuring the reverse proxy for mobility in Lync Server 2013</A>. CNAME redirection to the same domain is supported over HTTPS. In this case, the destination domain's certificate covers the originating domain.



</div>

<div>

## See Also


[Configuring the reverse proxy for mobility in Lync Server 2013](lync-server-2013-configuring-the-reverse-proxy-for-mobility.md)  


[Certificate summary - Autodiscover in Lync Server 2013](lync-server-2013-certificate-summary-autodiscover.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

