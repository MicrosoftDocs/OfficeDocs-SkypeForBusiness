---
title: Lync Server 2013 network infrastructure requirements
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Network infrastructure requirements
ms:assetid: 35c7bb3f-8e0f-48b7-8a2c-857d4b42a4c4
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425841(v=OCS.15)
ms:contentKeyID: 48183804
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Network infrastructure requirements for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-18_

The network adapter card of each server in the Lync Server 2013 topology must support at least 1 gigabit per second (Gbps). In general, you should connect all server roles within the Lync Server topology using a low latency and high bandwidth local area network (LAN). The size of the LAN is dependent on the size of the topology:

  - In Standard Edition topologies, servers should be in a network that supports 1 Gbps Ethernet or equivalent.

  - In Front End pool topologies, most servers should be in a network that supports more than 1 Gbps, especially when supporting audio/video (A/V) conferencing and application sharing.

For public switched telephone network (PSTN) integration, you can integrate by using either T1/E1 lines or SIP trunking.

<div>

## Audio/Video Network Requirements

Network requirements for audio/video (A/V) in a Lync Server deployment include the following:

  - If you are deploying a single Edge Server or an Edge pool using DNS load balancing, you can configure the external firewall as a NAT. You cannot configure the internal firewall as a NAT. For details about these requirements, see [Determine external A/V firewall and port requirements for Lync Server 2013](lync-server-2013-determine-external-a-v-firewall-and-port-requirements.md) in the Planning documentation.
    
    <div>
    

    > [!IMPORTANT]  
    > If you have an Edge pool and are using a hardware load balancer, you must use public IP addresses on each of the Edge Servers and you cannot use NAT for the servers or the pool at your NAT device (for example, the firewall, or other infrastructure device that would NAT inbound or outbound traffic). For details, see <A href="lync-server-2013-port-summary-scaled-consolidated-edge-with-hardware-load-balancers.md">Port summary - Scaled consolidated edge with hardware load balancers in Lync Server 2013</A> in the Planning for External User Access documentation.

    
    </div>

  - If your organization uses a Quality of Service (QoS) infrastructure, the media subsystem is designed to work within this existing infrastructure.

  - If you use Internet Protocol security (IPsec), we recommend disabling IPsec over the port ranges used for A/V traffic. For details, see [IPsec exceptions in Lync Server 2013](lync-server-2013-ipsec-exceptions.md) in the Planning documentation.

To ensure optimal media quality, do the following:

  - Provision your network links to support throughput of 65 kilobits per second (Kbps) per audio stream and 500 Kbps per video stream, if enabled, during peak usage periods. A bidirectional audio or video session consists of two streams.

  - To cope with unexpected spikes in traffic above this level and increased usage over time, Lync Server media endpoints can adapt to varying network conditions and support loads of three times the throughput (see previous paragraph) for audio and video while still retaining acceptable quality. However, do not assume that this adaptability will support an under-provisioned network. In an under-provisioned network, the ability of the Lync Server media endpoints to dynamically deal with varying network conditions (for example, temporary high packet loss) is reduced.

  - For network links where provisioning is extremely costly and difficult, you may need to consider provisioning for a lower volume of traffic. In this scenario, let the elasticity of the Lync Server media endpoints absorb the difference between the traffic volume and the peak traffic level, at the cost of some reduction in the voice quality. Also, there is a decrease in the headroom otherwise available to absorb sudden peaks in traffic.

  - For links that cannot be correctly provisioned in the short term (for example, a site with very poor WAN links), consider disabling video for certain users.

  - Provision your network to ensure a maximum end-to-end delay (latency) of 150 milliseconds (ms) under peak load. Latency is the one network impairment that Lync Server media components cannot reduce, and it is important to find and eliminate the weak points.

  - For servers running antivirus software, include all servers running Lync Server in the exception list in order to provide optimal performance and audio quality.

</div>

<div>

## Conferencing Network Requirements

The bandwidth that is used to download conference content from the Internet Information Services (IIS) server depends on the size of the content that is uploaded.

</div>

</div>

<span> </span>

</div>

</div>

</div>

