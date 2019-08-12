---
title: 'Lync Server 2013: Ports and protocols for internal servers'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Ports and protocols for internal servers
ms:assetid: c94063f1-e802-4a61-be90-022fc185335e
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398833(v=OCS.15)
ms:contentKeyID: 48185402
ms.date: 04/06/2016
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Ports and protocols for internal servers in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2016-04-06_

This section summarizes the ports and protocols used by servers, load balancers, and clients in a Lync Server deployment.

<div>


> [!IMPORTANT]  
> Lync and Communicator clients when involved in a one to one communication, is often referred to as peer-to-peer. Technically, the two clients are communicating in a one to one conversation, with the Instant Messaging multipoint control unit (IMMCU) in the middle. The IMMCU is a component of Front End Server. Placing the IMMCU in the required communication workflow allows call detail recording and other features that the Front End Server enables. Communication is from a dynamic source port on the client to the Front End Server port TLS/TCP/5061 (assuming the use of the recommended transport layer security). By design, peer-to-peer communication (as well as multi-party IM) is possible only when Lync Server and the IMMCU is active and available.



</div>

<div>

## Port and Protocol Details

<div>


> [!NOTE]  
> Windows Firewall must be running before you start the Lync Server services on a server, because that is when Lync Server opens the required ports in the firewall.



</div>

For details about firewall configuration for edge components, see [Determine external A/V firewall and port requirements for Lync Server 2013](lync-server-2013-determine-external-a-v-firewall-and-port-requirements.md).

The following table lists the ports that need to be open on each internal server role.

