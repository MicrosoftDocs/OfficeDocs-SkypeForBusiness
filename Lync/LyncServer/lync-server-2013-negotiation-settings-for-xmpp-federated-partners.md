---
title: 'Lync Server 2013: Negotiation settings for XMPP federated partners'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Negotiation settings for XMPP federated partners
ms:assetid: ef773942-ef92-4f71-85a1-738dfebdfa00
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ552456(v=OCS.15)
ms:contentKeyID: 48679567
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Negotiation settings for XMPP federated partners in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-21_

The settings for the negotiation types in the configuration of an XMPP Partner have a wide variety of possible combinations. Not all of these combinations are valid. The table detailed in this topic will define the valid and not valid settings. Common configurations are presented in the first table, the second table detailing all possible combinations. Note that you cannot have *Simple Authentication and Security Layer* (SASL) **unless** *Transport Layer Security* (TLS) is also available. SASL is sent in an unencrypted (readable) format and should never be transmitted unless protected by another means, such as TLS.

### Common XMPP Federation Negotiation Methods

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
<th>Transport Layer Security (TLS)</th>
<th>Simple Authentication and Security Layer (SASL)</th>
<th>Dialback Authentication</th>
<th>Expected Authentication Method(s)</th>
<th>Notes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Required</p></td>
<td><p>Required</p></td>
<td><p>False</p></td>
<td><p>SASL over TLS</p></td>
<td><p>TLS and SASL required helps to ensure that the SASL message stream is secure. Dialback is not available and cannot be used for a fallback method if the XMPP federated partner has not set TLS to required or optional.</p></td>
</tr>
<tr class="even">
<td><p>Required</p></td>
<td><p>Optional</p></td>
<td><p>True</p></td>
<td><p>SASL over TLS, TLS Dialback, TCP Dialback</p></td>
<td><p>By requiring TLS, if the XMPP federated partner has set SASL to optional or required SASL is used. If SASL is not available, Dialback over TLS will be used.</p></td>
</tr>
<tr class="odd">
<td><p>Optional</p></td>
<td><p>Optional</p></td>
<td><p>True</p></td>
<td><p>SASL over TLS, TLS Dialback, TCP Dialback</p></td>
<td><p>While very flexible in the negotiation methods offered, these settings rely on the XMPP federation partner’s settings. If the partner has TLS optional or required but SASL is not supported, TLS Dialback will be available. If the partner has TLS and SASL set to optional or required, the optimal selection of TLS over SASL is used.</p></td>
</tr>
<tr class="even">
<td><p>Not Supported</p></td>
<td><p>Not Supported</p></td>
<td><p>True</p></td>
<td><p>TCP Dialback</p></td>
<td><p>In many cases, TCP Dialback is the only possible solution. Less desirable than other options, it does provide some level of trust.</p></td>
</tr>
</tbody>
</table>


### XMPP Federation Negotiation Methods Matrix - Complete

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
<th>Transport Layer Security (TLS)</th>
<th>Simple Authentication and Security Layer (SASL)</th>
<th>Dialback Authentication</th>
<th>Expected Authentication Method</th>
<th>Notes, Warning or Error for Not Valid Configuration</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Required</p></td>
<td><p>Required</p></td>
<td><p>True</p></td>
<td><p>SASL over TLS</p></td>
<td><div>

> [!WARNING]  
> Dialback will not operate if both SASL and TLS are required.


</div></td>
</tr>
<tr class="even">
<td><p>Required</p></td>
<td><p>Required</p></td>
<td><p>False</p></td>
<td><p>SASL over TLS</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Optional</p></td>
<td><p>Required</p></td>
<td><p>True</p></td>
<td><p>SASL over TLS, TLS Dialback, TCP Dialback</p></td>
<td><div>

> [!WARNING]  
> SASL requires TLS. Allowing TLS to be optional may result in failed session negotiations.


</div></td>
</tr>
<tr class="even">
<td><p>Optional</p></td>
<td><p>Required</p></td>
<td><p>False</p></td>
<td><p>SASL over TLS</p></td>
<td><div>

> [!WARNING]  
> SASL requires TLS. Allowing TLS to be optional may result in failed session negotiations.


