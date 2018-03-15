---
title: "SIP trunking in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 7c586401-d0e5-4017-b3e1-fe5e7f8fc6db
description: "Session Initiation Protocol (SIP) is used to initiate and manage Voice over IP (VoIP) communications sessions for basic telephone service and for additional real-time communication services, such as instant messaging, conferencing, presence detection, and multimedia. This section provides planning information for implementing SIP trunks, a type of SIP connection that extends beyond the boundary of your local network."
---

# SIP trunking in Lync Server 2013
[]
Session Initiation Protocol (SIP) is used to initiate and manage Voice over IP (VoIP) communications sessions for basic telephone service and for additional real-time communication services, such as instant messaging, conferencing, presence detection, and multimedia. This section provides planning information for implementing SIP trunks, a type of SIP connection that extends beyond the boundary of your local network.
  
## What is SIP Trunking?

A SIP trunk is an IP connection that establishes a SIP communications link between your organization and an Internet telephony service provider (ITSP) beyond your firewall. Typically, a SIP trunk is used to connect your organization's central site to an ITSP. In some cases, you may also opt to use SIP trunking to connect your branch site to an ITSP.
  
### SIP Trunks vs. Direct SIP Connections

The term trunk is derived from circuit-switched technology. It refers to a dedicated physical line that connects telephone switching equipment. Like their predecessor, time division multiplexing (TDM) trunks, SIP trunks are connections between two separate SIP networks—the Lync Server 2013 enterprise and the ITSP. Unlike circuit-switched trunks, SIP trunks are virtual connections that can be established over any of the supported SIP trunking connection types. For details about the supported connection types, see [How do I implement SIP trunking in Lync Server 2013?](how-do-i-implement-sip-trunking.md).
  
Direct SIP connections, on the other hand, are SIP connections that do not cross the local network boundary (that is, they connect to a public switched telephone network (PSTN) gateway or private branch exchange (PBX) within your internal network). For details about how you can use direct SIP connections with Lync Server 2013, see [Direct SIP connections in Lync Server 2013](direct-sip-connections.md). 
  
## In This Section

- [Overview of SIP trunking in Lync Server 2013](overview-of-sip-trunking.md)
    
- [How do I implement SIP trunking in Lync Server 2013?](how-do-i-implement-sip-trunking.md)
    
- [Components and topologies for SIP trunking in Lync Server 2013](components-and-topologies-for-sip-trunking.md)
    
- [Branch site SIP trunking in Lync Server 2013](branch-site-sip-trunking.md)
    
- [SIP trunk deployment checklist for Lync Server 2013](sip-trunk-deployment-checklist.md)
    

