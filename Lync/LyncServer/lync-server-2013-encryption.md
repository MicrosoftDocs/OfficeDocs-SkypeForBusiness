---
title: 'Lync Server 2013: Encryption'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Encryption for Lync Server 2013
ms:assetid: d18c74a6-385b-407b-98eb-0d525fa38fea
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn481135(v=OCS.15)
ms:contentKeyID: 59893874
ms.date: 09/14/2017
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Encryption for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2017-09-14_

Microsoft Lync Server 2013 uses TLS and MTLS to encrypt instant messages. All server-to-server traffic requires MTLS, regardless of whether the traffic is confined to the internal network or crosses the internal network perimeter. TLS is optional but strongly recommended between the Mediation Server and media gateway. If TLS is configured on this link, MTLS is required. Therefore, the gateway must be configured with a certificate from a CA that is trusted by the Mediation Server.

<div>


> [!NOTE]  
> A security advisory regarding SSL 3.0 was published in 2014. Disabling SSL 3.0 in Lync Server 2013 is a supported option. To learn more about the security advisory, see <A class=uri href="https://blogs.technet.microsoft.com/uclobby/2014/10/22/disabling-ssl-3-0-in-lync-server-2013/">https://blogs.technet.microsoft.com/uclobby/2014/10/22/disabling-ssl-3-0-in-lync-server-2013/</A>.



</div>

<div>

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398321.security(OCS.15).gif" title="security" alt="security" />Security Note:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>To ensure the strongest cryptographic protocol is used, Lync Server 2013 will offer TLS encryption protocols in the following order to clients: <strong>TLS 1.2</strong> , <strong>TLS 1.1</strong>, <strong>TLS 1.0</strong>. TLS is a critical aspect of Lync Server 2013 and thus it is required in order to maintain a supported environment.</td>
</tr>
</tbody>
</table>


</div>

Requirements for client-to-client traffic depend on whether that traffic crosses the internal corporate firewall. Strictly internal traffic can use either TLS, in which case the instant message is encrypted, or TCP, in which case it is not.

The following table summarizes the protocol requirements for each type of traffic.

### Traffic Protection

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Traffic type</th>
<th>Protected by</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Server-to-server</p></td>
<td><p>MTLS</p></td>
</tr>
<tr class="even">
<td><p>Client-to-server</p></td>
<td><p>TLS</p></td>
</tr>
<tr class="odd">
<td><p>Instant messaging and presence</p></td>
<td><p>TLS (if configured for TLS)</p></td>
</tr>
<tr class="even">
<td><p>Audio and video and desktop sharing of media</p></td>
<td><p>SRTP</p></td>
</tr>
<tr class="odd">
<td><p>Desktop sharing (signaling)</p></td>
<td><p>TLS</p></td>
</tr>
<tr class="even">
<td><p>Web conferencing</p></td>
<td><p>TLS</p></td>
</tr>
<tr class="odd">
<td><p>Meeting content download, address book download, distribution group expansion</p></td>
<td><p>HTTPS</p></td>
</tr>
</tbody>
</table>


<div>

## Media Encryption

Media traffic is encrypted using Secure RTP (SRTP), a profile of Real-Time Transport Protocol (RTP) that provides confidentiality, authentication, and replay attack protection to RTP traffic. In addition, media flowing in both directions between the Mediation Server and its internal next hop is also encrypted using SRTP. Media flowing in both directions between the Mediation Server and a media gateway is not encrypted by default. The Mediation Server can support encryption to the media gateway, but the gateway must support MTLS and storage of a certificate.

<div>


> [!NOTE]  
> Audio/Video (A/V) is supported with the new version of Windows Live Messenger. If you are implementing A/V federation with Windows Live Messenger, you must also modify the Lync Server encryption level. By default, the encryption level is Required. You must change this setting to Supported by using the Lync Server Management Shell. For more information, see <A href="lync-server-2013-deploying-external-user-access.md">Deploying external user access in Lync Server 2013</A> in the Deployment documentation.



</div>

Audio and video media traffic is not encrypted between Microsoft Lync 2013 and Windows Live clients.

</div>

<div>

## FIPS

Lync Server 2013 and Microsoft Exchange Server 2013 operate with support for Federal Information Processing Standard (FIPS) 140-2 algorithms if the Windows Server operating systems are configured to use the FIPS 140-2 algorithms for system cryptography. To implement FIPS support, you must configure each server running Lync Server 2013 to support it. For details about the use of FIPS-compliant algorithms and how to implement FIPS support, see Microsoft Knowledge Base article 811833, The effects of enabling the “System cryptography: Use FIPS compliant algorithms for encryption, hashing, and signing" security setting in Windows XP and in later versions of Windows at [http://go.microsoft.com/fwlink/p/?linkid=3052\&kbid=811833](http://go.microsoft.com/fwlink/p/?linkid=3052%26kbid=811833). For details about FIPS 140-2 support and limitations in Exchange 2010, see Exchange 2010 SP1 and Support for FIPS Compliant Algorithms at [https://go.microsoft.com/fwlink/p/?LinkId=205335](https://go.microsoft.com/fwlink/p/?linkid=205335).

</div>

</div>

<span> </span>

</div>

</div>

</div>

