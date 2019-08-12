---
title: 'Lync Server 2013: Starting Lync from another application'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Starting Lync from another application
ms:assetid: 573b30b1-6590-4b24-8e96-a41be57cb0ef
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398376(v=OCS.15)
ms:contentKeyID: 48184184
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Starting Lync from another application

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-20_

You can use command-line parameters to quick-start Lync 2013. For example, if a user clicks a phone number in another application, the application can start an instance of Lync 2013 and initiate a call to that number.

Lync 2013 can also recognize a semicolon-delimited list of contact names for multiparty conferencing.

If Lync 2013 is configured to automatically sign in when started, then starting Lync 2013 with command-line parameters will open the Lync main window. If Lync is not configured to automatically sign in when started, the sign-in window opens.

The following table shows the available parameters.

### Lync 2013 Command-Line Parameters

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Extension</th>
<th>Format of Data</th>
<th>Action</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>tel:</p></td>
<td><p>tel URI</p></td>
<td><p>Opens the Conversation window for an audio call but does not dial the specified number.</p></td>
</tr>
<tr class="even">
<td><p>callto:</p></td>
<td><p>tel:, sip:, or typeable tel URI</p></td>
<td><p>Opens the Conversation window for an audio call but does not dial the specified number.</p></td>
</tr>
<tr class="odd">
<td><p>sip:</p></td>
<td><p>SIP URI</p></td>
<td><p>Opens the Conversation window with the specified SIP Uniform Resource Identifier (URI) in the participant list.</p></td>
</tr>
<tr class="even">
<td><p>Sips:</p></td>
<td><p>SIP URI</p></td>
<td><p>If Lync 2013 is configured to use the Transport Layer Security (TLS) protocol, functions exactly like sip:. If TLS is not being used, displays a dialog box informing the user that a higher level of security is required.</p></td>
</tr>
<tr class="odd">
<td><p>conf:</p></td>
<td><p>SIP URI of conference to join</p></td>
<td><p>If URI is self, instantiates the focus and brings up roster-only view. Otherwise, brings up roster view but does not send INVITE.</p></td>
</tr>
<tr class="even">
<td><p>im:</p></td>
<td><p>SIP URI</p></td>
<td><p>Displays an instant messaging (IM)-only Conversation window with the SIP URI. Accepts multiple SIP URIs specified inside angle brackets (&lt;&gt;) without any separator.</p>
<pre><code>im:&lt;sip:user1@host&gt;&lt;sip:user2@host&gt;</code></pre></td>
</tr>
</tbody>
</table>


The following table provides examples of these command-line parameters.

### Command-Line Parameter Examples

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Instance</th>
<th>Results</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Tel:+14255550101</p></td>
<td><p>Opens a phone-only view with +14255550101.</p></td>
</tr>
<tr class="even">
<td><p>Callto:tel:+ 14255550101</p></td>
<td><p>Opens a phone-only view with +14255550101.</p></td>
</tr>
<tr class="odd">
<td><p>Callto:sip:kazuto@litwareinc.com</p></td>
<td><p>Opens a phone-only view with kazuto@litwareinc.com.</p></td>
</tr>
<tr class="even">
<td><p>sip:kazuto@litwareinc.com</p></td>
<td><p>Opens a Conversation window with kazuto@litwareinc.com.</p></td>
</tr>
<tr class="odd">
<td><p>conf:sip:https://meet.contoso.com/kazuto/7322994</p></td>
<td><p>Opens a Conversation window and displays meeting audio join options.</p></td>
</tr>
</tbody>
</table>


</div>

<span> </span>

</div>

</div>

</div>

