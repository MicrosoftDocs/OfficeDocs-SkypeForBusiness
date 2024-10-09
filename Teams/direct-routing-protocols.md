---
title: "Teams Phone Direct Routing: Definitions and RFC standards"
author: CarolynRowe
ms.author: crowe
manager: pamgreen
ms.date: 12/16/2019
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - Tier1
ms.reviewer: nmurav
search.appverid: MET150
f1.keywords: 
  - NOCSH
description: How Teams Phone Direct Routing implements RFC standard protocols.
appliesto: 
  - Microsoft Teams
---

# Direct Routing - definitions and RFC standards

This article describes how Teams Phone Direct Routing implements RFC-standard protocols. This article is intended for voice administrators who are responsible for configuring the connection between the on-premises Session Border Controller (SBC) and the Session Initiation Protocol (SIP) proxy service.

The customer SBC interfaces with the following components in the Microsoft Teams backend: 

- **The SIP proxy** for signaling. This component is the Internet-facing component of Direct Routing that handles SIP (TLS) connections between the SBCs and Direct Routing.

- **The media processors** for media. This component is the Internet-facing component of Direct Routing that handles media traffic. This component uses SRTP and SRTCP protocols.


For more information about Direct Routing, see [Teams Phone Direct Routing](direct-routing-landing-page.md).

For more information about how Direct Routing implements the SIP protocol, see [Direct Routing - SIP protocol](direct-routing-protocols-sip.md).

## RFC standards

Direct Routing complies with RFC standards.  The SBC connected to Direct Routing must also comply with the following RFCs (or their successors). 

### Standards applicable to devices that support non-media bypass mode 

The following standards are applicable to devices that support only non-media bypass mode:

