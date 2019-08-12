---
title: 'Lync Server 2013: Mediation Server component'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Mediation Server component
ms:assetid: 5b19edef-4a54-43c9-aa12-5643b8108355
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398399(v=OCS.15)
ms:contentKeyID: 48184239
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Mediation Server component in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-21_

You must deploy Lync Server 2013, Mediation Server if you deploy the Enterprise Voice workload. This section describes basic functionality, dependencies, basic topologies, and planning guidelines.

The Mediation Server translates signaling and, in some configurations, media between your internal Lync Server 2013, Enterprise Voice infrastructure and a public switched telephone network (PSTN) gateway or a Session Initiation Protocol (SIP) trunk. On the Lync Server 2013 side, Mediation Server listens on a single mutual TLS (MTLS) transport address. On the gateway side, Mediation Server listens on all associated listening ports associated with trunks defined in the Topology document. All qualified gateways must support TLS, but can enable TCP as well. TCP is supported for gateways that do not support TLS.

If you also have an existing Public Branch Exchange (PBX) in your environment, Mediation Server handles calls between Enterprise Voice users and the PBX. If your PBX is an IP-PBX, you can create a direct SIP connection between the PBX and Mediation Server. If your PBX is a Time Division Multiplex (TDM) PBX, you must also deploy a PSTN gateway between Mediation Server and the PBX.

The Mediation Server is collocated with the Front End Server by default. The Mediation Server can also be deployed in a stand-alone pool for performance reasons, or if you deploy SIP trunking, in which case the stand-alone pool is strongly recommended.

If you deploy Direct SIP connections to a qualified PSTN gateway that supports media bypass and DNS load balancing, a stand-alone Mediation Server pool is not necessary. A stand-alone Mediation Server pool is not necessary because qualified gateways are capable of DNS load balancing to a pool of Mediation Servers and they can receive traffic from any Mediation Server in a pool.

We also recommend that you collocate the Mediation Server on a Front End pool when you have deployed IP-PBXs or connect to an Internet Telephony Server Provider’s Session Border Controller (SBC), as long as any of the following conditions are met:

  - The IP-PBX or SBC is configured to receive traffic from any Mediation Server in the pool and can route traffic uniformly to all Mediation Servers in the pool.

  - The IP-PBX does not support media bypass, but the Front End pool that is hosting the Mediation Server can handle voice transcoding for calls to which media bypass does not apply.

You can use the Microsoft Lync Server 2013, Planning Tool to evaluate whether the Front End pool where you want to collocate the Mediation Server can handle the load. If your environment cannot meet these requirements, then you must deploy a stand-alone Mediation Server pool.

The main functions of the Mediation Server are as follows:

  - Encrypting and decrypting SRTP on the Lync Server side

  - Translating SIP over TCP (for gateways that do not support TLS) to SIP over mutual TLS

  - Translating media streams between Lync Server and the gateway peer of the Mediation Server

  - Connecting clients that are outside the network to internal ICE components, which enable media traversal of NAT and firewalls

  - Acting as an intermediary for call flows that a gateway does not support, such as calls from remote workers on an Enterprise Voice client

  - In deployments that include SIP trunking, working with the SIP trunking service provider to provide PSTN support, which eliminates the need for a PSTN gateway

The following figure shows the signaling and media protocols that are used by the Mediation Server when communicating with a basic PSTN gateway and the Enterprise Voice infrastructure.

**Signaling and media protocols used by the Mediation Server**

![Mediation Server Protocols diagram](images/Gg398399.c3d39ba0-e323-4a58-8f07-4e80d3278af2(OCS.15).jpg "Mediation Server Protocols diagram")

<div>


> [!NOTE]  
> If you are using TCP or RTP/RTCP (instead of SRTP or SRTCP) on the network between the PSTN gateway and the Mediation Server, we recommend that you take measures to help ensure the security and privacy of the network.



</div>

<div>

## In This Section

  - [M:N trunk in Lync Server 2013](lync-server-2013-m-n-trunk.md)

  - [Call admission control and Mediation Server in Lync Server 2013](lync-server-2013-call-admission-control-and-mediation-server.md)

  - [Enhanced 9-1-1 (E9-1-1) and Mediation Server in Lync Server 2013](lync-server-2013-enhanced-9-1-1-e9-1-1-and-mediation-server.md)

  - [Media bypass and Mediation Server in Lync Server 2013](lync-server-2013-media-bypass-and-mediation-server.md)

  - [Components and topologies for Mediation Server in Lync Server 2013](lync-server-2013-components-and-topologies-for-mediation-server.md)

  - [Deployment guidelines for Mediation Server in Lync Server 2013](lync-server-2013-deployment-guidelines-for-mediation-server.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

