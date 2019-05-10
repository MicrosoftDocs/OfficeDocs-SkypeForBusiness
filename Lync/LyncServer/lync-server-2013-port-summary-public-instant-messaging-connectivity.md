---
title: 'Lync Server 2013: Port summary - Public instant messaging connectivity'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Port summary - Public instant messaging connectivity
ms:assetid: f46756ec-1401-4ca2-a4a4-5cd28bcfdc7f
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ618376(v=OCS.15)
ms:contentKeyID: 49105663
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Port summary - Public instant messaging connectivity in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-16_

To configure your firewall for ports and protocols necessary to support public instant messaging connectivity, first note that SIP/MTLS/TCP 5061 is bidirectional to account for the ability of contacts in the public IM provider to contact Lync clients, or for Lync to contact public IM contacts.

Windows Live Messenger can participate in audio/video communications with Lync clients. This accounts for the very similar firewall port and protocol configuration that you would typically have on the firewall to support Lync clients as external users.

<div>


> [!IMPORTANT]  
> More than ever, Lync is a powerful tool for connecting across organizations and with individuals around the world. Federation with Windows Live Messenger requires no additional user/device licenses beyond the Lync Standard Client Access License (CAL). Skype federation will be added to this list, enabling Lync users to reach hundreds of millions of people with IM and voice.<BR>Federation with Messenger client contacts will officially end on March 15, 2013, except for mainland China. Skype will become the federation client for federated users who previously used Messenger.



</div>

<div>

## Firewall Summary – Public Instant Messaging Connectivity


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Role/Protocol/TCP or UDP/Port</th>
<th>Source IP address</th>
<th>Destination IP address</th>
<th>Notes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Access/SIP(MTLS)/TCP/5061</p></td>
<td><p>Public IM connectivity partners</p></td>
<td><p>Edge Server Access interface</p></td>
<td><p>For federated and public IM connectivity that use SIP.</p></td>
</tr>
<tr class="even">
<td><p>Access/SIP(MTLS)/TCP/5061</p></td>
<td><p>Edge Server Access interface</p></td>
<td><p>Public IM connectivity partners</p></td>
<td><p>For federated and public IM connectivity that use SIP.</p></td>
</tr>
<tr class="odd">
<td><p>Access/SIP(TLS)/TCP/443</p></td>
<td><p>Clients</p></td>
<td><p>Edge Server Access interface</p></td>
<td><p>Client-to-server SIP traffic for external user access.</p></td>
</tr>
<tr class="even">
<td><p>A/V/RTP/TCP/50,000-59,999</p></td>
<td><p>Edge Server Access interface</p></td>
<td><p>Live Messenger clients</p></td>
<td><p>Used for A/V sessions with Windows Live Messenger if public IM connectivity is configured.</p></td>
</tr>
<tr class="odd">
<td><p>A/V/STUN,MSTURN/UDP/3478</p></td>
<td><p>Edge Server Access interface</p></td>
<td><p>Live Messenger clients</p></td>
<td><p>Required for public IM connectivity with Windows Live Messenger.</p></td>
</tr>
<tr class="even">
<td><p>A/V/STUN,MSTURN/UDP/3478</p></td>
<td><p>Live Messenger clients</p></td>
<td><p>Edge Server Access interface</p></td>
<td><p>Required for public IM connectivity with Windows Live Messenger.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## See Also


[Scenarios for external user access in Lync Server 2013](lync-server-2013-scenarios-for-external-user-access.md)  
[Determine external A/V firewall and port requirements for Lync Server 2013](lync-server-2013-determine-external-a-v-firewall-and-port-requirements.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

