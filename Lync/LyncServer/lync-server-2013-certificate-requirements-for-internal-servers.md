---
title: 'Lync Server 2013: Certificate requirements for internal servers'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Certificate requirements for internal servers
ms:assetid: 0444cdbd-538c-43b1-b9a1-9d7d6cf818d6
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398094(v=OCS.15)
ms:contentKeyID: 48183270
ms.date: 02/17/2017
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Certificate requirements for internal servers in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2017-02-17_

Internal servers that are running Lync Server and that require certificates include Standard Edition server, Enterprise Edition Front End Server, Mediation Server, and Director. The following table shows the certificate requirements for these servers. You can use the Lync Server certificate wizard to request these certificates.

<div>


> [!TIP]  
> Wildcard certificates are supported for the subject alternative names associated with the simple URLs on the Front End pool, Front End Server, or Director. For details about wildcard certificate support, see <A href="lync-server-2013-wildcard-certificate-support.md">Wildcard certificate support in Lync Server 2013</A>.



</div>

Although an internal enterprise certification authority (CA) is recommended for internal servers, you can also use a public CA. For a list of public CAs that provide certificates that comply with specific requirements for unified communications (UC) certificates and have partnered with Microsoft to ensure they work with the Lync Server Certificate Wizard, see article Microsoft Knowledge Base 929395, "Unified Communications Certificate Partners for Exchange Server and for Communications Server," at [https://go.microsoft.com/fwlink/p/?linkId=202834](https://go.microsoft.com/fwlink/p/?linkid=202834).

Communication with other applications and servers, such as Exchange 2013, requires a certificate that is supported by the other applications and products. For the 2013 release, Lync Server 2013 and other Microsoft server products, including Exchange 2013 and SharePoint Server, support the Open Authorization (OAuth) protocol for server-to-server authentication and authorization. For details, see [Managing server-to-server authentication (OAuth) and partner applications in Lync Server 2013](lync-server-2013-managing-server-to-server-authentication-oauth-and-partner-applications.md) in the Deployment documentation or the Operations documentation.

For connections from clients running Windows 7 operating system, Windows Server 2008 operating system, Windows Server 2008 R2 operating system, Windows Vista operating system, and Microsoft Lync Phone Edition, Lync Server 2013 includes support for (but does not require) certificates signed using the SHA-256 cryptographic hash function. To support external access using SHA-256, the external certificate is issued by a public CA using SHA-256.

The following tables show certificate requirements by server role for Front End pools and Standard Edition servers. All these are standard web server certificates, private key, non-exportable.

Note that server enhanced key usage (EKU) is automatically configured when you use the certificate wizard to request certificates.

<div>


> [!NOTE]  
> Each certificate Friendly Name must be unique in the computer store.



</div>

<div>


> [!NOTE]  
> If you have configured sipinternal.contoso.com or sipexternal.contoso.com in your DNS, you will need to add them in the certificate’s Subject Alternative Name.



</div>

### Certificates for Standard Edition Server

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Certificate</th>
<th>Subject name/ Common name</th>
<th>Subject alternative name</th>
<th>Example</th>
<th>Comments</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Default</p></td>
<td><p>Fully qualified domain name (FQDN) of the pool</p></td>
<td><p>FQDN of the pool and the FQDN of the server</p>
<p>If you have multiple SIP domains and have enabled automatic client configuration, the certificate wizard detects and adds each supported SIP domain FQDNs.</p>
<p>If this pool is the auto-logon server for clients and strict Domain Name System (DNS) matching is required in group policy, you also need entries for sip.sipdomain (for each SIP domain you have).</p></td>
<td><p>SN=se01.contoso.com; SAN=se01.contoso.com</p>
<p>If this pool is the auto-logon server for clients and strict DNS matching is required in group policy, you also need SAN=sip.contoso.com; SAN=sip.fabrikam.com</p></td>
<td><p>On Standard Edition server, the server FQDN is the same as the pool FQDN.</p>
<p>The wizard detects any SIP domains you specified during setup and automatically adds them to the subject alternative name.</p>
<p>You can also use this certificate for Server-to-Server Authentication.</p></td>
</tr>
<tr class="even">
<td><p>Web internal</p></td>
<td><p>FQDN of the server</p></td>
<td><p>Each of the following:</p>
<ul>
<li><p>Internal web FQDN (which is the same as the FQDN of the server)</p></li>
<li><p>Meet simple URLs</p></li>
<li><p>Dial-in simple URL</p></li>
<li><p>Admin simple URL</p></li>
<li><p>Or, a wildcard entry for the simple URLs</p></li>
</ul></td>
<td><p>SN=se01.contoso.com; SAN=se01.contoso.com; SAN=meet.contoso.com; SAN=meet.fabrikam.com; SAN=dialin.contoso.com; SAN=admin.contoso.com</p>
<p>Using a wildcard certificate:</p>
<p>SN=se01.contoso.com; SAN=se01.contoso.com; SAN=*.contoso.com</p></td>
<td><p>You cannot override the Internal web FQDN in Topology Builder.</p>
<p>If you have multiple Meet simple URLs, you must include all of them as subject alternative names.</p>
<p>Wildcard entries are supported for the simple URL entries.</p></td>
</tr>
<tr class="odd">
<td><p>Web external</p></td>
<td><p>FQDN of the server</p></td>
<td><p>Each of the following:</p>
<ul>
<li><p>External web FQDN</p></li>
<li><p>Dial-in simple URL</p></li>
<li><p>Meet simple URLs per SIP domain</p></li>
<li><p>Or, a wildcard entry for the simple URLs</p></li>
</ul></td>
<td><p>SN=se01.contoso.com; SAN=webcon01.contoso.com; SAN=meet.contoso.com; SAN=meet.fabrikam.com; SAN=dialin.contoso.com</p>
<p>Using a wildcard certificate:</p>
<p>SN=se01.contoso.com; SAN=webcon01.contoso.com; SAN=*.contoso.com</p></td>
<td><p>If you have multiple Meet simple URLs, you must include all of them as subject alternative names.</p>
<p>Wildcard entries are supported for the simple URL entries.</p></td>
</tr>
</tbody>
</table>


### Certificates for Front End Server in a Front End Pool

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Certificate</th>
<th>Subject name/ Common name</th>
<th>Subject alternative name</th>
<th>Example</th>
<th>Comments</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Default</p></td>
<td><p>FQDN of the pool</p></td>
<td><p>FQDN of the pool and FQDN of the server.</p>
<p>If you have multiple SIP domains and have enabled automatic client configuration, the certificate wizard detects and adds each supported SIP domain FQDNs.</p>
<p>If this pool is the auto-logon server for clients and strict DNS matching is required in group policy, you also need entries for sip.sipdomain (for each SIP domain you have).</p></td>
<td><p>SN=eepool.contoso.com; SAN=eepool.contoso.com; SAN=ee01.contoso.com</p>
<p>If this pool is the auto-logon server for clients and strict DNS matching is required in group policy, you also need SAN=sip.contoso.com; SAN=sip.fabrikam.com</p></td>
<td><p>The wizard detects any SIP domains you specified during setup and automatically adds them to the subject alternative name.</p>
<p>You can also use this certificate for Server-to-Server Authentication.</p></td>
</tr>
<tr class="even">
<td><p>Web Internal</p></td>
<td><p>FQDN of the pool</p></td>
<td><p>Each of the following:</p>
<ul>
<li><p>Internal web FQDN (which is NOT the same as the FQDN of the server)</p></li>
<li><p>Server FQDN</p></li>
<li><p>Lync pool FQDN</p></li>
<li><p>Meet simple URLs</p></li>
<li><p>Dial-in simple URL</p></li>
<li><p>Admin simple URL</p></li>
<li><p>Or, a wildcard entry for the simple URLs</p></li>
</ul></td>
<td><p>SN=ee01.contoso.com; SAN=ee01.contoso.com; SAN=meet.contoso.com; SAN=meet.fabrikam.com; SAN=dialin.contoso.com; SAN=admin.contoso.com</p>
<p>Using a wildcard certificate:</p>
<p>SN=ee01.contoso.com; SAN=ee01.contoso.com; SAN=*.contoso.com</p></td>
<td><p>If you have multiple Meet simple URLs, you must include all of them as subject alternative names.</p>
<p>Wildcard entries are supported for the simple URL entries.</p></td>
</tr>
<tr class="odd">
<td><p>Web external</p></td>
<td><p>FQDN of the pool</p></td>
<td><p>Each of the following:</p>
<ul>
<li><p>External web FQDN</p></li>
<li><p>Dial-in simple URL</p></li>
<li><p>Admin simple URL</p></li>
<li><p>Or, a wildcard entry for the simple URLs</p></li>
</ul></td>
<td><p>SN=ee01.contoso.com; SAN=webcon01.contoso.com; SAN=meet.contoso.com; SAN=meet.fabrikam.com; SAN=dialin.contoso.com</p>
<p>Using a wildcard certificate:</p>
<p>SN=ee01.contoso.com; SAN=webcon01.contoso.com; SAN=*.contoso.com</p></td>
<td><p>If you have multiple Meet simple URLs, you must include all of them as subject alternative names.</p>
<p>Wildcard entries are supported for the simple URL entries.</p></td>
</tr>
</tbody>
</table>


### Certificates for Director

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Certificate</th>
<th>Subject name/ Common name</th>
<th>Subject alternative name</th>
<th>Example</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Default</p></td>
<td><p>FQDN of the Director pool</p></td>
<td><p>FQDN of the Director, FQDN of the Director pool</p>
<p>If this pool is the auto-logon server for clients and strict DNS matching is required in group policy, you also need entries for sip.sipdomain (for each SIP domain you have).</p></td>
<td><p>SN=dir-pool.contoso.com; SAN=dir-pool.contoso.com; SAN=dir01.contoso.com</p>
<p>If this Director pool is the auto-logon server for clients and strict DNS matching is required in group policy, you also need SAN=sip.contoso.com; SAN=sip.fabrikam.com</p></td>
</tr>
<tr class="even">
<td><p>Web Internal</p></td>
<td><p>FQDN of the server</p></td>
<td><p>Each of the following:</p>
<ul>
<li><p>Internal web FQDN (which is the same as the FQDN of the server)</p></li>
<li><p>Server FQDN</p></li>
<li><p>Lync pool FQDN</p></li>
<li><p>Meet simple URLs</p></li>
<li><p>Dial-in simple URL</p></li>
<li><p>Admin simple URL</p></li>
<li><p>Or, a wildcard entry for the simple URLs</p></li>
</ul></td>
<td><p>SN=dir01.contoso.com; SAN=dir01.contoso.com; SAN=meet.contoso.com; SAN=meet.fabrikam.com; SAN=dialin.contoso.com; SAN=admin.contoso.com</p>
<p>SN=dir01.contoso.com; SAN=dir01.contoso.com SAN=*.contoso.com</p></td>
</tr>
<tr class="odd">
<td><p>Web external</p></td>
<td><p>FQDN of the server</p></td>
<td><p>Each of the following:</p>
<ul>
<li><p>External web FQDN</p></li>
<li><p>Dial-in simple URL</p></li>
<li><p>Admin simple URL</p></li>
<li><p>Or, a wildcard entry for the simple URLs</p></li>
</ul></td>
<td><p>The Director external web FQDN must be different from the Front End pool or Front End Server.</p>
<p>SN=dir01.contoso.com; SAN=directorwebcon01.contoso.com SAN=meet.contoso.com; SAN=meet.fabrikam.com; SAN=dialin.contoso.com</p>
<p>SN=dir01.contoso.com; SAN=directorwebcon01.contoso.com SAN=*.contoso.com</p></td>
</tr>
</tbody>
</table>


If you have a stand-alone Mediation Server pool, the Mediation Servers in it each need the certificates listed in the following table. If you collocate Mediation Server with the Front End Servers, the certificates listed in the “Certificates for Front End Server in Front End Pool” table earlier in this topic are sufficient.

### Certificates for Stand-alone Mediation Server

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Certificate</th>
<th>Subject name/ Common name</th>
<th>Subject alternative name</th>
<th>Example</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Default</p></td>
<td><p>FQDN of the pool</p></td>
<td><p>FQDN of the pool</p>
<p>FQDN of pool member server</p></td>
<td><p>SN=medsvr-pool.contoso.net; SAN=medsvr-pool.contoso.net; SAN=medsvr01.contoso.net</p></td>
</tr>
</tbody>
</table>


### Certificates for Survivable Branch Appliance

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Certificate</th>
<th>Subject name/ Common name</th>
<th>Subject alternative name</th>
<th>Example</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Default</p></td>
<td><p>FQDN of the appliance</p></td>
<td><p>SIP.&lt;sipdomain&gt; (need one entry per SIP domain)</p></td>
<td><p>SN=sba01.contoso.net; SAN=sip.contoso.com; SAN=sip.fabrikam.com</p></td>
</tr>
</tbody>
</table>


<div>

## See Also


[Wildcard certificate support in Lync Server 2013](lync-server-2013-wildcard-certificate-support.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