### Required Server Ports (by Server Role)

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
<th>Server role</th>
<th>Service name</th>
<th>Port</th>
<th>Protocol</th>
<th>Notes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>All Servers</p></td>
<td><p>SQL Browser</p></td>
<td><p>1434</p></td>
<td><p>UDP</p></td>
<td><p>SQL Browser for the local replicated copy of the Central Management Store database.</p></td>
</tr>
<tr class="even">
<td><p>Front End Servers</p></td>
<td><p>Lync Server Front-End service</p></td>
<td><p>5060</p></td>
<td><p>TCP</p></td>
<td><p>Optionally used by Standard Edition servers and Front End Servers for static routes to trusted services, such as remote call control servers.</p></td>
</tr>
<tr class="odd">
<td><p>Front End Servers</p></td>
<td><p>Lync Server Front-End service</p></td>
<td><p>5061</p></td>
<td><p>TCP (TLS)</p></td>
<td><p>Used by Standard Edition servers and Front End pools for all internal SIP communications between servers (MTLS), for SIP communications between Server and Client (TLS) and for SIP communications between Front End Servers and Mediation Servers (MTLS). Also used for communications with Monitoring Server.</p></td>
</tr>
<tr class="even">
<td><p>Front End Servers</p></td>
<td><p>Lync Server Front-End service</p></td>
<td><p>444</p></td>
<td><p>HTTPS</p>
<p>TCP</p></td>
<td><p>Used for HTTPS communication between the Focus (the Lync Server component that manages conference state) and the individual servers.</p>
<p>This port is also used for TCP communication between Survivable Branch Appliances and Front End Servers.</p></td>
</tr>
<tr class="odd">
<td><p>Front End Servers</p></td>
<td><p>Lync Server Front-End service</p></td>
<td><p>135</p></td>
<td><p>DCOM and remote procedure call (RPC)</p></td>
<td><p>Used for DCOM based operations such as Moving Users, User Replicator Synchronization, and Address Book Synchronization.</p></td>
</tr>
<tr class="even">
<td><p>Front End Servers</p></td>
<td><p>Lync Server IM Conferencing service</p></td>
<td><p>5062</p></td>
<td><p>TCP</p></td>
<td><p>Used for incoming SIP requests for instant messaging (IM) conferencing.</p></td>
</tr>
<tr class="odd">
<td><p>Front End Servers</p></td>
<td><p>Lync Server Web Conferencing service</p></td>
<td><p>8057</p></td>
<td><p>TCP (TLS)</p></td>
<td><p>Used to listen for Persistent Shared Object Model (PSOM) connections from client.</p></td>
</tr>
<tr class="even">
<td><p>Front End Servers</p></td>
<td><p>Lync Server Web Conferencing Compatibility service</p></td>
<td><p>8058</p></td>
<td><p>TCP (TLS)</p></td>
<td><p>Used to listen for Persistent Shared Object Model (PSOM) connections from the Live Meeting client and previous versions of Lync Server.</p></td>
</tr>
<tr class="odd">
<td><p>Front End Servers</p></td>
<td><p>Lync Server Audio/Video Conferencing service</p></td>
<td><p>5063</p></td>
<td><p>TCP</p></td>
<td><p>Used for incoming SIP requests for audio/video (A/V) conferencing.</p></td>
</tr>
<tr class="even">
<td><p>Front End Servers</p></td>
<td><p>Lync Server Audio/Video Conferencing service</p></td>
<td><p>57501-65535</p></td>
<td><p>TCP/UDP</p></td>
<td><p>Media port range used for video conferencing.</p></td>
</tr>
<tr class="odd">
<td><p>Front End Servers</p></td>
<td><p>Lync Server Web Compatibility service</p></td>
<td><p>80</p></td>
<td><p>HTTP</p></td>
<td><p>Used for communication from Front End Servers to the web farm FQDNs (the URLs used by IIS web components) when HTTPS is not used.</p></td>
</tr>
<tr class="even">
<td><p>Front End Servers</p></td>
<td><p>Lync Server Web Compatibility service</p></td>
<td><p>443</p></td>
<td><p>HTTPS</p></td>
<td><p>Used for communication from Front End Servers to the web farm FQDNs (the URLs used by IIS web components).</p></td>
</tr>
<tr class="odd">
<td><p>Front End Servers</p></td>
<td><p>Lync Server Web Compatibility service</p></td>
<td><p>8080</p></td>
<td><p>TCP and HTTP</p></td>
<td><p>Used by web components for external access.</p></td>
</tr>
<tr class="even">
<td><p>Front End Servers</p></td>
<td><p>Web server component</p></td>
<td><p>4443</p></td>
<td><p>HTTPS</p></td>
<td><p>HTTPS (from Reverse Proxy) and HTTPS Front End inter-pool communications for Autodiscover sign-in.</p></td>
</tr>
<tr class="odd">
<td><p>Front End Servers</p></td>
<td><p>Web server component</p></td>
<td><p>8060</p></td>
<td><p>TCP (MTLS)</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Front End Servers</p></td>
<td><p>Web server component</p></td>
<td><p>8061</p></td>
<td><p>TCP (MTLS)</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Front End Servers</p></td>
<td><p>Mobility Services component</p></td>
<td><p>5086</p></td>
<td><p>TCP (MTLS)</p></td>
<td><p>SIP port used by Mobility Services internal processes</p></td>
</tr>
<tr class="even">
<td><p>Front End Servers</p></td>
<td><p>Mobility Services component</p></td>
<td><p>5087</p></td>
<td><p>TCP (MTLS)</p></td>
<td><p>SIP port used by Mobility Services internal processes</p></td>
</tr>
<tr class="odd">
<td><p>Front End Servers</p></td>
<td><p>Mobility Services component</p></td>
<td><p>443</p></td>
<td><p>HTTPS</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Front End Servers</p></td>
<td><p>Lync Server Conferencing Attendant service (dial-in conferencing)</p></td>
<td><p>5064</p></td>
<td><p>TCP</p></td>
<td><p>Used for incoming SIP requests for dial-in conferencing.</p></td>
</tr>
<tr class="odd">
<td><p>Front End Servers</p></td>
<td><p>Lync Server Conferencing Attendant service (dial-in conferencing)</p></td>
<td><p>5072</p></td>
<td><p>TCP</p></td>
<td><p>Used for incoming SIP requests for Attendant (dial in conferencing).</p></td>
</tr>
<tr class="even">
<td><p>Front End Servers that also run a Collocated Mediation Server</p></td>
<td><p>Lync Server Mediation service</p></td>
<td><p>5070</p></td>
<td><p>TCP</p></td>
<td><p>Used by the Mediation Server for incoming requests from the Front End Server to the Mediation Server.</p></td>
</tr>
<tr class="odd">
<td><p>Front End Servers that also run a Collocated Mediation Server</p></td>
<td><p>Lync Server Mediation service</p></td>
<td><p>5067</p></td>
<td><p>TCP (TLS)</p></td>
<td><p>Used for incoming SIP requests from the PSTN gateway to the Mediation Server.</p></td>
</tr>
<tr class="even">
<td><p>Front End Servers that also run a Collocated Mediation Server</p></td>
<td><p>Lync Server Mediation service</p></td>
<td><p>5068</p></td>
<td><p>TCP</p></td>
<td><p>Used for incoming SIP requests from the PSTN gateway to the Mediation Server.</p></td>
</tr>
<tr class="odd">
<td><p>Front End Servers that also run a Collocated Mediation Server</p></td>
<td><p>Lync Server Mediation service</p></td>
<td><p>5081</p></td>
<td><p>TCP</p></td>
<td><p>Used for outgoing SIP requests from the Mediation Server to the PSTN gateway.</p></td>
</tr>
<tr class="even">
<td><p>Front End Servers that also run a Collocated Mediation Server</p></td>
<td><p>Lync Server Mediation service</p></td>
<td><p>5082</p></td>
<td><p>TCP (TLS)</p></td>
<td><p>Used for outgoing SIP requests from the Mediation Server to the PSTN gateway.</p></td>
</tr>
<tr class="odd">
<td><p>Front End Servers</p></td>
<td><p>Lync Server Application Sharing service</p></td>
<td><p>5065</p></td>
<td><p>TCP</p></td>
<td><p>Used for incoming SIP listening requests for application sharing.</p></td>
</tr>
<tr class="even">
<td><p>Front End Servers</p></td>
<td><p>Lync Server Application Sharing service</p></td>
<td><p>49152-65535</p></td>
<td><p>TCP</p></td>
<td><p>Media port range used for application sharing.</p></td>
</tr>
<tr class="odd">
<td><p>Front End Servers</p></td>
<td><p>Lync Server Conferencing Announcement service</p></td>
<td><p>5073</p></td>
<td><p>TCP</p></td>
<td><p>Used for incoming SIP requests for the Lync Server Conferencing Announcement service (that is, for dial-in conferencing).</p></td>
</tr>
<tr class="even">
<td><p>Front End Servers</p></td>
<td><p>Lync Server Call Park service</p></td>
<td><p>5075</p></td>
<td><p>TCP</p></td>
<td><p>Used for incoming SIP requests for the Call Park application.</p></td>
</tr>
<tr class="odd">
<td><p>Front End Servers</p></td>
<td><p>Lync Server Audio Test service</p></td>
<td><p>5076</p></td>
<td><p>TCP</p></td>
<td><p>Used for incoming SIP requests for the Audio Test service.</p></td>
</tr>
<tr class="even">
<td><p>Front End Servers</p></td>
<td><p>Not applicable</p></td>
<td><p>5066</p></td>
<td><p>TCP</p></td>
<td><p>Used for outbound Enhanced 9-1-1 (E9-1-1) gateway.</p></td>
</tr>
<tr class="odd">
<td><p>Front End Servers</p></td>
<td><p>Lync Server Response Group service</p></td>
<td><p>5071</p></td>
<td><p>TCP</p></td>
<td><p>Used for incoming SIP requests for the Response Group application.</p></td>
</tr>
<tr class="even">
<td><p>Front End Servers</p></td>
<td><p>Lync Server Response Group service</p></td>
<td><p>8404</p></td>
<td><p>TCP (MTLS)</p></td>
<td><p>Used for incoming SIP requests for the Response Group application.</p></td>
</tr>
<tr class="odd">
<td><p>Front End Servers</p></td>
<td><p>Lync Server Bandwidth Policy Service</p></td>
<td><p>5080</p></td>
<td><p>TCP</p></td>
<td><p>Used for call admission control by the Bandwidth Policy service for A/V Edge TURN traffic.</p></td>
</tr>
<tr class="even">
<td><p>Front End Servers</p></td>
<td><p>Lync Server Bandwidth Policy Service</p></td>
<td><p>448</p></td>
<td><p>TCP</p></td>
<td><p>Used for call admission control by the Lync Server Bandwidth Policy Service.</p></td>
</tr>
<tr class="odd">
<td><p>Front End Servers where the Central Management store resides</p></td>
<td><p>Lync Server Master Replicator Agent service</p></td>
<td><p>445</p></td>
<td><p>TCP</p></td>
<td><p>Used to push configuration data from the Central Management store to servers running Lync Server.</p></td>
</tr>
<tr class="even">
<td><p>All Servers</p></td>
<td><p>SQL Browser</p></td>
<td><p>1434</p></td>
<td><p>UDP</p></td>
<td><p>SQL Browser for local replicated copy of Central Management store data in local SQL Server instance</p></td>
</tr>
<tr class="odd">
<td><p>All internal servers</p></td>
<td><p>Various</p></td>
<td><p>49152-57500</p></td>
<td><p>TCP/UDP</p></td>
<td><p>Media port range used for audio conferencing on all internal servers. Used by all servers that terminate audio: Front End Servers (for Lync Server Conferencing Attendant service, Lync Server Conferencing Announcement service, and Lync Server Audio/Video Conferencing service), and Mediation Server.</p></td>
</tr>
<tr class="even">
<td><p>Office Web Apps Servers</p></td>
<td></td>
<td><p>443</p></td>
<td></td>
<td><p>Used by Lync Server 2013 to connect to Office Web Apps Server.</p></td>
</tr>
<tr class="odd">
<td><p>Directors</p></td>
<td><p>Lync Server Front-End service</p></td>
<td><p>5060</p></td>
<td><p>TCP</p></td>
<td><p>Optionally used for static routes to trusted services, such as remote call control servers.</p></td>
</tr>
<tr class="even">
<td><p>Directors</p></td>
<td><p>Lync Server Front-End service</p></td>
<td><p>444</p></td>
<td><p>HTTPS</p>
<p>TCP</p></td>
<td><p>Inter-server communication between Front End and Director. Additionally, client certificate publish (to Front End Servers) or validate if the client certificate has already been published.</p></td>
</tr>
<tr class="odd">
<td><p>Directors</p></td>
<td><p>Lync Server Web Compatibility service</p></td>
<td><p>80</p></td>
<td><p>TCP</p></td>
<td><p>Used for initial communication from Directors to the web farm FQDNs (the URLs used by IIS web components). In normal operation, will switch to HTTPS traffic, using port 443 and protocol type TCP.</p></td>
</tr>
<tr class="even">
<td><p>Directors</p></td>
<td><p>Lync Server Web Compatibility service</p></td>
<td><p>443</p></td>
<td><p>HTTPS</p></td>
<td><p>Used for communication from Directors to the web farm FQDNs (the URLs used by IIS web components).</p></td>
</tr>
<tr class="odd">
<td><p>Directors</p></td>
<td><p>Lync Server Front-End service</p></td>
<td><p>5061</p></td>
<td><p>TCP</p></td>
<td><p>Used for internal communications between servers and for client connections.</p></td>
</tr>
<tr class="even">
<td><p>Mediation Servers</p></td>
<td><p>Lync Server Mediation service</p></td>
<td><p>5070</p></td>
<td><p>TCP</p></td>
<td><p>Used by the Mediation Server for incoming requests from the Front End Server.</p></td>
</tr>
<tr class="odd">
<td><p>Mediation Servers</p></td>
<td><p>Lync Server Mediation service</p></td>
<td><p>5067</p></td>
<td><p>TCP (TLS)</p></td>
<td><p>Used for incoming SIP requests from the PSTN gateway.</p></td>
</tr>
<tr class="even">
<td><p>Mediation Servers</p></td>
<td><p>Lync Server Mediation service</p></td>
<td><p>5068</p></td>
<td><p>TCP</p></td>
<td><p>Used for incoming SIP requests from the PSTN gateway.</p></td>
</tr>
<tr class="odd">
<td><p>Mediation Servers</p></td>
<td><p>Lync Server Mediation service</p></td>
<td><p>5070</p></td>
<td><p>TCP (MTLS)</p></td>
<td><p>Used for SIP requests from the Front End Servers.</p></td>
</tr>
<tr class="even">
<td><p>Persistent Chat Front End Server</p></td>
<td><p>Persistent Chat SIP</p></td>
<td><p>5041</p></td>
<td><p>TCP (MTLS)</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Persistent Chat Front End Server</p></td>
<td><p>Persistent Chat Windows Communication Foundation (WCF)</p></td>
<td><p>881</p></td>
<td><p>TCP (TLS) and TCP (MTLS)</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Persistent Chat Front End Server</p></td>
<td><p>Persistent Chat File Transfer Service</p></td>
<td><p>443</p></td>
<td><p>TCP (TLS)</p></td>
<td></td>
</tr>
</tbody>
</table>


