---
title: 'Lync Server 2013: UCWA events'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: UCWA events
ms:assetid: 26cb409d-f4e4-43c7-873f-b694702d491d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ945621(v=OCS.15)
ms:contentKeyID: 51541461
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# UCWA events in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-15_

    The information in this topic pertains to Cumulative Updates for Lync Server 2013: February 2013.

Lync Server 2013 uses the Unified Communications Web API (UCWA) for a number of purposes, from accessing Microsoft Exchange for contact searches to updating presence for mobile clients.

UCWA will write records of operational behavior as event types Informational, Warning, and Error. The following table describes the events that can be written by the UCWA components.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Event ID</th>
<th>Event Type</th>
<th>Summary</th>
<th>Cause and Resolution</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>20001</p></td>
<td><p>Informational</p></td>
<td><p>UCWA initialized</p></td>
<td><p>N/A</p>
<p>N/A</p></td>
</tr>
<tr class="even">
<td><p>20002</p></td>
<td><p>Error</p></td>
<td><p>UCWA encountered an unexpected exception during initialization</p></td>
<td><p>An unexpected error has occurred during initialization</p>
<p>Examine the exception details in the associated event log entry to determine the possible cause</p></td>
</tr>
<tr class="odd">
<td><p>20003</p></td>
<td><p>Error</p></td>
<td><p>UCWA encountered an unhandled exception</p></td>
<td><p>An unhandled exception happened</p>
<p>Restart the server. If the problem persists contact product support</p></td>
</tr>
<tr class="even">
<td><p>20004</p></td>
<td><p>Error</p></td>
<td><p>Cannot access Exchange for HD photo</p></td>
<td><p>Connection to Exchange is not available</p>
<p>Make sure the connection to Exchange is available</p></td>
</tr>
<tr class="odd">
<td><p>20005</p></td>
<td><p>Informational</p></td>
<td><p>Recovered from failing to access Exchange for HD photo</p></td>
<td><p>N/A</p></td>
</tr>
<tr class="even">
<td><p>20006</p></td>
<td><p>Error</p></td>
<td><p>Cannot access Exchange for contact search</p></td>
<td><p>Connection to Exchange is not available</p>
<p>Make sure the connection to Exchange is available</p></td>
</tr>
<tr class="odd">
<td><p>20007</p></td>
<td><p>Informational</p></td>
<td><p>Recovered from failing to search contact in Exchange</p></td>
<td><p>N/A</p></td>
</tr>
<tr class="even">
<td><p>20008</p></td>
<td><p>Warning</p></td>
<td><p>Attempt to subscribe more than the allowed presence subscriptions per application</p></td>
<td><p>Attempt to subscribe more than the allowed presence subscriptions per application</p>
<p>Check the clients for unnecessary subscriptions</p></td>
</tr>
<tr class="odd">
<td><p>20009</p></td>
<td><p>Warning</p></td>
<td><p>Attempt to subscribe more than the allowed presence subscriptions per batch</p></td>
<td><p>Attempt to subscribe more than the allowed presence subscriptions per batch</p>
<p>Check the clients for unnecessary subscriptions</p></td>
</tr>
<tr class="even">
<td><p>20010</p></td>
<td><p>Error</p></td>
<td><p>Cannot retrieve inband data</p></td>
<td><p>Cannot retrieve inband data</p>
<p>If the problem persists contact product support</p></td>
</tr>
<tr class="odd">
<td><p>20011</p></td>
<td><p>Error</p></td>
<td><p>Cannot subscribe presence</p></td>
<td><p>Cannot subscribe presence</p>
<p>If the problem persists contact product support</p></td>
</tr>
<tr class="even">
<td><p>20012</p></td>
<td><p>Error</p></td>
<td><p>Failed to register endpoint</p></td>
<td><p>Failed to register endpoint</p>
<p>If the problem persists contact product support</p></td>
</tr>
<tr class="odd">
<td><p>20013</p></td>
<td><p>Error</p></td>
<td><p>IM MCU is unavailable</p></td>
<td><p>IM MCU is unavailable</p>
<p>See whether IM MCU is running</p></td>
</tr>
<tr class="even">
<td><p>20014</p></td>
<td><p>Informational</p></td>
<td><p>Recovered from failing to connect to IM MCU</p></td>
<td><p>N/A</p></td>
</tr>
<tr class="odd">
<td><p>20015</p></td>
<td><p>Error</p></td>
<td><p>AV MCU is unavailable</p></td>
<td><p>AV MCU is unavailable</p>
<p>See whether AV MCU is running</p></td>
</tr>
<tr class="even">
<td><p>20016</p></td>
<td><p>Informational</p></td>
<td><p>Recovered from failing to connect to AV MCU</p></td>
<td><p>N/A</p></td>
</tr>
<tr class="odd">
<td><p>20017</p></td>
<td><p>Error</p></td>
<td><p>AS MCU is unavailable</p></td>
<td><p>AS MCU is unavailable</p>
<p>See whether AS MCU is running</p></td>
</tr>
<tr class="even">
<td><p>20018</p></td>
<td><p>Informational</p></td>
<td><p>Recovered from failing to connect to AS MCU</p></td>
<td><p>N/A</p></td>
</tr>
<tr class="odd">
<td><p>20019</p></td>
<td><p>Error</p></td>
<td><p>Data MCU is unavailable</p></td>
<td><p>Data MCU is unavailable</p>
<p>See whether Data MCU is running</p></td>
</tr>
<tr class="even">
<td><p>20020</p></td>
<td><p>Informational</p></td>
<td><p>Recovered from failing to connect to Data MCU</p></td>
<td><p>N/A</p></td>
</tr>
<tr class="odd">
<td><p>20021</p></td>
<td><p>Error</p></td>
<td><p>Cannot join IM MCU</p></td>
<td><p>Cannot join IM MCU</p>
<p>See whether IM MCU is running</p></td>
</tr>
<tr class="even">
<td><p>20022</p></td>
<td><p>Error</p></td>
<td><p>Cannot join AV MCU</p></td>
<td><p>Cannot join AV MCU</p>
<p>See whether AV MCU is running</p></td>
</tr>
<tr class="odd">
<td><p>20023</p></td>
<td><p>Error</p></td>
<td><p>Cannot join AS MCU</p></td>
<td><p>Cannot join AS MCU</p>
<p>See whether AS MCU is running</p></td>
</tr>
<tr class="even">
<td><p>20024</p></td>
<td><p>Error</p></td>
<td><p>Cannot join Data MCU</p></td>
<td><p>Cannot join Data MCU</p>
<p>See whether Data MCU is running</p></td>
</tr>
<tr class="odd">
<td><p>20025</p></td>
<td><p>Error</p></td>
<td><p>Cannot access active directory for photo</p></td>
<td><p>Connection to active directory is not available</p>
<p>Make sure the connection to active directory is available</p></td>
</tr>
<tr class="even">
<td><p>20026</p></td>
<td><p>Informational</p></td>
<td><p>Recovered from failing to access active directory for photo</p></td>
<td><p>N/A</p></td>
</tr>
<tr class="odd">
<td><p>20027</p></td>
<td><p>Warning</p></td>
<td><p>Cannot deserialize</p></td>
<td><p>Cannot deserialize</p>
<p>If the problem persists contact product support</p></td>
</tr>
</tbody>
</table>


</div>

<span> </span>

</div>

</div>

</div>

