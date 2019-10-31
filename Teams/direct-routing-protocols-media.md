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

# Overview

This article describes how Direct Routing supports media bypass with an SBC enabled for ICE Lite as described in RFC 5245.  This article is intended for voice administrators who are responsible for configuring the connection between the on-premises SBC and the SIP proxy service.

This section provides an overview of the ICE Lite scenarios and requirements for interoperability. This will cover the message formats and the required state machine transitions for ensuring reliable call establishment and media flow.

## Terminology



- First Hello – The first words spoken by the caller and callee. It is important to ensure that all efforts are made to ensure that the first packets from the endpoints are delivered reliably for most use cases.

- Forking – The offer from the caller might be delivered to the multiple potential callee endpoints if the callee is available on multiple devices (for example, a Teams user might have Teams for Windows, Teams for Android/iPhone, where user signed in)

- Provisional Answer (183) – The callee endpoints for faster call setup sends an answer with the candidates and keys required to establish media flow. This is done in anticipation of the user potentially answering the call(200OK) from that specific callee instance. With forking the caller should be ready to receive multiple provisional answers.

- Re-Invite – Offer with final candidates selected by the ICE controlling endpoint. This will have the a=remote-candidate attribute to resolve any race conditions from handling multiple forks.

- Teams Endpoint – This could either be a server (Media Processor, Transport Relay) or the Teams client.

## Message format

The Teams infrastructure follows RFC 5245 for ICE-Lite. This implies all the STUN messages will be compliant with RFC 5389.

The SBCs as required by the RFC 5389 MUST ignore any STUN attributes that they do not recognize and continue to the process the messages with the known attributes. 

If any malformed packets are received the packets MUST be discarded without impacting the media session establishment.

## ICE Lite requirements

This section briefly captures the requirements for ICE-Lite.

### Candidate gathering

The SBC MUST offer only one candidate that is publicly reachable. This candidate MUST be IPV4. 
Note: If there is a requirement for the SBC candidate to be IPV6 we can need discuss more on how to handle this complexity.

#### Connectivity Checks

The ICE Lite implementation MUST responds to any connectivity checks received. The ICE Lite endpoint MUST not send any connectivity check requests. (If connectivity checks are sent in violation the full implementation will respond, this can result in unexpected peer derived candidates being discovered and potentially result in call failures)

###3 Nominations

The ICE full implementation endpoint will always be the Controlling endpoint and will follow “Regular” nominations for the selecting the final candidates to be used for media flow. The ICE Lite endpoint can use the nominations to conclude on the path to be used for media and complete call establishment.

Note: In the case of forking with peer endpoints sending 183 provisional answers, the SBC MUST be ready to respond to checks from multiple endpoints and also nominations from multiple endpoints if the nominations happen before 200OK. Depending on the convergence of ICE state machine on the final path and timing of the user answering the nominations can happen before or after 200OK. The SBC MUST be able to handle both cases.

###3 Converging for forking

If the offer from the SBC forks to multiple Teams endpoints, the Teams endpoints MAY respond with a provisional answer and start connectivity checks. The SBC MUST be prepared to receive connectivity checks and respond to connectivity checks potentially from multiple peer endpoints. For example, the Teams user could be signed on to his desktop and cell phone. Both devices will be notified of the inbound call and will attempt connectivity checks with the SBC.

Eventually only one of the endpoints will answer the call (200OK). On receiving the 200OK the SBC can setup the right context for processing the media packets.

### Scenarios

####  Inbound Call From SBC

For this scenario there are several possible peer endpoints that SBC MUST handle:
• Server endpoints will typically respond directly with 200OK. These are full ICE endpoints that are typically involved in Voicemail, Call Queue, AA scenarios.
• Client endpoints can send multiple provisional answers with different From/To tags (183) followed by a 200OK from the endpoint that answers the call. These are full ICE endpoints typically representing end user clients.
• Other SBC endpoints. These are ICE Lite endpoints typically involved in the scenario of simultaneously ringing client endpoints and another phone number(s).

The SBC MUST respond to all valid connectivity check requests received from the full ICE endpoints. Per RFC the full ICE endpoints will become Controlling endpoints. The Teams (client/server) endpoints will perform “Regular” Nominations to complete connectivity checks. The final 200Ok can either be from an endpoint that sent early media or from a different endpoint. On receiving the 200Ok SBC MUST setup the right context for media flow. 

