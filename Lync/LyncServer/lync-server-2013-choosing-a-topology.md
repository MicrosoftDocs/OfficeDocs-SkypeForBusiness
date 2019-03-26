---
title: 'Lync Server 2013: Choosing a topology'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Choosing a topology
ms:assetid: 23f2aeb6-fed9-4349-8fba-dcbf18ee4b04
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425716(v=OCS.15)
ms:contentKeyID: 48183634
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Choosing a topology in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

_**Topic Last Modified:** 2013-02-21_

When you choose a topology, you can use one the following supported topology options:

<div>


> [!NOTE]
> Unless otherwise noted, if you have experience with Microsoft Lync Server 2010, you will find the guidance here is largely unchanged.



</div>

  - [Single consolidated edge with private IP addresses and NAT in Lync Server 2013](lync-server-2013-single-consolidated-edge-with-private-ip-addresses-and-nat.md)

  - [Single consolidated edge with public IP addresses in Lync Server 2013](lync-server-2013-single-consolidated-edge-with-public-ip-addresses.md)

  - [Scaled consolidated edge, DNS load balancing with private IP addresses using NAT in Lync Server 2013](lync-server-2013-scaled-consolidated-edge-dns-load-balancing-with-private-ip-addresses-using-nat.md)

  - [Scaled consolidated edge, DNS load balancing with public IP addresses in Lync Server 2013](lync-server-2013-scaled-consolidated-edge-dns-load-balancing-with-public-ip-addresses.md)

  - [Scaled consolidated edge with hardware load balancers in Lync Server 2013](lync-server-2013-scaled-consolidated-edge-with-hardware-load-balancers.md)

<div>


> [!IMPORTANT]
> The internal Edge interface and external Edge interface must use the same type of load balancing. You cannot use DNS load balancing on one Edge interface and hardware load balancing on the other Edge interface.



</div>

The following table summarizes the functionality available with the supported Microsoft Lync Server 2013 topologies. The column headings indicate the functionality available for a given Edge configuration option. Using the Scaled Edge (DNS load balanced) option as an example, you can see that it supports high availability, can use non-routable private IP addresses (with NAT) or routable public IP addresses assigned to the Edge external interfaces, and reduces cost because a hardware load balancer is not required.

Edge failover scenarios supported with DNS Load Balancing are Lync-to-Lync point-to-point sessions, Lync conferencing sessions, Lync-to-PSTN sessions and Office 365. Edge failover scenarios that do not benefit from DNS Load Balancing are failover for remote user Exchange Unified Messaging (UM) (prior to Exchange 2010 SP1), public instant messaging (IM) connectivity, and federation with servers running Office Communications Server.

### Summary of Edge Server Topology Options

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
<th>Topology</th>
<th>High availability</th>
<th>Additional DNS A records required for external Edge Server in the Edge pool</th>
<th>Edge Failover for Lync-to-Lync sessions</th>
<th>Edge Failover for Lync-to-Lync EUM/PIC/OCS Federation sessions</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Single Edge using NAT</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
</tr>
<tr class="even">
<td><p>Single Edge using Public IP</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
</tr>
<tr class="odd">
<td><p>Scaled Edge (DNS Load Balanced) using NAT</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>*</p></td>
</tr>
<tr class="even">
<td><p>Scaled Edge (DNS Load Balanced) using Public IP</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>*</p></td>
</tr>
<tr class="odd">
<td><p>Scaled Edge Hardware load balanced)</p></td>
<td><p>Yes</p></td>
<td><p>No (one DNS A record per VIP)</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
</tr>
</tbody>
</table>


**\*** Failover for public instant messaging (IM) connectivity, and federation with servers running Office Communications Server is not available with DNS load balancing. Exchange UM (remote user) failover using DNS load balancing requires Exchange Server 2010 SP1 or newer.



> [!NOTE]
> Single Edge and Scaled Edge (DNS load balanced) topologies can use:
> <ul><li><p>Routable public IP addresses</p></li>
> <li><p>Non-routable private IP address if symmetric network address translation (NAT) is used</p></li>
>
> <ul><li> If you use public IP address or private IP address with NAT, you will still use the same number of IP addresses based on your configuration choice in Topology Builder. You can configure the Edge Server to use a single IP address with distinct ports per service, or use distinct IP addresses per service, but use the same port (by default, TCP 443).</li></ul>
>
> If you decide to use non-routable private IP addresses with NAT:
> <ul><li><p>You must use routable private IP addresses on all three external interfaces</p></li>
> <li><p>You must configure symmetric NAT for incoming and outgoing traffic</p></li></ul>
>
> Scaled Edge (hardware load balanced) topology must use public IP addresses.