- [RFC 3261 SIP](https://tools.ietf.org/html/rfc3261): Session Initiation Protocol
- [RFC 3325](https://www.ietf.org/rfc/rfc3325). Private Extension to the Session Initiation Protocol for asserted identity within Trusted Networks--Sections about handling P-Asserted-Identity header. Direct Routing sends P-Asserted-Identity with Privacy ID headers. 
- [RFC 4244](https://www.ietf.org/rfc/rfc4244.txt) An extension to Session Initiation Protocol (SIP) for required History Information. See also: Routing SIP Protocol description for more information.
- [RFC 3892](https://www.ietf.org/rfc/rfc3892.txt) The Session Initiation Protocol Referred-By mechanism
- [RFC 3891](https://www.ietf.org/rfc/rfc3891.txt) The Session Initiation Protocol (SIP) "Replaces" Header 
- [RFC 6337](https://tools.ietf.org/html/rfc6337) Session Initiation Protocol (SIP) Usage of the Offer/Answer Model.
  See the “Deviations from RFC” section.
- [RFC 3711](https://tools.ietf.org/html/rfc3711) and [RFC 4771](https://tools.ietf.org/html/rfc4771). Protect RTP traffic using SRTP. The SBC must be able to establish keys using SDES. 
- [RFC 8035](https://www.ietf.org/rfc/rfc8035.txt) Session Description Protocol (SDP) Offer/Answer Clarifications for RTP/RTCP Multiplexing

### Standards applicable to devices that support media bypass mode

In addition to the standards listed as applicable to nonbypass mode, the following standards are used for media bypass mode:

- [RFC 5245 Interactive Connectivity Establishment (ICE) for media bypass](https://tools.ietf.org/html/rfc5245).  The SBC must support the following:
  - ICE Lite - the Teams clients are full ICE clients
  - [ICE Restarts](https://tools.ietf.org/html/rfc5245#section-9.1.1.1). See more on ICE restarts use case and examples in ICE Restart:  Media bypass call transferred to an endpoint that doesn't support media bypass   
- [RFC RFC 5589 Session Initiation Protocol (SIP) Call Control – Transfer](https://tools.ietf.org/html/rfc5589). 
- [RFC 3960 Early Media and Ringing Tone Generation in the Session Initiation Protocol (SIP)](https://tools.ietf.org/html/rfc3960), see sections 3.1, Forking, and 3.2, Ringing Tone Generation 
- [RFC 5389 Session Traversal Utilities for NAT (STUN)](https://tools.ietf.org/html/rfc5389)
- [RFC 5766 Traversal Using Relays around NAT (TURN): Relay Extensions to Session Traversal Utilities for NAT (STUN)](https://tools.ietf.org/html/rfc5766)

### Standards applicable to support conveying location information to E911 providers

- [RFC 6442, Location Conveyance for the Session Initiation Protocol](https://tools.ietf.org/html/rfc6442)

### Deviations from the RFCs

The following table lists the sections of the RFC(s) in which Microsoft's implementation of the SIP or media stack deviates from the standard:

| RFC and sections | Description | Deviation |
| :---------------------  |:---------------------- |:-----------------------|
| [RFC 6337, section 5.3 Hold and Resume of Media](https://tools.ietf.org/html/rfc6337#section-5.3) | RFC allows using “a=inactive”, “a=sendonly”, a=recvonly” to place a call on hold. |The SIP proxy only supports “a=inactive” and doesn't understand if the SBC sends “a=sendonly” or “a=recvonly”.
| [RFC 6337, section 5.4 Behavior on Receiving SDP with c=0.0.0.0](https://tools.ietf.org/html/rfc6337#section-5.4) | [RFC3264](https://tools.ietf.org/html/rfc3264) requires that an agent is capable of receiving SDP with a connection address of 0.0.0.0, in which case it means that neither RTP nor RTCP should be sent to the peer. | The SIP proxy doesn't support this option. |
| [RFC 3261, section 25 Augmented BNF for the SIP Protocol](https://tools.ietf.org/html/rfc3261#section-25.1) | '#' character should be sent as '%23'| The SIP proxy sends the '#' character in a Request-URI unescaped.
| [RFC 3264, section 8.3.1 An Offer/Answer Model with SDP](https://www.rfc-editor.org/rfc/rfc3264#section-8.3.1) |3264 details a MAY (Optional) media re-target mechanism allowing changing media port, IP address, or transport after session is established. | Optional media re-target is not supported. During a call, SIP requests to update media port, IP address, or transport are not supported. Media will not be sent to the updated session target; media from Direct Routing will continue to flow to the original target.

Note from RFC supporting the choice; The offerer MUST be prepared to receive media on both the old and new ports as soon as the offer is sent. The offerer SHOULD NOT cease listening for media on the old port until the answer is received and media arrives on the new port.|

## TCP/TLS transport considerations

When sending a SIP request (new or in-dialogue), Microsoft SIP Proxy may open a new TCP/TLS connection or reuse an existing connection if one exists.  

- There are a maximum of two TCP/TLS connections per remote FQDN/IP, per each SIP proxy virtual machine. Before sending a SIP request, SIP proxy checks for active TCP connections with the target SBC/Trunk FQDN’s resolved IP address. If two connections exist, they're reused. If two connections don't exist, a new connection is opened.  

  - This logic is per SIP proxy virtual machine.  

  - SIP proxy IPs are serviced by multiple virtual machines per region.  

  - From the SBC perspective, there may be multiple inbound proxy connections from all SIP proxy regions.  

- TCP/TLS connections opened by SIP proxy don't necessarily stay open as long as the call does. However, the connection doesn't close immediately after a response to a SIP request.  If a connection doesn't time out, it may be reused for other SIP requests.  

- SIP Proxy doesn't support connection aliasing as described in [RFC 5923: Connection Reuse in the Session Initiation Protocol (SIP)](https://www.rfc-editor.org/rfc/rfc5923.html).

  - Outbound SIP proxy TCP connections only service outbound SIP Proxy requests (to SBCs) and related responses.

  - Inbound SIP proxy TCP connections (from SBCs) only service incoming SIP requests and related responses.  


### Timeout policies 

- SIP proxy TCP idle timeout is two minutes. The timer resets when a SIP transaction occurs over the connection.  

- SIP proxy sends application CRLF keep-alive per [RFC 5626: Managing Client-Initiated Connections in the Session Initiation Protocol (SIP)](https://www.rfc-editor.org/rfc/rfc5626).

  - The keep-alive doesn't reset the TCP idle timer.

  - CRLF keep-alive sent by the supplier SBC resets the TCP idle timer.

- Due to the aliasing constraint mentioned previously, the supplier SBC must not use in-dialogue SIP requests for resetting the timer on connections created by SIP Proxy outbound to the supplier SBC. 

- After two minutes of idling, (FIN, ACK) is transmitted to the supplier SBC by SIP Proxy within approximately 10 to 20 seconds. 

### Notes

- It's recommended that the SBC actively reuses connections, like SIP proxy. This method saves time, which is needed for TCP and TLS connections. 

- The SBC should renew the connection at least once per hour. 

- When a new SBC’s certificate is uploaded, the SBC must renew all connections. 

- When domain configurations are updated, it's recommended that the SBC’s connections are renewed. Otherwise, a new configuration will be applied after the internal SIP proxy cache is renewed – up to four hours. 

 
## Operational modes

There are two operational modes for Direct Routing:

- **Without media bypass** in which all RTP traffic flows between the Teams client, the media processors, and the SBC.  

- **With media bypass** in which all RTP media flows between the Teams endpoints and the SBC. 

SIP traffic always flows through the SIP proxy. 

## DTMF

In-band DTMF isn't supported by media stack.
