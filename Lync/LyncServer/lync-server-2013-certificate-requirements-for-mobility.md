---
title: 'Lync Server 2013: Certificate requirements for mobility'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Certificate requirements for mobility
ms:assetid: bb0e97af-cf60-4271-a0ab-654429d884ea
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Hh690044(v=OCS.15)
ms:contentKeyID: 48185251
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Certificate requirements for mobility in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-06-24_

If you deploy the mobility feature and support automatic discovery for mobile clients, you need to include certain subject alternative name entries on certificates to support secure connections from the mobile clients.

You need to include subject alternative name entries for automatic discovery on the following certificates:

  - Director pool

  - Front End pool

  - Reverse proxy

This section describes the subject alternative name entries that are required on your certificates for automatic discovery.

<div>


> [!NOTE]  
> Reissuing certificates by using an internal certificate authority is typically a simple process, but adding multiple subject alternative name entries to public certificates used by the reverse proxy can be expensive. If you have many SIP domains, making the addition of subject alternative names very expensive, you can configure the reverse proxy to use HTTP for the initial Autodiscover Service request, instead of using HTTPS (the default configuration). For details, see <A href="lync-server-2013-technical-requirements-for-mobility.md">Technical requirements for mobility in Lync Server 2013</A>.



</div>

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
<td><p>SAN=lyncdiscoverinternal.&lt;sipdomain&gt;</p></td>
</tr>
<tr class="even">
<td><p>External Autodiscover Service URL</p></td>
<td><p>SAN=lyncdiscover.&lt;sipdomain&gt;</p></td>
</tr>
</tbody>
</table>


<div>


> [!NOTE]  
> Alternatively, you can use SAN=*.&lt;sipdomain&gt;



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
<td><p>SAN=lyncdiscoverinternal.&lt;sipdomain&gt;</p></td>
</tr>
<tr class="even">
<td><p>External Autodiscover Service URL</p></td>
<td><p>SAN=lyncdiscover.&lt;sipdomain&gt;</p></td>
</tr>
</tbody>
</table>


<div>


> [!NOTE]  
> Alternatively, you can use SAN=*.&lt;sipdomain&gt;



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
> You assign this SAN to the certificate assigned to the SSL Listener on the reverse proxy.



</div>

<div>


> [!NOTE]  
> Your reverse proxy listener will have subject alternative names for your external Web Services URL(s) (for example, SAN=lyncwebextpool01.contoso.com, and dirwebexternal.contoso.com if you have deployed the optional Director).



</div>

</div>

<span> </span>

</div>

</div>

</div>