####  Early media


If there is early media flow SBC MUST latch to first endpoint that starts streaming media, media flow can start even before candidates are nominated. 
The SBC SHOULD have support for sending DTMF during this phase to enable IVR/voicemail scenarios. SBC should use the highest priority path on which it has received checks if nominations have not completed.

#### Outbound call to SBC

The Teams endpoints are the Caller for this scenario and will be the Controlling Endpoint. The Teams endpoint on receiving either a provisional answer (183) or final answer(200OK) will start connectivity checks and proceed to “Regular” Nominations to complete connectivity checks.

Note: If the SBC sends a provisional answer (183), the SBC MUST be ready to receive connectivity check requests and potentially complete nominations even before the 200OK is sent by the SBC. If checks and/or nominations are completed before the 200OK is received checks and/or nominations will not be performed again after 200OK is received. SBC MUST NOT change ICE candidates, password and ufrag between 183 and 200.

To support early media, SBC MAY start streaming the media to the peer ICE candidate with the highest priority based on received connectivity checks, even before nominations are completed by Teams endpoint. SBC should expect media from Teams on any candidate until nominations are completed. Once candidate is nominated, SBC MUST reset to the right context to send and receive media packets.

## SRTP requirements

The SBC MUST support SRTP encryption cipher AES_CM_128_HMAC_SHA1_80 for offer and answer in the following format:

```
"inline:" <key||salt> ["|" lifetime]
```

Example of crypto attribute in SDP offer from the SBC:

```
a=crypto:1 AES_CM_128_HMAC_SHA1_80 inline:V/Lr6Lsvhad/crSB9kCQ28jrYDxR2Yfk5bXryH5V|2^31
```

MKI and Length parameters are not required

Reference: RFC 4568, section 6.1 https://tools.ietf.org/html/rfc4568#section-6.1

## SDES support Requirements

The Device must be able to offer SDES in the format as described below. Microsoft Media Processors always prefer SDES. In case of non-Media Bypass even if a client only supports DTLS the Media Processors will convert to SDES.

In case of Media Bypass, if a client is DTLS only (future Google Chrome state) the Direct Routing will insert an MP in the path, converting the call from media bypass to on-bypass type. Between the SBC and media Processor component of Direct Routing SDES is always used.

At the moment of writing this specification there were no Teams client which only offer DTLS, however Google announced that at some point of time they will stop supporting SDES.

## 4.4  Format for Offer from SBC in BYPASS (Offer must contain SDES and can contain DTLS Optional in the following format)

```
m=audio 54056 UDP/TLS/RTP/SAVP 0 8 76 77 18 9 101 13
a=rtcp:54056
a=crypto:1 AES_CM_128_HMAC_SHA1_80 inline:krXco0QRglwErMqtbMs2zSw29tBdmdgXpEYZhQmp|2^31
a=fingerprint:sha-256 AE:24:07:15:5C:B7:45:1A:E4:45:60:C1:1E:68:0E:CC:8D:A6:78:3B:76:65:BB:B0:77:88:07:F8:98:18:62:34
a=setup:actpass
a=rtcp-mux
```

###   Format for Answer containing SDES  to SBC

```
m=audio 54056 RTP/SAVP 111 103 104 9 0 8 description 106 13 110 112 113 126
a=rtcp:54056
a=crypto:2 AES_CM_128_HMAC_SHA1_80 inline:fBc61ikv1kMy0sF85DblNqTzVAbFa7hJQ9GKb6Yj|2^31|1:1
a=crypto:3 AES_CM_128_HMAC_SHA1_80 inline:O1qT9tWbs/NwJVwhfrgF5tCrbNOxnVDqkIqTx4rz|2^31
a=rtcp-mux

```

### Format for Offer from Teams to SBC 

### 4.4.3 Format for SDES only offer to SBC

```
m=audio 52884 RTP/SAVP 111 103 104 9 0 8 106 13 110 112 113 126
a=crypto:0 AES_CM_128_HMAC_SHA1_32 inline:Hr4D2cgUu9+Uza5Igz/JkVx59DAxDbaxJg862ibQ|2^31
a=crypto:1 AES_CM_128_HMAC_SHA1_80 inline:JPEaIxHegfuv53ykBPZk8hV0GO8kTiiqRMfHimEE|2^31
a=rtcp:52884
a=rtcp-mux
```

