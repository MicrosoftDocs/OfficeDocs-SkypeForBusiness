---
title: 'Lync Server 2013: Scenarios for external user access'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Scenarios for external user access
ms:assetid: 25697446-b045-4d12-9b1c-47f694b4f224
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425727(v=OCS.15)
ms:contentKeyID: 48183640
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Scenarios for external user access in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-08_

Providing external user access for Lync Server 2013 requires that you deploy at least one Edge Server and one reverse proxy in your perimeter network. Optionally, you may deploy a Director or Director pool in your internal network.

If you need greater capacity than a single Edge Server can provide, or if you need high availability for your Edge Server deployment, you can configure load balancing and deploy multiple Edge Servers in a load balanced pool. If your organization has multiple data centers, you can have Edge Server or Edge pool deployments at more than one location. However, only one of the Edge Server deployments can be designated as the federation route.

This section defines the scenarios for Edge Server deployments and maps the planning sections to the possible scenarios. For example, if your deployment requires high availability, federation with extensible messaging and presence (XMPP) contacts, and Lync mobility, you would select the matching entries in the following table that would satisfy these requirements and use the referenced planning sections to define your deployment, as illustrated in the following flowchart.

**Edge Server deployment scenario selection process**

![Sample deployment flowchart](images/Gg425727.007100b5-6923-4909-bfd7-897d8867205f(OCS.15).jpg "Sample deployment flowchart")

By using this process, you can plan for and document the configuration of all potential features that you intend to deploy for your users. However, you can add federation and mobility services after you have deployed the Edge Server and have confirmed the correct operation before adding other features. The process of adding features to an existing Edge Server deployment is covered in the Deployment section. For details on deployment, see [Deploying external user access in Lync Server 2013](lync-server-2013-deploying-external-user-access.md) By including planning for these features during the initial planning process, you can prepare for the DNS, firewall, and certificate requirements for the added features, which enables you to acquire the certificates and configure DNS and port/protocol requirements in advance.

<div>


> [!TIP]  
> If you are planning to install the Edge Servers and reverse proxy and then add features later (for example, federation and mobility), determine what certificates you will require for all services after deployment. Planning for and acquiring the certificates for all features in advance, initially deployed or not, saves you from having to order new certificates to satisfy the requirements of federation (that is, on the Edge Servers) or the reverse proxy (that is, for mobility services).



</div>

<div>


> [!NOTE]  
> All edge services run on each Edge Server. Services cannot be split between two different Edge Servers. If you deploy an Edge pool for scalability, all edge services are deployed on each Edge Server in the pool. XMPP federation, Office Communications Server, and Lync Server federation, public IM connectivity and client mobility are additional services that can be deployed after you have deployed your first Edge Server or Edge pool. Mobility services is a feature that uses the reverse proxy. Installation of mobility services will not add features to your Edge Servers, but will require reconfiguration of your reverse proxy. The <STRONG>Installation goal</STRONG> column that lists these features provides planning guidance in the associated column under <STRONG>Edge Server planning section or sections</STRONG> for concurrently planning these features to be deployed when the Edge Servers are installed and configured.



</div>

<div>

