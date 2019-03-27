---
title: 'Lync Server 2013: Certificate summary - Extensible messaging and presence protocol (XMPP) federation'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Certificate summary - Extensible messaging and presence protocol (XMPP) federation
ms:assetid: b059a34e-99df-40af-91fe-fe2aa52841f6
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ618374(v=OCS.15)
ms:contentKeyID: 49105661
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Certificate summary - Extensible messaging and presence protocol (XMPP) federation in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-12-23_

Certificate requirements for enabling and establishing communications with extensible messaging and presence protocol (XMPP) partners require the additional record of your XMPP domains. The record that is included on the certificate as a subject alternative name (SAN) will be the domain that can participate in XMPP communications. The domain can be the root-level domain (for example, contoso.com) if you want to enable XMPP for your entire domain, or can be selected child domains (for example, corp.contoso.com, finance.contoso.com) if you are enabling XMPP for a subset of users.

<div>

## Certificate Summary for Extensible Messaging and Presence Protocol


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Component</th>
<th>Subject name</th>
<th>Subject alternative names (SAN)/Order</th>
<th>Comments</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Assign to Access Edge service of Edge Server or Edge pool</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>webcon.contoso.com</p>
<p>sip.contoso.com</p>
<p>sip.fabrikam.com</p>
<p>contoso.com</p></td>
<td><p>The first three SAN entries are the normal SAN entries for a full Edge Server. The contoso.com is the entry required for federation with the XMPP partner at the root domain level. This entry will allow XMPP for all domains with the suffix contoso.com.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## See Also


[Example XMPP configuration in Lync Server 2013 – XMPP federation with Google Talk](lync-server-2013-example-xmpp-configuration-–-xmpp-federation-with-google-talk.md)  


[Plan for Edge Server certificates in Lync Server 2013](lync-server-2013-plan-for-edge-server-certificates.md)  


[Set up Edge certificates for Lync Server 2013](lync-server-2013-set-up-edge-certificates.md)  
[Request-CsCertificate](https://docs.microsoft.com/powershell/module/skype/Request-CsCertificate)  
[Set-CsCertificate](https://docs.microsoft.com/powershell/module/skype/Set-CsCertificate)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

