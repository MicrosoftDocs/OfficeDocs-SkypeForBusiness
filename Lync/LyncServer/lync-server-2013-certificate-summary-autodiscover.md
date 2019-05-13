---
title: 'Lync Server 2013: Certificate summary - Autodiscover'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Certificate summary - Autodiscover
ms:assetid: 16ac96bb-882a-4141-b75c-9530637548d9
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ945616(v=OCS.15)
ms:contentKeyID: 51541451
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Certificate summary - Autodiscover in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-14_

The Lync Server 2013 Autodiscover Service runs on the Director and Front End pool servers, and when published in DNS, can be used by Lync clients to locate server and user services. If you are upgrading from Lync Server 2010 and did not deploy Mobility, before clients can use automatic discovery, you must modify certificate subject alternative name lists on any Director and Front End Server running the Autodiscover Service. In addition, it may be necessary to modify the subject alternative name lists on certificates used for external web service publishing rules on reverse proxies.

The decision about whether to use subject alternative name lists on reverse proxies is based on whether you publish the Autodiscover Service on port 80 or on port 443:

  - **Published on port 80**   No certificate changes are required if the initial query to the Autodiscover Service occurs over port 80. This is because mobile devices running Lync will access the reverse proxy on port 80 externally and then be bridged to a Director or Front End Server on port 8080 internally. For details, see the "Initial Autodiscover Process Using Port 80" section [Technical requirements for mobility in Lync Server 2013](lync-server-2013-technical-requirements-for-mobility.md).

  - **Published on port 443**   The subject alternative name list on certificates used by the external web services publishing rule must contain a *lyncdiscover.\<sipdomain\>* entry for each SIP domain within your organization.
    
    <div>
    

    > [!IMPORTANT]  
    > We highly recommend using HTTPS over HTTP. HTTPS uses certificates to encrypt traffic. HTTP does not provide for encryption, and any data sent will be plain text.

    
    </div>

Reissuing certificates by using an internal certificate authority is typically a simple process. But for public certificates used on the web service publishing rule, adding multiple subject alternative name entries can become expensive. To work around this issue, we support the initial automatic discovery connection over port 80, which is then redirected to port 8080 on the Director or Front End Server.

<div>


> [!NOTE]  
> If your Lync Server 2013 infrastructure uses internal certificates that are issued from an internal certification authority (CA) and you plan to support mobile devices connecting wirelessly, either the root certificate chain from the internal CA must be installed on the mobile devices or you must change to a public certificate on your Lync Server 2013 infrastructure.



</div>

This topic describes the added subject alternative names required for the Director, Front End Server and reverse proxy. Only the added subject alternative names (SAN) are referenced. Refer to the planning sections for guidance on the other entries on certificates. For details, see [Scenarios for the Director in Lync Server 2013](lync-server-2013-scenarios-for-the-director.md), [Scenarios for external user access in Lync Server 2013](lync-server-2013-scenarios-for-external-user-access.md), and [Scenarios for reverse proxy in Lync Server 2013](lync-server-2013-scenarios-for-reverse-proxy.md).

The following tables define the Autodiscover SAN entries for the Director pool, the Front End pool, and the reverse proxy:

### Director Pool Certificate Requirements

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Description</th>
<th>Subject alternative name entry</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Internal Autodiscover Service URL</p></td>
<td><p>SAN=lyncdiscoverinternal.&lt;internal domain name&gt;</p></td>
</tr>
<tr class="even">
<td><p>External Autodiscover Service URL</p></td>
<td><p>SAN=lyncdiscover.&lt;sipdomain&gt;</p></td>
</tr>
</tbody>
</table>


<div>


> [!NOTE]  
> You assign the newly updated certificate with the new SAN entry to the Default certificate. Alternatively, you can use SAN=*.&lt;sipdomain&gt;.



</div>

### Front End Pool Certificate Requirements

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Description</th>
<th>Subject alternative name entry</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Internal Autodiscover Service URL</p></td>
<td><p>SAN=lyncdiscoverinternal.&lt;internal domain name&gt;</p></td>
</tr>
<tr class="even">
<td><p>External Autodiscover Service URL</p></td>
<td><p>SAN=lyncdiscover.&lt;sipdomain&gt;</p></td>
</tr>
</tbody>
</table>


<div>


> [!NOTE]  
> You assign the newly updated certificate with the new SAN entry to the Default certificate. Alternatively, you can use SAN=*.&lt;sipdomain&gt;



</div>

### Reverse Proxy (Public CA) Certificate Requirements

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Description</th>
<th>Subject alternative name entry</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>External Autodiscover Service URL</p></td>
<td><p>SAN=lyncdiscover.&lt;sipdomain&gt;</p></td>
</tr>
</tbody>
</table>


<div>


> [!NOTE]  
> You assign the newly updated certificate with the new SAN entry to the SSL Listener on the reverse proxy.



</div>

</div>

<span> </span>

</div>

</div>

</div>