<div>


> [!NOTE]  
> Some remote call control scenarios require a TCP connection between the Front End Server or Director and the PBX. Although Lync Server no longer uses TCP port 5060, during remote call control deployment you create a trusted server configuration, which associates the RCC Line Server FQDN with the TCP port that the Front End Server or Director will use to connect to the PBX system. For details, see the <STRONG>CsTrustedApplicationComputer</STRONG> cmdlet in the Lync Server Management Shell documentation.



</div>

For your pools that use only hardware load balancing (not DNS load balancing), the following table shows the ports that need to open the hardware load balancers.

### Hardware Load Balancer Ports if Using Only Hardware Load Balancing

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Load Balancer</th>
<th>Port</th>
<th>Protocol</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Front End Server load balancer</p></td>
<td><p>5061</p></td>
<td><p>TCP (TLS)</p></td>
</tr>
<tr class="even">
<td><p>Front End Server load balancer</p></td>
<td><p>444</p></td>
<td><p>HTTPS</p></td>
</tr>
<tr class="odd">
<td><p>Front End Server load balancer</p></td>
<td><p>135</p></td>
<td><p>DCOM and remote procedure call (RPC)</p></td>
</tr>
<tr class="even">
<td><p>Front End Server load balancer</p></td>
<td><p>80</p></td>
<td><p>HTTP</p></td>
</tr>
<tr class="odd">
<td><p>Front End Server load balancer</p></td>
<td><p>8080</p></td>
<td><p>TCP - Client and device retrieval of root certificate from Front End Server – clients and devices authenticated by NTLM</p></td>
</tr>
<tr class="even">
<td><p>Front End Server load balancer</p></td>
<td><p>443</p></td>
<td><p>HTTPS</p></td>
</tr>
<tr class="odd">
<td><p>Front End Server load balancer</p></td>
<td><p>4443</p></td>
<td><p>HTTPS (from reverse proxy)</p></td>
</tr>
<tr class="even">
<td><p>Front End Server load balancer</p></td>
<td><p>5072</p></td>
<td><p>TCP</p></td>
</tr>
<tr class="odd">
<td><p>Front End Server load balancer</p></td>
<td><p>5073</p></td>
<td><p>TCP</p></td>
</tr>
<tr class="even">
<td><p>Front End Server load balancer</p></td>
<td><p>5075</p></td>
<td><p>TCP</p></td>
</tr>
<tr class="odd">
<td><p>Front End Server load balancer</p></td>
<td><p>5076</p></td>
<td><p>TCP</p></td>
</tr>
<tr class="even">
<td><p>Front End Server load balancer</p></td>
<td><p>5071</p></td>
<td><p>TCP</p></td>
</tr>
<tr class="odd">
<td><p>Front End Server load balancer</p></td>
<td><p>5080</p></td>
<td><p>TCP</p></td>
</tr>
<tr class="even">
<td><p>Front End Server load balancer</p></td>
<td><p>448</p></td>
<td><p>TCP</p></td>
</tr>
<tr class="odd">
<td><p>Mediation Server load balancer</p></td>
<td><p>5070</p></td>
<td><p>TCP</p></td>
</tr>
<tr class="even">
<td><p>Front End Server load balancer (if the pool also runs Mediation Server)</p></td>
<td><p>5070</p></td>
<td><p>TCP</p></td>
</tr>
<tr class="odd">
<td><p>Director load balancer</p></td>
<td><p>443</p></td>
<td><p>HTTPS</p></td>
</tr>
<tr class="even">
<td><p>Director load balancer</p></td>
<td><p>444</p></td>
<td><p>HTTPS</p></td>
</tr>
<tr class="odd">
<td><p>Director load balancer</p></td>
<td><p>5061</p></td>
<td><p>TCP</p></td>
</tr>
<tr class="even">
<td><p>Director load balancer</p></td>
<td><p>4443</p></td>
<td><p>HTTPS (from reverse proxy)</p></td>
</tr>
</tbody>
</table>


