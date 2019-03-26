---
title: 'Lync Server 2013: Overview of call admission control'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Overview of call admission control
ms:assetid: 6fda0195-4c89-4dea-82e8-624f03e3d062
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398529(v=OCS.15)
ms:contentKeyID: 48184474
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Overview of call admission control in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-22_

Real-time communications are sensitive to the latency and packet loss that can occur on congested networks. Call admission control (CAC) determines, based on available network bandwidth, whether to allow real-time communications sessions such as voice or video calls to be established. The CAC design in Lync Server 2013 offers four main attributes:

  - It is simple to deploy and manage without requiring additional equipment, such as specially configured routers.

  - It addresses critical unified communications use cases, such as roaming users and multiple points of presence. CAC policies are enforced according to where the endpoint is located, not where the user is homed.

  - In addition to voice calls, it can be applied to other traffic, such as video calls and audio/video conferencing sessions.

  - Provides the flexibility to enable representation of various kinds of network topologies. For examples, see [Components and topologies for CAC in Lync Server 2013](lync-server-2013-components-and-topologies-for-cac.md).

If a new voice or video session exceeds the bandwidth limits that you have set on a WAN link, the session is either blocked or (for phone calls only) rerouted to the PSTN.

CAC controls real-time traffic for voice and video only. It does not control data traffic.

Administrators define CAC policies, which are enforced by the Bandwidth Policy Service that is installed with every Front End pool. CAC settings are automatically propagated to all Lync Server Front End Servers in your network.

For calls that fail because of CAC policies, the order of precedence for rerouting the call is as follows:

1.  Internet

2.  PSTN

3.  Voice mail

Call detail recording (CDR) captures information about calls that are rerouted to the PSTN or to voice mail. CDR does not capture information about calls that are rerouted to the Internet, because the Internet is treated as an alternate path rather than a secondary option.

<div>


> [!NOTE]  
> Voice mail deposits will not be denied because of bandwidth constraints.



</div>

The Bandwidth Policy Service generates two types of log files in comma separated values (CSV) format. The **check failures** log file captures information when bandwidth requests are denied. The **link utilization** log file captures a snapshot of the network topology and the WAN link bandwidth utilization. Both of these log files can assist you in fine-tuning your CAC policies based on utilization.

<div>

## Call Admission Control Considerations

The administrator selects to install the Bandwidth Policy Service on the first pool configured in the central site. Since there is a single central site per network region, there is only one Bandwidth Policy Service per network region, which manages bandwidth policy for that region, its associated sites and the links to those sites. The Bandwidth Policy Service runs as part of the Front End Servers, and therefore high availability is built-in within that pool. The Bandwidth Policy Service running on each Front End Server synchronizes every 15 seconds. If the Front End pool fails, CAC policies are no longer enforced for that site until the Front End pool and consequently the Bandwidth Policy Service becomes operational again. This implies that all calls will go through for the duration the Bandwidth Policy Service is out of service. Therefore there is the possibility of bandwidth oversubscription of your links during this period

The Bandwidth Policy Service provides high availability within a Front End pool; however, it does not provide redundancy across Front End pools. The Bandwidth Policy Service cannot failover from one Front End pool to another. Once service to the Front End pool is restored, the Bandwidth Policy Service is resumed and can enforce bandwidth policy checks again.

<div>

## Network Considerations

Although bandwidth restriction for audio and video is enforced by the Bandwidth Policy Service in Lync Server 2013, this restriction is not enforced at the network router (layer 2 and 3). Lync Server 2010 CAC cannot prevent a data application, for example, from consuming the entire network bandwidth on a WAN link, including the bandwidth that is reserved for audio and video by your CAC policy. To protect the necessary bandwidth on your network, you can deploy a Quality of Service (QoS) protocol such as Differentiated Services (DiffServ). Therefore, a best practice is to coordinate the CAC bandwidth policies you define with any QoS settings that you might deploy.

</div>

<div>

## Media and Signaling Paths over VPN

If your enterprise supports media through VPN, ensure that either both the media stream and the signaling stream go through the VPN or both are routed through the internet. By default, the media and signaling streams go through the VPN tunnel.

</div>

<div>

## Call Admission Control of Outside Users

Call admission control is not enforced for remote users where the network traffic flows through the Internet. Because the media traffic is traversing the Internet, which is not managed by Lync Server, CAC cannot be applied. CAC checks will be performed, however, on the portion of the call that flows through the enterprise network.

</div>

<div>

## Call Admission Control of PSTN Connections

Call admission control is enforceable on the Mediation Server regardless of whether it is connected to an IP/PBX, a PSTN gateway, or a SIP trunk. Because the Mediation Server is a back-to-back user agent (B2BUA), it terminates media. It has two connection sides: a side that is connected to Lync Server and a gateway side, which is connected to PSTN gateways, IP/PBXs, or SIP trunks. For details about PSTN connections, see [Planning for PSTN connectivity in Lync Server 2013](lync-server-2013-planning-for-pstn-connectivity.md).

CAC can be enforced on both sides of the Mediation Server unless media bypass is enabled. If media bypass is enabled, the media traffic doesn’t traverse the Mediation Server but instead flows directly between the Lync client and the gateway. In this case, CAC is not needed. For details, see [Planning for media bypass in Lync Server 2013](lync-server-2013-planning-for-media-bypass.md).

The following figure illustrates how CAC is enforced on PSTN connections with and without media bypass enabled.

**Call admission control enforcement on connections to the PSTN**

![Voice CAC Media Bypass Connection Enforcement](images/Gg398703.4d66d529-0912-4de1-abec-266f54272eb3(OCS.15).jpg "Voice CAC Media Bypass Connection Enforcement")

</div>

<div>

## Compatibility of Call Admission Control with Earlier Versions of Office Communications Server

Call admission control can be enabled only on endpoints that are enabled for Lync Server 2010 and later.

Call admission control cannot be enabled on endpoints running Office Communicator 2007 R2 or earlier.

**Application of CAC on different Lync Server versions**

![Voice CAC Version Comparison diagram](images/Gg398529.fdbfee7e-15fc-445b-949d-8d61e61ac350(OCS.15).jpg "Voice CAC Version Comparison diagram")

</div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