## Identifying and Mapping Your Deployment Goals


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Installation goal</th>
<th>Edge Server planning documentation</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>You have decided that a single server is sufficient for Edge services in your infrastructure. You also intend to use private IP addresses for the Edge server external interfaces with NAT to the Internet.</p>
<p>Use this planning section if you are deploying a single Edge Server in your perimeter. You will deploy an Edge Server with private IP addresses assigned to the Edge Server and will use NAT to provide the public IP addresses for the external users on the Internet.</p></td>
<td><p><a href="lync-server-2013-single-consolidated-edge-with-private-ip-addresses-and-nat.md">Single consolidated edge with private IP addresses and NAT in Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p>You have decided that a single server is sufficient for Edge services in your infrastructure. You also intend to use public IP addresses for the Edge server external interfaces to the Internet.</p>
<p>Use this planning section if you are deploying a single Edge Server in your perimeter. You will deploy an Edge Server with public IP addresses assigned to the Edge Server. Instead of NAT, you will use routing in this scenario. The actual public IP address of the Edge Server are made available for external user connections.</p></td>
<td><p><a href="lync-server-2013-single-consolidated-edge-with-public-ip-addresses.md">Single consolidated edge with public IP addresses in Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p>You have decided that high availability of the Edge services is important to your users and you will deploy two or more Edge Servers in this pool. You also intend to use private IP addresses for the Edge Server external interfaces with NAT to the Internet.</p>
<p>Use this planning section if you are deploying a pool of Edge Servers in your perimeter. You will deploy the Edge Servers with private IP addresses assigned to the Edge Server, using DNS load balancing to distribute communication across the pool. You will use NAT to provide the public IP addresses for the external users on the Internet.</p></td>
<td><p><a href="lync-server-2013-scaled-consolidated-edge-dns-load-balancing-with-private-ip-addresses-using-nat.md">Scaled consolidated edge, DNS load balancing with private IP addresses using NAT in Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p>You have decided that high availability of the Edge services is important to your users and you will deploy two or more Edge Servers in this pool. You also intend to use public IP addresses for the Edge Server external interfaces to the Internet.</p>
<p>Use this planning section if you are deploying a pool of Edge Servers in your perimeter. You will deploy the Edge Servers with public IP addresses assigned to the Edge Server, using DNS load balancing to distribute communication across the pool. Instead of NAT, you will use routing to provide the public IP addresses for the external users on the Internet.</p></td>
<td><p><a href="lync-server-2013-scaled-consolidated-edge-dns-load-balancing-with-public-ip-addresses.md">Scaled consolidated edge, DNS load balancing with public IP addresses in Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p>You have decided that high availability of the Edge services is important to your users and you will deploy two or more Edge Servers in this pool using a hardware load balancer.</p>
<p>Use this planning section if you are deploying a pool of Edge Servers in your perimeter. You will deploy the Edge Servers with public IP addresses assigned to the Edge Server, using hardware load balancers to distribute communication across the pool. Instead of NAT, you will use routing to provide the public IP addresses for the external users on the Internet.</p></td>
<td><p><a href="lync-server-2013-scaled-consolidated-edge-with-hardware-load-balancers.md">Scaled consolidated edge with hardware load balancers in Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p>The federation scenarios allow you to plan for the feature that will extend the types of partners that your users can communicate with.</p>
<ul>
<li><p>Lync Server federation</p></li>
<li><p>Office Communications Server federation</p></li>
<li><p>Public IM connectivity</p></li>
<li><p>XMPP federation</p></li>
</ul></td>
<td><p>Planning for Federation Scenarios</p>
<ul>
<li><p><a href="lync-server-2013-planning-for-lync-server-and-office-communications-server-federation.md">Planning for Lync Server 2013 and Office Communications Server federation</a></p></li>
<li><p><a href="lync-server-2013-planning-for-public-instant-messaging-connectivity.md">Planning for public instant messaging connectivity in Lync Server 2013</a></p></li>
<li><p><a href="lync-server-2013-planning-for-extensible-messaging-and-presence-protocol-xmpp-federation.md">Planning for extensible messaging and presence protocol (XMPP) federation in Lync Server 2013</a></p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Mobility services are offered through the reverse proxy. Services that enable mobility for external users are deployed on the Front End Server or Front End pool. You create or modify existing publishing rules on the reverse proxy to enable mobility services for your external users.</p></td>
<td><p><a href="lync-server-2013-planning-for-mobility.md">Planning for mobility in Lync Server 2013</a></p></td>
</tr>
</tbody>
</table>


<div>


> [!TIP]  
> In the following Scenarios sections are reference architectures, example DNS, port/protocol definitions, and certificate requirements. Also included are diagrams for your DNS, port/protocol definitions and certificate needs. The diagrams will provide a template for you to fill in and distribute to other teams (for example, your organization’s Network Team, Public Key Infrastructure Team, and Server Deployment Team). The goal of the diagrams is to enhance communication and to ensure success when communicating the required Edge Server configuration elements to the people who will do the actual configuration work. We recommend that you use the diagrams and associated reference architectures to plan your deployment.



</div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

