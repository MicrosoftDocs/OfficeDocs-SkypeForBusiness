---
title: 'Lync Server 2013: Network settings for the advanced Enterprise Voice features'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Network settings for the advanced Enterprise Voice features
ms:assetid: 7f6de9e4-c8a4-44e4-8d14-21fe8c45283a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398637(v=OCS.15)
ms:contentKeyID: 48184632
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Network settings for the advanced Enterprise Voice features in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-10_

Lync Server has three advanced Enterprise Voice features: call admission control (CAC), emergency services (E9-1-1), and media bypass. These features share certain configuration requirements for network regions, network sites, and association of each subnet in the Lync Server topology with a network site. For details about planning for deployment of these features, see:

  - [Planning for call admission control in Lync Server 2013](lync-server-2013-planning-for-call-admission-control.md)

  - [Planning for emergency services (E9-1-1) in Lync Server 2013](lync-server-2013-planning-for-emergency-services-e9-1-1.md)

  - [Planning for media bypass in Lync Server 2013](lync-server-2013-planning-for-media-bypass.md)

For details about deploying each of these features, see [Deploying advanced Enterprise Voice features in Lync Server 2013](lync-server-2013-deploying-advanced-enterprise-voice-features.md) in the Deployment documentation.

This topic provides an overview of the configuration requirements that are common to all three advanced Enterprise Voice features.

<div>

## Network Regions

A network region is a network hub or network backbone used only in the configuration of call admission control (CAC), E9-1-1, and media bypass.

<div>


> [!NOTE]  
> Network regions are not the same as Lync Server dial-in conferencing regions, which are required to associate dial-in conferencing access numbers with one or more Lync Server dial plans. For details about dial-in conferencing regions, see <A href="lync-server-2013-dial-in-conferencing-requirements.md">Dial-in conferencing requirements in Lync Server 2013</A> in the Planning documentation.



</div>

CAC requires that every network region have an associated Lync Server central site, which manages media traffic within the region (that is, it makes decisions based on policies that you have configured, regarding whether or not a real-time audio or video session can be established). Lync Server central sites do not represent geographical locations, but rather logical groups of servers that are configured as a pool or a set of pools. For details about central sites, see [Reference topologies in Lync Server 2013](lync-server-2013-reference-topologies.md) in the Planning documentation. Also see [Supported topologies in Lync Server 2013](lync-server-2013-supported-topologies.md) in the Supportability documentation.

To configure a network region, you can either use the **Regions** tab on the **Network Configuration** section of Lync Server Control Panel, or run the **New-CsNetworkRegion** or **Set-CsNetworkRegion** Lync Server Management Shell cmdlets. For instructions, see [Create or modify a network region in Lync Server 2013](lync-server-2013-create-or-modify-a-network-region.md) in the Deployment documentation, or refer to the Lync Server Management Shell documentation.

The same network region definitions are shared by all three advanced Enterprise Voice features. If you have already created network regions for one feature, you do not need to create new network regions for the other features. You may, however, need to modify an existing network region definition to apply feature-specific settings. For example, if you have created network regions for E9-1-1 (which do not require an associated central site) and, later, you deploy call admission control, you must modify each of the network region definitions to specify a central site.

To associate a Lync Server central site with a network region, you specify the central site name, either by using the **Network Configuration** section of Lync Server Control Panel, or by running the **New-CsNetworkRegion** or **Set-CsNetworkRegion** Lync Server Management Shell cmdlets. For instructions, see [Create or modify a network region in Lync Server 2013](lync-server-2013-create-or-modify-a-network-region.md) in the Deployment documentation, or refer to the Lync Server Management Shell documentation.

</div>

<div>

## Network Sites

A network site represents a geographical location, such as a branch office, a regional office, or a main office. Each network site must be associated with a specific network region.

<div>


> [!NOTE]  
> Network sites are used only by the advanced Enterprise Voice features. They are not the same as the branch sites that you configure in your Lync Server topology. For details about branch sites, see <A href="lync-server-2013-reference-topologies.md">Reference topologies in Lync Server 2013</A> in the Planning documentation. Also see <A href="lync-server-2013-supported-topologies.md">Supported topologies in Lync Server 2013</A> in the Supportability documentation.



</div>

To configure a network site and associate it with a network region, you can either use the **Network Configuration** section of Lync Server Control Panel, or run the Lync Server Management Shell **New-CsNetworkSite** or **Set-CsNetworkSite** cmdlets. For details, see [Create or modify a network site in Lync Server 2013](lync-server-2013-create-or-modify-a-network-site.md) in the Deployment documentation, or refer to the Lync Server Management Shell documentation.

</div>

<div>

## Identify IP Subnets

For each network site, you will need to work with your network administrator to determine which IP subnets are assigned to each network site. If your network administrator has already organized the IP subnets into network regions and network sites, then your work is significantly simplified.

For example, the New York site in the North America region can be assigned the following IP subnets: 172.29.80.0/23, 157.57.216.0/25, 172.29.91.0/23, 172.29.81.0/24. If Bob, who usually works in Detroit, travels to the New York office for training, turns on his computer and connects to the network, his computer will get an IP address in one of the four ranges that are allocated for New York—for example, 172.29.80.103.

<div>


> [!WARNING]  
> The IP subnets specified during network configuration on the server must match the format that is provided by client computers in order to be properly used for media bypass. A Lync client takes its local IP address and masks the IP address with the associated subnet mask. When determining the bypass ID associated with each client, the Registrar will compare the list of IP subnets associated with each network site against the subnet that is provided by the client for an exact match. For this reason, it is important that subnets entered during network configuration on the server are actual subnets instead of virtual subnets. (If you deploy call admission control, but not media bypass, call admission control will function properly even if you configure virtual subnets.)<BR>For example, if a Lync client signs in on a computer with an IP address of 172.29.81.57 with an IP subnet mask of 255.255.255.0, it will request the bypass ID that is associated with subnet 172.29.81.0. If the subnet is defined as 172.29.0.0/16, although the client belongs to the virtual subnet, the Registrar will not consider this a match because the Registrar is specifically looking for subnet 172.29.81.0. Therefore, it is important that the administrator enters subnets exactly as provided by Lync clients (which are provisioned with subnets during network configuration, either statically or by Dynamic Host Configuration Protocol (DHCP).)



</div>

</div>

<div>

## Associating Subnets with Network Sites

Every subnet in the enterprise network must be associated with a network site (that is, every subnet needs to be associated with a geographic location). This association of subnets enables the advanced Enterprise Voice features to locate the endpoints geographically. For example, locating the endpoints enables CAC to regulate the flow of real-time audio and video data going to and from the network site.

To associate subnets with network sites, you can either use the **Network Configuration** section of Lync Server Control Panel, or you can use the Lync Server Management Shell. For instructions, see [Associate a subnet with a network site in Lync Server 2013](lync-server-2013-associate-a-subnet-with-a-network-site.md) in the Deployment documentation, or refer to the Lync Server Management Shell documentation.

</div>

<div>

## See Also


[Planning for call admission control in Lync Server 2013](lync-server-2013-planning-for-call-admission-control.md)  
[Planning for emergency services (E9-1-1) in Lync Server 2013](lync-server-2013-planning-for-emergency-services-e9-1-1.md)  
[Planning for media bypass in Lync Server 2013](lync-server-2013-planning-for-media-bypass.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

