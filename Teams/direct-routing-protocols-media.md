---
title: Direct Routing support for media bypass
author: CarolynRowe
ms.author: crowe
manager: pamgreen
ms.date: 01/22/2024
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
description: How Direct Routing supports media bypass with a Session Border Controller enabled for ICE Lite.
appliesto: 
  - Microsoft Teams
---

# Direct Routing - media protocols

This article describes how Direct Routing supports media bypass with a Session Border Controller (SBC) enabled for ICE Lite as described in [RFC 5245](https://tools.ietf.org/html/rfc5245). This article is intended for voice administrators who are responsible for configuring the connection between the on-premises SBC and the SIP proxy service.

This article provides an overview of the ICE Lite scenarios and requirements for interoperability. The article describes the message formats and the required state machine transitions for ensuring reliable call and media flow.

## Terminology

- First Hello – The first words spoken by the caller and callee. It's important that all efforts are made to ensure that the first packets from the endpoints are delivered reliably for most use cases.

- Forking – The offer from the caller might be delivered to multiple callee endpoints if the callee is available on multiple devices (for example, a Teams user might be signed into Teams for Windows and Teams for Android or iPhone).

- Provisional Answer (183) – The callee endpoints for faster call setup send an answer with the candidates and keys required to establish media flow. This answer is done in anticipation of the user potentially answering the call(200OK) from that specific callee instance. With forking, the caller should be ready to receive multiple provisional answers.

- Re-Invite – Offer with final candidates selected by the ICE controlling endpoint. This offer has the a=remote-candidate attribute to resolve any race conditions from handling multiple forks.

- Teams Endpoint – This endpoint could either be a server (Media Processor, Transport Relay) or the Teams client.

## Message format

The Teams infrastructure follows RFC 5245 for ICE-Lite. All the STUN messages are compliant with [RFC 5389](https://tools.ietf.org/html/rfc5389).

The SBCs, as required by RFC 5389, must ignore any STUN attributes that they don't recognize, and continue to process the messages with the known attributes. 

If any malformed packets are received, the packets must be discarded without impacting the media session establishment.

## ICE Lite requirements

This section briefly captures the requirements for ICE Lite.

### Candidate gathering

The SBC must offer only one candidate. Currently, only IPV4 candidates are supported.


#### Connectivity checks

The ICE Lite implementation must respond to any connectivity checks received. The ICE Lite endpoint must not send any connectivity check requests. (If connectivity checks are sent in violation, the full implementation responds, which can result in unexpected peer-derived candidates being discovered and potentially result in call failures.)

#### Nominations

The ICE full implementation endpoint is the Controlling endpoint, and follows  “Regular” nominations for selecting the final candidates to be used for media flow. The ICE Lite endpoint can use the nominations to conclude the path to be used for media and complete call establishment.

When forking with peer endpoints sends 183 provisional answers, the SBC must be ready to respond to checks from multiple endpoints and also nominations from multiple endpoints if the nominations happen before 200OK. Depending on the convergence of the ICE state machine on the final path and timing of the user answering, the nominations can happen before or after 200OK. The SBC must be able to handle both cases.

#### Converging for forking

If the offer from the SBC forks to multiple Teams endpoints, the Teams endpoints may respond with a provisional answer and start connectivity checks. The SBC must be prepared to receive connectivity checks and respond to connectivity checks from multiple peer endpoints. For example, the Teams user could be signed on to both a desktop and a cell phone. Both devices are notified of the inbound call and will attempt connectivity checks with the SBC.

Eventually only one of the endpoints answer the call (200OK). On receiving the 200OK, the SBC can set up the right context for processing the media packets.

## Scenarios

###  Inbound call from SBC

For this scenario, there are several possible peer endpoints that the SBC must handle:

- Server endpoints typically respond directly with 200OK. These ICE Full endpoints  are typically involved in Voicemail, Call queue, and Auto attendant scenarios.

- Client endpoints can send multiple provisional answers with different From/To tags (183) followed by a 200OK from the endpoint that answers the call. These ICE Full endpoints are typically representing end user clients.

- Other SBC endpoints. These ICE Lite endpoints are typically involved in the scenario of simultaneously ringing client endpoints and another phone number(s).

The SBC must respond to all valid connectivity check requests received from the ICE Full endpoints. Per RFC, the ICE Full endpoints become Controlling endpoints. The Teams (client/server) endpoints perform “Regular” nominations to complete connectivity checks. The final 200Ok can either be from an endpoint that sent early media or from a different endpoint. On receiving the 200Ok, the SBC must set up the right context for media flow. 

###  Early media

If there's early media flow, the SBC must latch to the first endpoint that starts streaming media; media flow can start before candidates are nominated. 
The SBC should have support for sending DTMF during this phase to enable IVR/voicemail scenarios. The SBC should use the highest priority path on which it received checks if nominations haven't completed.

### Outbound call to SBC

The Teams endpoints are the Caller for this scenario and are the Controlling Endpoint. On receiving either a provisional answer (183) or a final answer(200OK), the Teams endpoint starts connectivity checks and proceed to “Regular” nominations to complete the connectivity checks.

Note: If the SBC sends a provisional answer (183), the SBC must be ready to receive connectivity check requests and potentially complete the nominations  before it sends the 200OK. If checks and/or nominations are completed before the 200OK is received, checks and/or nominations won't be performed again after 200OK is received. The SBC must not change ICE candidates, password, and ufrag (username fragment) between 183 and 200.

To support early media, the SBC may start streaming the media to the peer ICE candidate, with the highest priority based on received connectivity checks, even before nominations are completed by Teams endpoint. The SBC should expect media from Teams on any candidate until nominations are completed. Once a candidate is nominated, the SBC must reset to the right context to send and receive media packets.

### Handling M lines in SDP 

In some calling scenarios, other media modalities may be offered in a call to the PSTN. For example, m=video if a Teams video call is forwarded to the PSTN. If the customer SBC is configured with media bypass, then these lines won't be removed by the service, and need to be handled by the SBC following RFC3264: For each non “m=audio” line in the offer, the SBC must include a corresponding “m=” line in the answer, and the port number in this line should be set to zero, effectively rejecting all non-audio streams. 

## SRTP support requirements

The SBC must support SRTP encryption cipher AES_CM_128_HMAC_SHA1_80 for offer and answer in the following format:

```console
"inline:" <key||salt> ["|" lifetime]
```

The following is an example of the crypto attribute in the SDP offer from the SBC:

```console
a=crypto:1 AES_CM_128_HMAC_SHA1_80 inline:V/Lr6Lsvhad/crSB9kCQ28jrYDxR2Yfk5bXryH5V|2^31
```

MKI and Length parameters aren't required.

For more information, see [RFC 4568, section 6.1](https://tools.ietf.org/html/rfc4568#section-6.1).

## SDES support requirements

The device must be able to offer SDES in the following format. Microsoft Media Processors always prefer SDES.

- With non-media bypass, even if a client only supports DTLS, the Media Processors convert to SDES.

- With media bypass, if a client is DTLS only (future Google Chrome state), Direct Routing inserts an MP in the path, converting the call from media bypass to non-media bypass. Between the SBC and media processor component of Direct Routing, SDES is always used.

Currently, there is no Teams client that offers only DTLS; however Google announced that at some point in time they will stop supporting SDES.

## Format for offer from SBC in bypass mode 

Offer must contain SDES and can contain DTLS optional in the following format:

```console
m=audio 54056 UDP/TLS/RTP/SAVP 0 8 76 77 18 9 101 13
a=rtcp:54056
a=crypto:1 AES_CM_128_HMAC_SHA1_80 inline:krXco0QRglwErMqtbMs2zSw29tBdmdgXpEYZhQmp|2^31
a=fingerprint:sha-256 AE:24:07:15:5C:B7:45:1A:E4:45:60:C1:1E:68:0E:CC:8D:A6:78:3B:76:65:BB:B0:77:88:07:F8:98:18:62:34
a=setup:actpass
a=rtcp-mux
```

### Format for answer containing SDES to SBC

```console
m=audio 54056 RTP/SAVP 111 103 104 9 0 8 description 106 13 110 112 113 126
a=rtcp:54056
a=crypto:2 AES_CM_128_HMAC_SHA1_80 inline:fBc61ikv1kMy0sF85DblNqTzVAbFa7hJQ9GKb6Yj|2^31|1:1
a=crypto:3 AES_CM_128_HMAC_SHA1_80 inline:O1qT9tWbs/NwJVwhfrgF5tCrbNOxnVDqkIqTx4rz|2^31
a=rtcp-mux

```

## Format for offer from Teams to SBC 

### Format for SDES only offer to SBC

```console
m=audio 52884 RTP/SAVP 111 103 104 9 0 8 106 13 110 112 113 126
a=crypto:0 AES_CM_128_HMAC_SHA1_32 inline:Hr4D2cgUu9+Uza5Igz/JkVx59DAxDbaxJg862ibQ|2^31
a=crypto:1 AES_CM_128_HMAC_SHA1_80 inline:JPEaIxHegfuv53ykBPZk8hV0GO8kTiiqRMfHimEE|2^31
a=rtcp:52884
a=rtcp-mux
```

