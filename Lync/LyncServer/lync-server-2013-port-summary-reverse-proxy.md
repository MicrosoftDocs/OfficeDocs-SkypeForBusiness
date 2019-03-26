---
title: 'Lync Server 2013: Port summary - Reverse proxy'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Port summary - Reverse proxy
ms:assetid: 59b9ac3c-3e6f-4776-b366-174f0dd1f2eb
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204932(v=OCS.15)
ms:contentKeyID: 48184251
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Port summary - Reverse proxy in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-15_

The reverse proxy has minimal requirements for firewall and port/protocol.

  - External firewall requirements are the HTTPS/TCP/443 and the optional HTTP/TCP/80. HTTPS is used for SSL and TLS secure communications through the reverse proxy. HTTP is used if you choose to allow access to the Autodiscover Service when modifying certificates might prove difficult or not cost justified.

  - Clients expect to contact the Office Web Apps Server on HTTPS. The Office Web Apps Server expects communication from internal clients on HTTPS/TCP/443. The recommended configuration is to allow HTTPS/TCP/443 from the reverse proxy to the Office Web Apps Server.

  - Port 8080 is used to route traffic from the reverse proxy internal interface to the Front End Server, Front End pool virtual IP (VIP) or the optional Director or Director pool VIP. Port TCP 8080 is required for mobile devices running Lync to locate the Autodiscover Service in situations where modifying the external web service publishing rule certificate is undesirable (for example, if you have a large number of SIP domains). If you choose to acquire new certificates with the necessary SAN entries, the port TCP 8080 is not needed and is optional.

  - Port 4443 is used for traffic from the reverse proxy internal interface to the Front End Server, Front End pool virtual IP (VIP) or the optional Director or Director pool VIP
    
    ![13142405-d5c9-45b7-a8b7-a8c89f09c97c](images/JJ204932.13142405-d5c9-45b7-a8b7-a8c89f09c97c(OCS.15).jpg "13142405-d5c9-45b7-a8b7-a8c89f09c97c")  
    
    <div>
    

    > [!WARNING]  
    > Do not confuse the 4443 over TCP from the reverse proxy to the internal deployment for the port 4443 over TCP traffic from the Standard Edition server or the Front End pool that manages the Central Management store role.

    
    </div>

<div>

## Port and Protocol Details

### Firewall Details for Reverse Proxy Server: External Interface

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Protocol/TCP or UDP/Port</th>
<th>Source IP Address</th>
<th>Destination IP Address</th>
<th>Notes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>HTTP/TCP/80</p></td>
<td><p>Any</p></td>
<td><p>Reverse proxy listener</p></td>
<td><p>(Optional) Redirection to HTTPS if user enters http://&lt;publishedSiteFQDN&gt;.</p>
<p>Also required if using Office Web Apps for conferencing and the Autodiscover Service for mobile devices running Lync in situations where the organization does not want to modify the external web service publishing rule certificate.</p></td>
</tr>
<tr class="even">
<td><p>HTTPS/TCP/443</p></td>
<td><p>Any</p></td>
<td><p>Reverse proxy listener</p></td>
<td><p>Address book downloads, Address Book Web Query service, Autodiscover, client updates, meeting content, device updates, group expansion, Office Web Apps for conferencing, dial-in conferencing, and meetings.</p></td>
</tr>
</tbody>
</table>


### Firewall Details for Reverse Proxy Server: Internal Interface

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Protocol/TCP or UDP/Port</th>
<th>Source IP Address</th>
<th>Destination IP Address</th>
<th>Notes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>HTTP/TCP/8080</p></td>
<td><p>Internal reverse proxy interface</p></td>
<td><p>Front End Server, Front End pool, Director, Director pool</p></td>
<td><p>Required if using the Autodiscover Service for mobile devices running Lync in situations where the organization does not want to modify the external web service publishing rule certificate.</p>
<p>Traffic sent to port 80 on the reverse proxy external interface is redirected to a pool on port 8080 from the reverse proxy internal interface so that the pool Web Services can distinguish it from internal web traffic.</p></td>
</tr>
<tr class="even">
<td><p>HTTPS/TCP/4443</p></td>
<td><p>Internal reverse proxy interface</p></td>
<td><p>Front End Server, Front End pool, Director, Director pool</p></td>
<td><p>Traffic sent to port 443 on the reverse proxy external interface is redirected to a pool on port 4443 from the reverse proxy internal interface so that the pool web services can distinguish it from internal web traffic.</p></td>
</tr>
<tr class="odd">
<td><p>HTTPS/TCP/443</p></td>
<td><p>Internal reverse proxy interface</p></td>
<td><p>Office Web Apps for conferencing</p></td>
<td></td>
</tr>
</tbody>
</table>


</div>

</div>

<span> </span>

</div>

</div>

</div>

