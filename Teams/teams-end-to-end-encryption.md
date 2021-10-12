---
title: End-to-end encryption for Microsoft Teams overview
author: kccross
ms.author: krowley
manager: laurawi
ms.date: 10/12/2021
ms.topic: conceptual
ms.service: msteams
audience: admin
ms.reviewer: ashgupt
description:  Learn how to enable enhanced encryption capabilities in Microsoft Teams, create end-to-end encryption policies, and then assign policies to your users.
ms.localizationpriority: high
search.appverid: MET150
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
ms.custom: 
- Security
appliesto: 
  - Microsoft Teams
---

# Security and Microsoft Teams

> [!IMPORTANT]
> The Teams service model is subject to change in order to improve customer experiences. For example, the default access or refresh token expiration times may be subject to modification in order to improve performance and authentication resiliency for those using Teams. Any such changes would be made with the goal of keeping Teams secure and Trustworthy by Design.

Microsoft Teams, as part of the Microsoft 365 and Office 365 services, follows all the security best practices and procedures such as service-level security through defense-in-depth, customer controls within the service, security hardening, and operational best practices. For full details, see the [Microsoft Trust Center](https://microsoft.com/trustcenter).



### Man-in-the-middle attack

A man-in-the-middle attack occurs when an attacker reroutes communication between two users through the attacker's computer without the knowledge of the two communicating users. The attacker can monitor and read the traffic before sending it on to the intended recipient. Each user in the communication unknowingly sends traffic to and receives traffic from the attacker, all while thinking they are communicating only with the intended user. This can happen if an attacker can modify Active Directory Domain Services to add his or her server as a trusted server or modify Domain Name System (DNS) configuration to get clients to connect through the attacker on their way to the server.

Man-in-the-middle attacks on media traffic between two endpoints participating in Teams audio, video, and application sharing, is prevented by using SRTP to encrypt the media stream. Cryptographic keys are negotiated between the two endpoints over a proprietary signaling protocol (Teams Call Signaling protocol) which uses TLS 1.2 and AES-256 (in GCM mode) encrypted UDP / TCP channel.

### TLS and MTLS for Teams

TLS and MTLS protocols provide encrypted communications and endpoint authentication on the Internet. Teams uses these two protocols to create the network of trusted servers and to ensure that all communications over that network are encrypted. All communications between servers occur over MTLS. Any remaining or legacy SIP communications from client to server occur over TLS.

TLS enables users, through their client software, to authenticate the Teams servers to which they connect. On a TLS connection, the client requests a valid certificate from the server. To be valid, the certificate must have been issued by a Certificate Authority (CA) that is also trusted by the client and the DNS name of the server must match the DNS name on the certificate. If the certificate is valid, the client uses the public key in the certificate to encrypt the symmetric encryption keys to be used for the communication, so only the original owner of the certificate can use its private key to decrypt the contents of the communication. The resulting connection is trusted and from that point is not challenged by other trusted servers or clients.

Server-to-server connections rely on mutual TLS (MTLS) for mutual authentication. On an MTLS connection, the server originating a message and the server receiving it exchange certificates from a mutually trusted CA. The certificates prove the identity of each server to the other. In the Teams service, this procedure is followed.

TLS and MTLS help prevent both eavesdropping and man-in-the middle attacks. In a man-in-the-middle attack, the attacker reroutes communications between two network entities through the attacker's computer without the knowledge of either party. TLS and Teams' specification of trusted servers mitigate the risk of a man-in-the middle attack partially on the application layer by using encryption that is coordinated using the Public Key cryptography between the two endpoints. An attacker would have to have a valid and trusted certificate with the corresponding private key and issued to the name of the service to which the client is communicating to decrypt the communication.

> [!NOTE]
> Teams data is encrypted in transit and at rest in Microsoft datacenters. Microsoft uses industry standard technologies such as TLS and SRTP to encrypt all data in transit between users' devices and Microsoft datacenters, and between Microsoft datacenters. This includes messages, files, meetings, and other content. Enterprise data is also encrypted at rest in Microsoft datacenters, in a way that allows organizations to decrypt content if needed, to meet their security and compliance obligations, such as eDiscovery.

### Encryption for Teams

Teams uses TLS and MTLS to encrypt instant messages. All server-to-server traffic requires MTLS, regardless of whether the traffic is confined to the internal network or crosses the internal network perimeter.

This table summarizes the protocols used by Teams.

***Traffic Encryption***


|**Traffic type**|**Encrypted by**|
|:-----|:-----|
|Server-to-server|MTLS|
|Client-to-server (ex. instant messaging and presence)|TLS|
|Media flows (ex. audio and video sharing of media)|TLS|
|Audio and video sharing of media|SRTP/TLS|
|Signaling|TLS|
|||

#### Media encryption

Media traffic is encrypted using Secure RTP (SRTP), a profile of Real-time Transport Protocol (RTP) that provides confidentiality, authentication, and replay attack protection to RTP traffic. SRTP uses a session key generated by using a secure random number generator and exchanged using the signaling TLS channel. Client to client media traffic is negotiated through client to server connection signaling, but is encrypted using SRTP when going directly client to client.

Teams uses a credentials-based token for secure access to media relays over TURN. Media relays exchange the token over a TLS-secured channel.

#### Federal Information Processing Standard (FIPS)

Teams uses FIPS compliant algorithms for encryption key exchanges. For more information on the implementation of FIPS, see [Federal Information Processing Standard (FIPS) Publication 140-2](/microsoft-365/compliance/offering-fips-140-2).

## Related topics

[Top 12 tasks for security teams to support working from home](/microsoft-365/security/top-security-tasks-for-remote-work)

[Manage meeting settings in Microsoft Teams](./meeting-settings-in-teams.md)