Lync Server 2013 supports placing Access, Web Conferencing, and A/V Edge external interfaces behind a router or firewall that performs network address translation (NAT) for both single and scaled consolidated Edge Server topologies.

Using NAT for all Edge external interfaces requires the use of DNS load balancing. When compared to using hardware load balancers, using DNS load balancing without NAT allows you to reduce the number of public IP address per Edge Server in an Edge pool as described in the following list:

  - Lync Server 2013 Scaled Consolidated Edge (DNS load balanced) Requires three public IP addresses for each Edge Server in an Edge pool.

  - Lync Server 2013 Scaled Consolidated Edge (hardware load balanced) Requires three public IP address for load balancer virtual IP addresses (one time requirement that does not increment as more Edge Servers are added to the pool) plus three public IP addresses per Edge Server in a pool.

### IP Address Requirements for Scaled Consolidated Edge (IP Address per role)

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Number of Edge Servers per pool</th>
<th>Number of required IP addresses Lync Server 2013 (DNS load balanced)</th>
<th>Number of required IP addresses Lync Server 2013 (hardware load balanced)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>2</p></td>
<td><p>6</p></td>
<td><p>3 (1 per VIP) + 6</p></td>
</tr>
<tr class="even">
<td><p>3</p></td>
<td><p>9</p></td>
<td><p>3 (1 per VIP) + 9</p></td>
</tr>
<tr class="odd">
<td><p>4</p></td>
<td><p>12</p></td>
<td><p>3 (1 per VIP) + 12</p></td>
</tr>
<tr class="even">
<td><p>5</p></td>
<td><p>15</p></td>
<td><p>3 (1 per VIP) + 15</p></td>
</tr>
</tbody>
</table>


### IP Address Requirements for Scaled Consolidated Edge (Single IP address for all roles)

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Number of Edge Servers per pool</th>
<th>Number of required IP addresses Lync Server 2013 (DNS load balanced)</th>
<th>Number of required IP addresses Lync Server 2013 (hardware load balanced)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>2</p></td>
<td><p>2</p></td>
<td><p>1 (1 per VIP) + 2</p></td>
</tr>
<tr class="even">
<td><p>3</p></td>
<td><p>3</p></td>
<td><p>1 (1 per VIP) + 3</p></td>
</tr>
<tr class="odd">
<td><p>4</p></td>
<td><p>4</p></td>
<td><p>1 (1 per VIP) + 4</p></td>
</tr>
<tr class="even">
<td><p>5</p></td>
<td><p>5</p></td>
<td><p>1 (1 per VIP) + 5</p></td>
</tr>
</tbody>
</table>


The primary decision points for topology selection are high availability and load balancing. The requirement for high availability can influence the load balancing decision.

  - **High availability**   If you need high availability, deploy at least two Edge Servers in a pool. A single Edge pool will support up to twelve Edge Servers. If more capacity is required, you can deploy multiple Edge pools. As a general rule, 10% of a given user base will need external access.
    
    <div>
    

    > [!IMPORTANT]
    > Topology Builder will allow you to configure up to twenty Edge Servers in a single Edge pool. The tested and supported maximum number of Edge Servers in a pool is twelve and Topology Builder allowing for a number larger than twelve should not be construed as implied support for more than twelve Edge Servers in a single Edge pool.

    
    </div>

  - **Hardware load balancing**   Hardware load balancing is supported for load balancing Lync Server 2013 Edge Servers when using publicly routable IP addresses for the Edge external interfaces. For example, you would use this approach in situations where failover is required for any of the following applications:
    
      - Public IM connectivity
    
      - Federation with companies running Microsoft Office Communications Server 2007 or Microsoft Office Communications Server 2007 R2
    
      - External access to Exchange 2007 Unified Messaging (UM) or Exchange 2010 UM
        
        <div>
        

        > [!IMPORTANT]
        > DNS load balancing for Exchange 2010 SP1 and newer is supported for Exchange UM.

        
        </div>
    
    These three applications will continue to operate, but they are not DNS load balancing aware and will only connect to the first Edge Server in the pool. If that server is unavailable, the connection will fail. For example, if multiple Edge Servers are deployed in a pool to handle the federated traffic load, only one access proxy actually receives traffic while the others are idle.

<div>


> [!IMPORTANT]
> Using DNS load balancing is recommended if you are federating with companies using Lync Server 2010 and Microsoft Office 365. Be aware that there are significant performance impacts if most of your federated partners are using Office Communications Server 2007 or Office Communications Server 2007 R2.



</div>

</div>

<span> </span>

</div>

</div>

</div>

