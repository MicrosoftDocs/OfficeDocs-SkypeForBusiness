---
title: 'DNS summary - SIP, XMPP federation, and public instant messaging'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: DNS summary - SIP, XMPP federation, and public instant messaging
ms:assetid: 1ed24fb8-a849-44c0-a52e-7aef7527e644
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ618369(v=OCS.15)
ms:contentKeyID: 49105656
ms.date: 03/09/2017
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# DNS summary - SIP, XMPP federation, and public instant messaging in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2017-03-09_

The Domain Name System (DNS) records that will be required for defining a federation with Office Communications Server or Lync Server partners is determined by your decision to either allow automatic DNS discovery of your domain by other perspective partners. If you publish the \_sipfederationtls.\_tcp. *\<SIP domain name\>* SRV record, any other SIP federated domain will be able to “discover” your federation. You can control which federated domains can communicate with you by using the Allows domains and Blocked Domains settings in the Lync Server Control Panel, or by setting the allowed or blocked domains configuration using the Lync Server Management Shell and the **Get**, **Set**, **New**, **Remove-CsAllowedDomain** and **-CsBlockedDomain** PowerShell cmdlets. For additional information on how to configure theses settings and the use of the PowerShell cmdlets, see **Related Topics** at the end of this topic.

The DNS records summary table depicts the required entries for an open, or discoverable, federation. If you do not want to implement Federation Discovery, You can decide to not configure the \_sipfederationtls.\_tcp. *\<SIP domain name\>* record.

<div>


> [!IMPORTANT]
> There are specific scenarios in which you must have the _sipfederationtls._tcp. <EM>&lt;SIP domain name&gt;</EM> SRV record, but you do not want to have a discoverable federation. One such instance is where you have deployed mobility for your users. The mobility push notification clearinghouse (PNCH) is a special type of federation that is used for Microsoft Lync Mobile clients on Apple iPhone or iPad using the Lync 2010 Mobile client or Windows Phone using the Lync 2010 Mobile or Lync 2013 Mobile clients. The _sipfederationtls._tcp. <EM>&lt;SIP domain name&gt;</EM> SRV record is used in the case of mobility and push notification. To mitigate this issue and control your discoverability, clear the setting <STRONG>Enable partner domain discovery</STRONG> to turn off discovery.



</div>

To configure extensible messaging and presence protocol (XMPP) for your deployment, you create two domain name system (DNS) records in an external DNS server that will resolve the records to the Access Edge service of your Edge Server or Edge pool.

When you configure domain name system (DNS) for public instant messaging connectivity, you will find that the configuration that supports external users will support public IM connectivity. If you have already configured your Edge Server or Edge pool, you should have the DNS records necessary to support public IM connectivity.

<div>

## DNS Summary - SIP Federation including Public Instant Messaging Connectivity


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Location/TYPE/Port</th>
<th>FQDN</th>
<th>IP address/FQDN host record</th>
<th>Maps to/Comments</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>External DNS/SRV/5061</p></td>
<td><p>_sipfederationtls._tcp.contoso.com</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>Access Edge service external interface Required for automatic DNS discovery of your federation to other potential federation partners, and is known as “Allowed SIP Domains” (called enhanced federation in previous releases).Repeat as necessary for all SIP domains with Lync enabled users</p>



> [!IMPORTANT]
> This SRV record is required for mobility and the push notification clearing house. In cases where there is more than one SIP domain, create and publish an SRV record for each domain that will have Lync Mobile clients. The Push Notification Service and Apple Push Notification service may not operate as expected if there is not an explicit SRV record for each SIP domain that the deployment supports.

</td>
</tr>
</tbody>
</table>


</div>

<div>

## DNS Summary - Extensible Messaging and Presence Protocol (XMPP)


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Location/TYPE/Port</th>
<th>FQDN</th>
<th>IP address/FQDN host record</th>
<th>Maps to/Comments</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>External DNS/SRV/5269</p></td>
<td><p>_xmpp-server._tcp.contoso.com</p></td>
<td><p>xmpp.contoso.com</p></td>
<td><p>XMPP proxy external interface on the Access Edge service or Edge pool.Repeat as necessary for all internal SIP domains with Lync enabled users where contact with XMPP contacts is allowed through the configuration of the External Access Policy through a global policy, site policy where the user is located, or user policy applied to the Lync-enabled user. An allowed XMPP domain must also be configured in the XMPP Federated Partners policy. See topics in <strong>See Also</strong> for additional details</p></td>
</tr>
<tr class="even">
<td><p>External DNS/A</p></td>
<td><p>xmpp.contoso.com (for example)</p></td>
<td><p>IP address of Access Edge service on your Edge Server or Edge pool hosting XMPP proxy</p></td>
<td><p>Points to the Access Edge service or Edge pool that hosts the XMPP proxy service. Typically, the SRV record that you create will point to this host (A or AAAA) record</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## See Also


[Setting up XMPP federation in Lync Server 2013](lync-server-2013-setting-up-xmpp-federation.md)  
[Configuring for push notifications in Lync Server 2013](lync-server-2013-configuring-for-push-notifications.md)  
[Enable or disable discovery of federation partners in Lync Server 2013](lync-server-2013-enable-or-disable-discovery-of-federation-partners.md)  


[Scenarios for external user access in Lync Server 2013](lync-server-2013-scenarios-for-external-user-access.md)  
[Determine DNS requirements for Lync Server 2013](lync-server-2013-determine-dns-requirements.md)  


[Manage SIP federated domains for your organization in Lync Server 2013](lync-server-2013-manage-sip-federated-domains-for-your-organization.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

