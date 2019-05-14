---
title: 'Lync Server 2013: DNS summary - Reverse proxy'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: DNS summary - Reverse proxy
ms:assetid: 3073affa-4d92-4453-9974-3a82ca0c6445
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204781(v=OCS.15)
ms:contentKeyID: 48183755
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# DNS summary - Reverse proxy in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-22_

You configure two network adapters in your reverse proxy as follows:

<div>

## Reverse Proxy Network Adapter Requirements

  - **Network adapter 1 (Internal Interface)** example
    
    Internal interface with 172.25.33.40 assigned.
    
    No default gateway is defined.
    
    Ensure there is a route from the network containing the reverse proxy internal interface to any networks that contain Lync Server Front End pool servers (for example, from 172.25.33.0 to 192.168.10.0).

  - **Network adapter 2 (External Interface)** example
    
    A minimum of one public IP address is assigned to this network adapter.
    
    Gateway is defined to point to the router or integrated firewall in your outer perimeter. (10.45.16.1 in the scenario examples)

### DNS Records Required for Reverse Proxy

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
<th>IP address</th>
<th>Maps to/comments</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>External DNS/A</p></td>
<td><p>webext.contoso.com</p></td>
<td><p>Assigned listener for externally published resources</p></td>
<td><p>External web services from the internal deployment. Additional records can be defined and created for all pools and single servers for any SIP domain that will use this reverse proxy, and has defined external web services.</p></td>
</tr>
<tr class="even">
<td><p>External DNS/A</p></td>
<td><p>webdirext.contoso.com</p></td>
<td><p>Assigned listener for externally published resources</p></td>
<td><p>External web services for the Directors or Director pools in your deployment. You can define as many Directors as there are distinct Directors, of which may be associated with other SIP domains.</p>
<div>

> [!IMPORTANT]  
> Defining the DNS records for and publishing the Directors is not an either the Front End pool or the Director decision. You must define and publish both the Director and the Front End pool external web services if you are using Directors. Specific traffic types (for authentication and other uses) will be sent to the Director first, if it is defined in the topology.


</div></td>
</tr>
<tr class="odd">
<td><p>External DNS/A</p></td>
<td><p>dialin.contoso.com</p></td>
<td><p>Assigned listener for externally published resources</p></td>
<td><p>Dial-in conferencing published externally</p></td>
</tr>
<tr class="even">
<td><p>External DNS/A</p></td>
<td><p>meet.contoso.com</p></td>
<td><p>Assigned listener for externally published resources</p></td>
<td><p>Conferences published externally</p></td>
</tr>
<tr class="odd">
<td><p>External DNS/A</p></td>
<td><p>officewebapps01.contoso.com</p></td>
<td><p>Assigned listener for Office Web Apps Server</p></td>
<td><p>Office Web Apps Server deployed internally or in the perimeter, and published for external client access</p></td>
</tr>
<tr class="even">
<td><p>External DNS/A</p></td>
<td><p>lyncdiscover.contoso.com</p></td>
<td><p>Assigned listener for externally published resources</p></td>
<td><p>Lync Discover External record for externally published AutoDiscover, and includes Mobility, Microsoft Lync Web App, and scheduler Web app</p></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

