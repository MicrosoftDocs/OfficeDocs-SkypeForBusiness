---
title: 'Lync Server 2013: SIP trunk deployment checklist'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: SIP trunk deployment checklist
ms:assetid: 94f4f03e-19d5-4198-92be-e4076dbb959a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398755(v=OCS.15)
ms:contentKeyID: 48184891
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# SIP trunk deployment checklist for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-21_

Before you can deploy a SIP trunk, you and your service provider must exchange some basic connection information about your respective SIP trunk endpoints.

Get the following information for each ITSP gateway that you will connect to:

  - IP address

  - Fully qualified domain name (FQDN)

<div>


> [!NOTE]  
> The service provider may ask you to connect to more than one ITSP gateway. In that case, you must configure a connection between each ITSP gateway and each Mediation Server in your pool.



</div>

The information you give to your service provider depends on your SIP trunk connection type:

  - For Multiprotocol Label Switching (MPLS) or private network connections, give the ITSP the publicly routable IP Address of the router in your perimeter network (also known as DMZ, demilitarized zone, and screened subnet). Verify that the gateway or Session Border Controller (SBC) at the ITSP can reach this address. Also give the ITSP the FQDN of your Mediation Server.

  - For virtual private network (VPN) connections, give the ITSP the IP address of your VPN server.

<div>

## Certificate Considerations

To determine whether you need a certificate for SIP trunking, check with your ITSP about protocol support:

1.  If your ITSP supports Transmission Control Protocol (TCP) only, you do not need a certificate.

2.  If your ITSP supports Transport Layer Security (TLS), the ITSP must provide you with a certificate.

<div>


> [!NOTE]  
> SIP works in conjunction with real-time transport protocol (RTP) or secure real-time transport protocol (SRTP), the protocols that manage the actual voice data in Voice over Internet Protocol (VoIP) calls.



</div>

</div>

<div>

## Deployment Process

To implement the Lync Server side of the SIP trunk connection, follow these steps:

1.  Using the Lync Server Topology Builder, create and configure the SIP domain topology. For details, see [Define and configure a topology in Topology Builder for Lync Server 2013](lync-server-2013-define-and-configure-a-topology-in-topology-builder.md) in the Deployment documentation.

2.  Using the Lync Server Control Panel, configure voice routing for the new SIP domain. For details, see [Configuring trunks in Lync Server 2013](lync-server-2013-configuring-trunks.md) in the Deployment documentation.

3.  Test connectivity by using the **Test-CsPstnOutboundCall** cmdlet. For details, see the Lync Server Management Shell documentation or Help for Lync Server Management Shell.

</div>

</div>

<span> </span>

</div>

</div>

</div>

