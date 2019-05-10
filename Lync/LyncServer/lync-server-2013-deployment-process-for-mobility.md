---
title: 'Lync Server 2013: Deployment process for mobility'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Deployment process for mobility
ms:assetid: 5a1cebda-c14b-4ff4-9c36-f7caa868160f
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Hh690023(v=OCS.15)
ms:contentKeyID: 48184220
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Deployment process for mobility in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-19_

    Some information in this topic pertains to Cumulative Updates for Lync Server 2013: February 2013. It is noted accordingly.

This section describes the sequence of steps required to deploy the Lync Server 2013 mobility feature.

### Mobility Deployment Process

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Phase</th>
<th>Steps</th>
<th>Permissions</th>
<th>Deployment documentation</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Create Domain Name System (DNS) records</p></td>
<td><ul>
<li><p>Create an internal DNS CNAME or A (host, if IPv6, AAAA) record to resolve the internal Autodiscover Service URL.</p></li>
<li><p>Create an external DNS CNAME or A (host, if IPv6, AAAA) record to resolve the external Autodiscover Service URL.</p></li>
</ul></td>
<td><p>Domain Admins</p>
<p>DnsAdmins</p></td>
<td><p><a href="lync-server-2013-creating-dns-records-for-the-autodiscover-service.md">Creating DNS records for the Autodiscover Service in Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p>Modify certificates</p></td>
<td><p>Add subject alternative name entries to the following certificates to support secure connections for mobile users:</p>
<ul>
<li><p>Director certificate</p></li>
<li><p>Front End pool certificate</p></li>
<li><p>Reverse proxy certificate</p></li>
</ul></td>
<td><p>Local administrator</p></td>
<td><p><a href="lync-server-2013-modifying-certificates-for-mobility.md">Modifying certificates for mobility in Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p>Configure the reverse proxy</p></td>
<td><ul>
<li><p>Assign certificates updated with subject alternative names to the Secure Sockets Layer (SSL) Listener.</p></li>
<li><p>Reconfigure the web publishing rule for the external Autodiscover Service URL.</p></li>
<li><p>Be sure that a web publishing rule exists for the external Lync Server 2013 Web Services URL on your Front End pool.</p></li>
</ul>
<p>Or</p>
<ul>
<li><p>If you choose to use HTTP for the initial Autodiscover request and do not update subject alternative name lists on the certificates, configure a new web publishing rule or reconfigure an existing publishing rule for port 80 HTTP.</p></li>
</ul></td>
<td><p>Local administrator</p></td>
<td><p><a href="lync-server-2013-configuring-the-reverse-proxy-for-mobility.md">Configuring the reverse proxy for mobility in Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p>Test your mobility deployment for Lync 2010 Mobile using the Mcx Mobility Service</p></td>
<td><p>Run <strong>Test-CsMcxP2PIM</strong> to test sending an instant message from one person to another.</p>
<p>See the Lync Server Management Shell cmdlet documentation for <a href="https://docs.microsoft.com/powershell/module/skype/Test-CsMcxP2PIM">Test-CsMcxP2PIM</a> for a complete list of options.</p></td>
<td><p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-verifying-your-mobility-deployment.md">Verifying your mobility deployment in Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p>Test your mobility deployment for Lync 2013 Mobile clients using the UCWA Web components</p></td>
<td><p>Use the <strong>Test-CsUcwaConference</strong> cmdlet to test and verify that pre-defined test users or a pair of actual users can use UCWA to create and participate in a conference.</p>
<p>See the Lync Server Management Shell cmdlet documentation for <a href="https://docs.microsoft.com/powershell/module/skype/Test-CsUcwaConference">Test-CsUcwaConference</a> for a complete list of options.</p></td>
<td><p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-verifying-your-mobility-deployment.md">Verifying your mobility deployment in Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p>Configure for push notifications</p></td>
<td><ul>
<li><p>For Lync Server 2013 Edge Servers, add a Lync Server online hosting provider and configure hosting provider federation.</p></li>
<li><p>For Lync Server 2010  Edge Servers, add a Lync Server online hosting provider and configure hosting provider federation.</p></li>
<li><p>For Office Communications Server 2007 R2 Edge Servers, add a federated partner.</p></li>
<li><p>If you want to support push notifications over a Wi-Fi network, configure a firewall rule outbound for TCP port 5223.</p></li>
<li><p>Use the <strong>Set-CsPushNotificationConfiguration</strong> cmdlet to enable push notifications to the Apple Push Notification Service (APNS) and Microsoft Push Notification Service (MPNS). This feature is disabled by default.</p></li>
<li><p>Use the <strong>Test-CsFederatedPartner</strong> cmdlet to test the federation configuration and the <strong>Test-CsMCXPushNotification</strong> cmdlet to test push notifications.</p>
<div>

> [!NOTE]  
> Push notifications are used for Lync 2010 Mobile clients on Apple devices and Windows Phone<BR>Push notification is required for Lync 2013 Mobile clients on Windows Phone only


</div></li>
</ul></td>
<td><p>RtcUniversalServerAdmins</p></td>
<td><p><a href="lync-server-2013-configuring-for-push-notifications.md">Configuring for push notifications in Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p>Configure mobility policy</p></td>
<td><p>Use the <strong>Set-CsMobilityPolicy</strong> cmdlet to allow or disallow:</p>
<ul>
<li><p>Call via Work</p></li>
<li><p>Enable IP Audio and IP Video</p></li>
<li><p>Require WiFi for IP Audio and/or IP Video</p></li>
</ul></td>
<td><p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-configuring-mobility-policy.md">Configuring mobility policy in Lync Server 2013</a></p></td>
</tr>
</tbody>
</table>


</div>

<span> </span>

</div>

</div>

</div>

