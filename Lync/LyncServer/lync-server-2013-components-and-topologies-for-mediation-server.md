---
title: 'Lync Server 2013: Components and topologies for Mediation Server'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Components and topologies for Mediation Server
ms:assetid: 71397168-36c3-4d21-b8ef-db6a751634ee
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398537(v=OCS.15)
ms:contentKeyID: 48184487
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Components and topologies for Mediation Server in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-21_

This topic describes the components on which the Mediation Server is dependent and the topologies in which the Mediation Server can be deployed

<div>

## Dependencies

The Mediation Server has the following dependencies:

  - **Registrar.** Required. The Registrar is the next hop for signaling in the Mediation Server interactions with the Lync Server 2013 network. Note that Mediation Server can be collocated on a Front End Server along with the Registrar, in addition to being installed in a stand-alone pool consisting only of Mediation Servers. The Registrar is collocated with a Mediation Server and PSTN gateway on a Survivable Branch Appliance.

  - **Monitoring Server.** Optional but highly recommended. The Monitoring Server allows the Mediation Server to record quality metrics associated with its media sessions.

  - **Edge Server.** Required for external user support. The Edge Server allows the Mediation Server to interact with users who are located behind a NAT or firewall.

</div>

<div>

## Topologies

The Lync Server 2013, Mediation Server is by default collocated with an instance of the Registrar on a Standard Edition server, a Front End pool, or Survivable Branch Appliance. All Mediation Servers in a Front End pool must be configured identically.

Where performance is an issue, it may be preferable to deploy one or more Mediation Servers in a dedicated stand-alone pool. Or, if you are deploying SIP trunking, we recommend that you deploy a stand-alone Mediation Server pool.

If you deploy Direct SIP connections to a qualified PSTN gateway that supports media bypass and DNS load balancing, a stand-alone Mediation Server pool is not necessary. A stand-alone Mediation Server pool is not necessary because qualified gateways are capable of DNS load balancing to a pool of Mediation Servers and they can receive traffic from any Mediation Server in a pool.

We also recommend that you collocate the Mediation Server on a Front End pool when you have deployed IP-PBXs or connect to an Internet Telephony Server Provider’s Session Border Controller (SBC), as long as any of the following conditions are met:

  - The IP-PBX or SBC is configured to receive traffic from any Mediation Server in the pool and can route traffic uniformly to all Mediation Servers in the pool.

  - The IP-PBX does not support media bypass, but the Front End pool that is hosting the Mediation Server can handle voice transcoding for calls to which media bypass does not apply.

You can use the Microsoft Lync Server 2013, Planning Tool to evaluate whether the Front End pool where you want to collocate the Mediation Server can handle the load. If your environment cannot meet these requirements, then you must deploy a stand-alone Mediation Server pool.

For details about which topology to deploy, see [Deployment guidelines for Mediation Server in Lync Server 2013](lync-server-2013-deployment-guidelines-for-mediation-server.md).

The following figure shows a simple topology consisting of two sites connected by a WAN link. Mediation Server is collocated with the Registrar on a Front End pool at Site 1. The Mediation Servers at Site 1 controls both the PSTN gateway at Site 1 and the gateway at Site 2. In this topology, media bypass is enabled globally to use site and region information, and the trunks to each PSTN gateway (GW1 and GW2) have bypass enabled.

**Example of sites connected by a WAN link with a Mediation Server at Site 1 and a PSTN gateway at Site 2**

![Voice Topology with Mediation Server WAN Gateway](images/Gg398537.67872e61-1444-447b-918c-abe89abc3004(OCS.15).jpg "Voice Topology with Mediation Server WAN Gateway")

The next figure shows a simple topology where the Mediation Server is collocated with the Registrar on Front End pool at Site 1 and has a Direct SIP connection to the IP-PBX at Site 1. In this figure, the Mediation Server also controls a PSTN gateway at Site 2. Assume that Lync users exist at both Sites 1 and 2. Also assume that the IP-PBX has an associated media processor that must be traversed by all media originating from Lync endpoints before being sent to media endpoints controlled by the IP-PBX. In this topology, media bypass is enabled globally to use site and region information, and the trunks to the PBX and PSTN gateway have media bypass enabled.

**Example of sites connected by a WAN link with a Mediation Server at Site 1 and a PBX at Site 2**

![Voice Topology Mediation Server WAN PBX](images/Gg398537.df6c8a5b-8431-4187-907d-ff5ca26eeeec(OCS.15).jpg "Voice Topology Mediation Server WAN PBX")

For details about planning for PBX topologies, see [Deployment guidelines for Mediation Server in Lync Server 2013](lync-server-2013-deployment-guidelines-for-mediation-server.md) and [Direct SIP deployment options in Lync Server 2013](lync-server-2013-direct-sip-deployment-options.md).

The last figure in this topic shows a topology where the Mediation Server is connected to the SBC of an Internet Telephony Service Provider. For details about SIP trunk topologies, see [SIP trunking in Lync Server 2013](lync-server-2013-sip-trunking.md).

</div>

</div>

<span> </span>

</div>

</div>

</div>

