---
title: 'Lync Server 2013: UserAgentDef table'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: UserAgentDef table
ms:assetid: 96c49239-d999-4045-8b64-9d1940cce8ff
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205100(v=OCS.15)
ms:contentKeyID: 48184860
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# UserAgentDef table in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-03-25_

The UserAgentDef table maps user agent identifiers to the agent’s descriptive names. User agents are software clients used to connect to Microsoft Lync Server 2013. This table was introduced in Microsoft Lync Server 2013.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>UAType</th>
<th>UAName</th>
<th>UACategory</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1</p></td>
<td><p>MediationServer</p></td>
<td><p>MediationServer</p></td>
</tr>
<tr class="even">
<td><p>2</p></td>
<td><p>AV-MCU</p></td>
<td><p>AV-MCU</p></td>
</tr>
<tr class="odd">
<td><p>4</p></td>
<td><p>OC</p></td>
<td><p>OC</p></td>
</tr>
<tr class="even">
<td><p>8</p></td>
<td><p>OCPhone</p></td>
<td><p>OCPhone</p></td>
</tr>
<tr class="odd">
<td><p>16</p></td>
<td><p>LMC</p></td>
<td><p>LMC</p></td>
</tr>
<tr class="even">
<td><p>32</p></td>
<td><p>DVT</p></td>
<td><p>DVT</p></td>
</tr>
<tr class="odd">
<td><p>64</p></td>
<td><p>MM</p></td>
<td><p>MM</p></td>
</tr>
<tr class="even">
<td><p>64</p></td>
<td><p>MC</p></td>
<td><p>MM</p></td>
</tr>
<tr class="odd">
<td><p>128</p></td>
<td><p>Attendant</p></td>
<td><p>Attendant</p></td>
</tr>
<tr class="even">
<td><p>256</p></td>
<td><p>Conferencing_Announcement_Service_1.0</p></td>
<td><p>CAS</p></td>
</tr>
<tr class="odd">
<td><p>512</p></td>
<td><p>Conferencing_Attendant_1.0</p></td>
<td><p>CAA</p></td>
</tr>
<tr class="even">
<td><p>512</p></td>
<td><p>Conference_Auto_Attendant_1.0</p></td>
<td><p>CAA</p></td>
</tr>
<tr class="odd">
<td><p>1024</p></td>
<td><p>Response_Group_Service</p></td>
<td><p>RGS</p></td>
</tr>
<tr class="even">
<td><p>1032</p></td>
<td><p>Call_Park_Service_1.0</p></td>
<td><p>CPS</p></td>
</tr>
<tr class="odd">
<td><p>1040</p></td>
<td><p>Response_Group_Service Announcement_Service</p></td>
<td><p>AS</p></td>
</tr>
<tr class="even">
<td><p>2048</p></td>
<td><p>Microsoft.Rtc.Applications.Ccs</p></td>
<td><p>CCS</p></td>
</tr>
<tr class="odd">
<td><p>16386</p></td>
<td><p>CoMo</p></td>
<td><p>CoMo</p></td>
</tr>
<tr class="even">
<td><p>16387</p></td>
<td><p>CWA</p></td>
<td><p>CWA</p></td>
</tr>
<tr class="odd">
<td><p>16388</p></td>
<td><p>InboundRouting</p></td>
<td><p>InboundRouting</p></td>
</tr>
<tr class="even">
<td><p>16389</p></td>
<td><p>ComoSvc</p></td>
<td><p>ComoSvc</p></td>
</tr>
<tr class="odd">
<td><p>16393</p></td>
<td><p>MSExchangeUM</p></td>
<td><p>ExUM</p></td>
</tr>
<tr class="even">
<td><p>16395</p></td>
<td><p>ArchivingAgent</p></td>
<td><p>ARCHAGENT</p></td>
</tr>
<tr class="odd">
<td><p>16396</p></td>
<td><p>ST</p></td>
<td><p>ST</p></td>
</tr>
<tr class="even">
<td><p>16397</p></td>
<td><p>applicationsharing</p></td>
<td><p>ASMCU</p></td>
</tr>
<tr class="odd">
<td><p>16398</p></td>
<td><p>WPLync</p></td>
<td><p>WPLync</p></td>
</tr>
<tr class="even">
<td><p>16399</p></td>
<td><p>iPhoneLync</p></td>
<td><p>iPhoneLync</p></td>
</tr>
<tr class="odd">
<td><p>16400</p></td>
<td><p>AndroidLync</p></td>
<td><p>AndroidLync</p></td>
</tr>
<tr class="even">
<td><p>16401</p></td>
<td><p>iPadLync</p></td>
<td><p>iPadLync</p></td>
</tr>
<tr class="odd">
<td><p>16402</p></td>
<td><p>NokiaLync</p></td>
<td><p>NokiaLync</p></td>
</tr>
<tr class="even">
<td><p>16403</p></td>
<td><p>LyncImm</p></td>
<td><p>LyncImm</p></td>
</tr>
<tr class="odd">
<td><p>16404</p></td>
<td><p>PCS</p></td>
<td><p>PCS</p></td>
</tr>
<tr class="even">
<td><p>16405</p></td>
<td><p>LWA</p></td>
<td><p>LWA</p></td>
</tr>
<tr class="odd">
<td><p>16406</p></td>
<td><p>OWA</p></td>
<td><p>OWA</p></td>
</tr>
<tr class="even">
<td><p>16407</p></td>
<td><p>AOC</p></td>
<td><p>AOC</p></td>
</tr>
<tr class="odd">
<td><p>16408</p></td>
<td><p>GCC</p></td>
<td><p>GCC</p></td>
</tr>
<tr class="even">
<td><p>16409</p></td>
<td><p>IMMCU</p></td>
<td><p>IMMCU</p></td>
</tr>
<tr class="odd">
<td><p>16410</p></td>
<td><p>XmppTGW</p></td>
<td><p>XmppGateway</p></td>
</tr>
<tr class="even">
<td><p>32769</p></td>
<td><p>Gateway</p></td>
<td><p>Gateway</p></td>
</tr>
<tr class="odd">
<td><p>32770</p></td>
<td><p>GatewayMediationServerPair</p></td>
<td><p>GatewayMediationServerPair</p></td>
</tr>
</tbody>
</table>


</div>

<span> </span>

</div>

</div>

</div>