Your Front End pools and Director pools that use DNS load balancing also must have a hardware load balancer deployed. The following table shows the ports that need to be open on these hardware load balancers.

### Hardware Load Balancer Ports if Using DNS Load Balancing

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Load Balancer</th>
<th>Port</th>
<th>Protocol</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Front End Server load balancer</p></td>
<td><p>80</p></td>
<td><p>HTTP</p></td>
</tr>
<tr class="even">
<td><p>Front End Server load balancer</p></td>
<td><p>443</p></td>
<td><p>HTTPS</p></td>
</tr>
<tr class="odd">
<td><p>Front End Server load balancer</p></td>
<td><p>8080</p></td>
<td><p>TCP - Client and device retrieval of root certificate from Front End Server – clients and devices authenticated by NTLM</p></td>
</tr>
<tr class="even">
<td><p>Front End Server load balancer</p></td>
<td><p>4443</p></td>
<td><p>HTTPS (from reverse proxy)</p></td>
</tr>
<tr class="odd">
<td><p>Director load balancer</p></td>
<td><p>443</p></td>
<td><p>HTTPS</p></td>
</tr>
<tr class="even">
<td> </td>
<td> </td>
<td> </td>
</tr>
<tr class="odd">
<td><p>Director load balancer</p></td>
<td><p>4443</p></td>
<td><p>HTTPS (from reverse proxy)</p></td>
</tr>
</tbody>
</table>