</div></td>
</tr>
<tr class="odd">
<td><p>Not Supported</p></td>
<td><p>Required</p></td>
<td><p>True</p></td>
<td><p>TCP Dialback</p></td>
<td><div>

> [!WARNING]  
> SASL requires TLS. Allowing TLS to be optional may result in failed session negotiations.


</div></td>
</tr>
<tr class="even">
<td><p>Not Supported</p></td>
<td><p>Required</p></td>
<td><p>False</p></td>
<td><div>

> [!WARNING]  
> Not Valid Configuration


</div></td>
<td><div>

> [!WARNING]  
> Because SASL requires TLS, and TLS is not available, SASL/TLS cannot succeed. TCP Dialback is set to false, and cannot be used.


</div></td>
</tr>
<tr class="odd">
<td><p>Required</p></td>
<td><p>Optional</p></td>
<td><p>True</p></td>
<td><p>SASL over TLS, TLS Dialback</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Required</p></td>
<td><p>Optional</p></td>
<td><p>False</p></td>
<td><p>SASL over TLS</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Optional</p></td>
<td><p>Optional</p></td>
<td><p>True</p></td>
<td><p>SASL over TLS, TLS Dialback, TCP Dialback</p></td>
<td><div>

> [!WARNING]  
> SASL requires TLS. Allowing TLS to be optional may result in failed session negotiations.


</div></td>
</tr>
<tr class="even">
<td><p>Optional</p></td>
<td><p>Optional</p></td>
<td><p>False</p></td>
<td><p>SASL over TLS</p></td>
<td><div>

> [!WARNING]  
> SASL requires TLS. Allowing TLS to be optional may result in failed session negotiations.


</div></td>
</tr>
<tr class="odd">
<td><p>Not Supported</p></td>
<td><p>Optional</p></td>
<td><p>True</p></td>
<td><p>TCP Dialback</p></td>
<td><div>

> [!WARNING]  
> SASL requires TLS. Allowing TLS to be optional may result in failed session negotiations.


</div></td>
</tr>
<tr class="even">
<td><p>Not Supported</p></td>
<td><p>Optional</p></td>
<td><p>False</p></td>
<td><div>

> [!WARNING]  
> Not Valid Configuration


</div></td>
<td><div>

> [!WARNING]  
> SASL requires TLS. Allowing TLS to be optional may result in failed session negotiations.


</div></td>
</tr>
<tr class="odd">
<td><p>Required</p></td>
<td><p>Not Supported</p></td>
<td><p>True</p></td>
<td><p>TLS Dialback</p></td>
<td><p>Configuration allows for TLS Dialback.</p></td>
</tr>
<tr class="even">
<td><p>Required</p></td>
<td><p>Not Supported</p></td>
<td><p>False</p></td>
<td><p>Not Valid Configuration</p></td>
<td><div>

> [!WARNING]  
> SASL or Dialback must be enabled.


</div></td>
</tr>
<tr class="odd">
<td><p>Optional</p></td>
<td><p>Not Supported</p></td>
<td><p>True</p></td>
<td><p>TLS Dialback, TCP Dialback</p></td>
<td><p>Based on negotiation choices of the other end point, TCP or TLS Dialback will be accepted.</p></td>
</tr>
<tr class="even">
<td><p>Optional</p></td>
<td><p>Not Supported</p></td>
<td><p>False</p></td>
<td><p>Not Valid Configuration</p></td>
<td><div>

> [!WARNING]  
> SASL or Dialback must be enabled.


</div></td>
</tr>
<tr class="odd">
<td><p>Not Supported</p></td>
<td><p>Not Supported</p></td>
<td><p>True</p></td>
<td><p>TCP Dialback</p></td>
<td><p>TCP Dialback is the only negotiation method available</p></td>
</tr>
<tr class="even">
<td><p>Not Supported</p></td>
<td><p>Not Supported</p></td>
<td><p>False</p></td>
<td><p>Not Valid Configuration</p></td>
<td><div>

> [!WARNING]  
> SASL or Dialback must be enabled.


</div></td>
</tr>
</tbody>
</table>


</div>

<span> </span>

</div>

</div>

</div>

