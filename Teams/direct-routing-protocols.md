---
title:  Phone System Direct Routing
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.date: 01/28/2019
ms.topic: article
ms.service: msteams
audience: admin
ms.collection:  
- Teams_ITAdmin_Help
- M365-voice
ms.reviewer: nmurav
search.appverid: MET150
description: Direct Routing protocols
appliesto:
- Microsoft Teams
---

# Direct Routing - RFC protocols

This article describes how Microsoft Phone System Direct Routing implements RFC standard protocols. This article is intended for voice administrators who are responsible for configuring the connection between the on-premises Session Border Controller (SBC) and the Session Initiation Protocol (SIP) proxy service.

The customer SBC interfaces with the following components in the Microsoft Teams backend: 

- **The SIP proxy** for signaling. This is the Internet-facing component of Direct Routing that handles SIP (TLS) connections between the SBCs and Direct Routing.

- **The media processors** for media. This is the Internet-facing component of Direct Routing that handles media traffic. This component uses SRTP and SRTCP protocols.


For more information about Direct Routing, see [Phone System Direct Routing](direct-routing-landing-page.md).

For more information about how Direct Routing implements the SIP protocol, see [Direct Routing - SIP protocol](direct-routing-protocols-sip.md).

## RFC standards

Direct Routing complies with RFC standards.  The SBC connected to Direct Routing must also comply with the following RFCs (or their successors). 

### Standards applicable to devices that support non-media bypass mode 

The following standards are applicable to devices that support only non-media bypass mode:

- [RFC 3261 SIP](https://tools.ietf.org/html/rfc3261): Session Initiation Protocol
- [RFC 3325](https://www.ietf.org/rfc/rfc3325). Private Extension to the Session Initiation Protocol for asserted identity within Trusted Networks. 
  Sections about handling P-Asserted-Identity header. Direct Routing sends P-Asserted-Identity with Privacy ID headers. 
- [RFC 4244](https://www.ietf.org/rfc/rfc4244.txt) An extension to Session Initiation Protocol (SIP) for requires History Information. See also: Routing SIP Protocol description for more information
- [RFC 3892](https://www.ietf.org/rfc/rfc3892.txt) The Session Initiation Protocol Referred-By mechanism
- [RFC 3891](https://www.ietf.org/rfc/rfc3891.txt) The Session Initiation Protocol (SIP) "Replaces" Header 
- [RFC 6337](https://tools.ietf.org/html/rfc6337) Session Initiation Protocol (SIP) Usage of the Offer/Answer Model.
  See the “Deviations from RFC” section .
- [RFC 3711](https://tools.ietf.org/html/rfc3711) and [RFC 4771](https://tools.ietf.org/html/rfc4771). Protect RTP traffic using SRTP. The SBC must be able to establish keys using SDES. 
- [RFC 8035](https://www.ietf.org/rfc/rfc8035.txt) Session Description Protocol (SDP) Offer/Answer Clarifications for RTP/RTCP Multiplexing

### Standards applicable to devices that support media bypass mode

In addition to the standards listed as applicable to non-bypass mode, the following standards are used for media bypass mode:

- [RFC 5245 Interactive Connectivity Establishment (ICE) for media bypass](https://tools.ietf.org/html/rfc5245).  The SBC must support the following:
  - ICE Lite - the Teams clients are full ICE clients
  - [ICE Restarts](https://tools.ietf.org/html/rfc5245#section-9.1.1.1). See more on ICE restarts use case and examples in ICE Restart:  Media bypass call transferred to an endpoint which does not support media bypass   
- [RFC RFC 5589 Session Initiation Protocol (SIP) Call Control – Transfer](https://tools.ietf.org/html/rfc5589). 
- [RFC 3960 Early Media and Ringing Tone Generation in the Session Initiation Protocol (SIP)](https://tools.ietf.org/html/rfc3960), see sections 3.1, Forking, and 3.2, Ringing Tone Generation 
- [RFC 5389 Session Traversal Utilities for NAT (STUN)](https://tools.ietf.org/html/rfc5389)
- [RFC 5766 Traversal Using Relays around NAT (TURN): Relay Extensions to Session Traversal Utilities for NAT (STUN)](https://tools.ietf.org/html/rfc5766)

### Standards applicable to support conveying location information to E911 providers:

- [RFC 6442, Location Conveyance for the Session Initiation Protocol](https://tools.ietf.org/html/rfc6442)

### Deviations from the RFC's

The following table lists the sections of the RFC(s) in which Microsoft's implementation of the SIP or media stack deviates from the standard:

| RFC and sections | Description | Deviation |
| :---------------------  |:---------------------- |:-----------------------|
| [RFC 6337, section 5.3 Hold and Resume of Media](https://tools.ietf.org/html/rfc6337#section-5.3) | RFC allows using “a=inactive”, “a=sendonly”, a=recvonly” to place call on hold |The SIP proxy only supports “a=inactive” and does not understand if the SBC sends “a=sendonly” or “a=recvonly”
| [RFC 6337, section 5.4 “Behavior on Receiving SDP with c=0.0.0.0](https://tools.ietf.org/html/rfc6337#section-5.4) | [RFC3264](https://tools.ietf.org/html/rfc3264) requires that an agent is capable of receiving SDP with a connection address of 0.0.0.0, in which case it means that neither  RTP nor RTCP should be sent to the peer. | The SIP proxy does not support this option |

## Operational modes

There are two operational modes for Direct Routing:

- **Without media bypass** in which all RTP traffic flows between the Teams client, the media processors, and the SBC.  

- **With media bypass** in which all RTP media flows between the Teams endpoints and the SBC. 

Note that SIP traffic always flows via the SIP proxy.   