### Required Client Ports

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
<th>Port</th>
<th>Protocol</th>
<th>Notes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Clients</p></td>
<td><p>67/68</p></td>
<td><p>DHCP</p></td>
<td><p>Used by Lync Server to find the Registrar FQDN (that is, if DNS SRV fails and manual settings are not configured).</p></td>
</tr>
<tr class="even">
<td><p>Clients</p></td>
<td><p>443</p></td>
<td><p>TCP (TLS)</p></td>
<td><p>Used for client-to-server SIP traffic for external user access.</p></td>
</tr>
<tr class="odd">
<td><p>Clients</p></td>
<td><p>443</p></td>
<td><p>TCP (PSOM/TLS)</p></td>
<td><p>Used for external user access to web conferencing sessions.</p></td>
</tr>
<tr class="even">
<td><p>Clients</p></td>
<td><p>443</p></td>
<td><p>TCP (STUN/MSTURN)</p></td>
<td><p>Used for external user access to A/V sessions and media (TCP)</p></td>
</tr>
<tr class="odd">
<td><p>Clients</p></td>
<td><p>3478</p></td>
<td><p>UDP (STUN/MSTURN)</p></td>
<td><p>Used for external user access to A/V sessions and media (UDP)</p></td>
</tr>
<tr class="even">
<td><p>Clients</p></td>
<td><p>5061</p></td>
<td><p>TCP (MTLS)</p></td>
<td><p>Used for client-to-server SIP traffic for external user access.</p></td>
</tr>
<tr class="odd">
<td><p>Clients</p></td>
<td><p>6891-6901</p></td>
<td><p>TCP</p></td>
<td><p>Used for file transfer between Lync clients and previous clients (clients of Microsoft Office Communications Server 2007 R2, Microsoft Office Communications Server 2007, and Live Communications Server 2005).</p></td>
</tr>
<tr class="even">
<td><p>Clients</p></td>
<td><p>1024-65535 *</p></td>
<td><p>TCP/UDP</p></td>
<td><p>Audio port range (minimum of 20 ports required)</p></td>
</tr>
<tr class="odd">
<td><p>Clients</p></td>
<td><p>1024-65535 *</p></td>
<td><p>TCP/UDP</p></td>
<td><p>Video port range (minimum of 20 ports required).</p></td>
</tr>
<tr class="even">
<td><p>Clients</p></td>
<td><p>1024-65535 *</p></td>
<td><p>TCP</p></td>
<td><p>Peer-to-peer file transfer (for conferencing file transfer, clients use PSOM).</p></td>
</tr>
<tr class="odd">
<td><p>Clients</p></td>
<td><p>1024-65535 *</p></td>
<td><p>TCP</p></td>
<td><p>Application sharing.</p></td>
</tr>
<tr class="even">
<td><p>Aastra 6721ip common area phone</p>
<p>Aastra 6725ip desk phone</p>
<p>HP 4110 IP Phone (common area phone)</p>
<p>HP 4120 IP Phone (desk phone)</p>
<p>Polycom CX500 IP common area phone</p>
<p>Polycom CX600 IP desk phone</p>
<p>Polycom CX700 IP desk phone</p>
<p>Polycom CX3000 IP conference phone</p></td>
<td><p>67/68</p></td>
<td><p>DHCP</p></td>
<td><p>Used by the listed devices to find the Lync Server certificate, provisioning FQDN, and Registrar FQDN.</p></td>
</tr>
</tbody>
</table>


**\*** To configure specific ports for these media types, use the CsConferencingConfiguration cmdlet (ClientMediaPortRangeEnabled, ClientMediaPort, and ClientMediaPortRange parameters).

<div>


> [!NOTE]  
> The set programs for Lync clients automatically create the required operating-system firewall exceptions on the client computer.



</div>

<div>


> [!NOTE]  
> The ports that are used for external user access are required for any scenario in which the client must traverse the organization’s firewall (for example, any external communications or meetings hosted by other organizations).



</div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

