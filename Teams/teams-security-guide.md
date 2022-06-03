---
title: Security guide for Microsoft Teams overview
author: MSFTTracyP
ms.author: tracyp
manager: dansimp
ms.date: 04/12/2022
ms.topic: reference
ms.service: msteams
audience: admin
ms.reviewer: pawa
description: Security advice and learnings for IT admins in installing, configuring, and maintaining Microsoft Teams.
ms.localizationpriority: high
search.appverid: MET150
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
  - remotework
ms.custom: 
- Security
appliesto: 
  - Microsoft Teams
---

# Security and Microsoft Teams

> [!IMPORTANT]
> The Teams service model is subject to change in order to improve customer experiences. For example, the default access or refresh token expiration times may be subject to modification in order to improve performance and authentication resiliency for those using Teams. Any such changes would be made with the goal of keeping Teams secure and Trustworthy by Design.

Microsoft Teams, as part of the Microsoft 365 and Office 365 services, follows all the security best practices and procedures such as service-level security through defense-in-depth, customer controls within the service, security hardening, and operational best practices. For full details, see the [Microsoft Trust Center](https://microsoft.com/trustcenter).

## Trustworthy by design

Teams is designed and developed in compliance with the Microsoft Trustworthy Computing Security Development Lifecycle (SDL), which is described at [Microsoft Security Development Lifecycle (SDL)](https://www.microsoft.com/sdl/default.aspx). The first step in creating a more secure unified communications system was to design threat models and test each feature as it was designed. Multiple security-related improvements were built into the coding process and practices. Build-time tools detect buffer overruns and other potential security threats before the code is checked in to the final product. It's impossible to design against all unknown security threats. No system can guarantee complete security. However, because product development embraced secure design principles from the start, Teams incorporates industry standard security technologies as a fundamental part of its architecture.

## Trustworthy by default

Network communications in Teams are encrypted by default. By requiring all servers to use certificates and by using OAUTH, Transport Layer Security (TLS), and Secure Real-Time Transport Protocol (SRTP), all Teams data is protected on the network.

## How Teams handles common security threats

This section identifies the more common threats to the security of the Teams Service and how Microsoft mitigates each threat.

### Compromised-key attack

Teams uses the PKI features in the Windows Server operating system to protect the key data used for encryption for the TLS connections. The keys used for media encryptions are exchanged over TLS connections.

### Network denial-of-service attack

A distributed denial-of-service (DDOS) attack occurs when the attacker prevents normal network use and function by valid users. By using a denial-of-service attack, the attacker can:

- Send invalid data to applications and services running in the attacked network to disrupt their normal function.
- Send a large amount of traffic, overloading the system until it stops responding or responds slowly to legitimate requests.
- Hide the evidence of the attacks.
- Prevent users from accessing network resources.

Teams mitigates against these attacks by running Azure DDOS network protection and by throttling client requests from the same endpoints, subnets, and federated entities.

### Eavesdropping

Eavesdropping occurs when an attacker gains access to the data path in a network and has the ability to monitor and read the traffic. Eavesdropping is also called sniffing or snooping. If the traffic is in plain text, the attacker can read the traffic when the attacker gains access to the path. An example is an attack performed by controlling a router on the data path.

Teams uses mutual TLS (MTLS) and Server to Server (S2S) OAuth (among other protocols) for server communications within Microsoft 365 and Office 365, and also uses TLS from clients to the service. All traffic on the network is encrypted.

These methods of communication make eavesdropping difficult or impossible to achieve within the time period of a single conversation. TLS authenticates all parties and encrypts all traffic. While TLS doesn't prevent eavesdropping, the attacker can't read the traffic unless the encryption is broken.

The *Traversal Using Relays around NAT* (TURN) protocol is used for real-time media purposes. The TURN protocol doesn't mandate the traffic to be encrypted and the information that it's sending is protected by message integrity. Although it's open to eavesdropping, the information it's sending, that is, IP addresses and port, can be extracted directly by looking at the source and destination addresses of the packets. The Teams service ensures that the data is valid by checking the Message Integrity of the message using the key derived from a few items including a TURN password, which is never sent in clear text. SRTP is used for media traffic and is also encrypted.

### Identity spoofing (IP address spoofing)

Spoofing occurs when the attacker identifies and then uses an IP address of a network, computer, or network component without being authorized to do so. A successful attack allows the attacker to operate as if the attacker is the entity normally identified by the IP address.

TLS authenticates all parties and encrypts all traffic. Using TLS prevents an attacker from performing IP address spoofing on a specific connection (for example, mutual TLS connections). An attacker could still spoof the address of the Domain Name System (DNS) server. However, because authentication in Teams is performed with certificates an attacker would not have a valid information required to spoof one of the parties in the communication.

### Man-in-the-middle attack

A man-in-the-middle attack occurs when an attacker reroutes communication between two users through the attacker's computer without the knowledge of the two communicating users. The attacker can monitor and read the traffic before sending it on to the intended recipient. Each user in the communication unknowingly sends traffic to and receives traffic from the attacker, all while thinking they are communicating only with the intended user. This scenario can happen if an attacker can modify Active Directory Domain Services to add their server as a trusted server, or modify DNS configuration or use other means to  to get clients to connect through the attacker on their way to the server.

Man-in-the-middle attacks on media traffic between two endpoints participating in Teams audio, video, and application sharing, is prevented by using *Secure Real-Time Transport Protocol* (SRTP) to encrypt the media stream. Cryptographic keys are negotiated between the two endpoints over a proprietary signaling protocol (Teams Call Signaling protocol) which uses TLS 1.2 and AES-256 (in GCM mode) encrypted UDP or TCP channel.

### Real-time Transport Protocol (RTP) replay attack

A replay attack occurs when a valid media transmission between two parties is intercepted and retransmitted for malicious purposes. Teams uses SRTP with a secure signaling protocol that protects transmissions from replay attacks by enabling the receiver to maintain an index of already received RTP packets and compare each new packet with packets already listed in the index.

### Spim

Spim is unsolicited commercial instant messages or presence subscription requests, like spam, but in instant message form. While not by itself a compromise of the network, it's annoying in the least, can reduce resource availability and production, and can possibly lead to a compromise of the network. An example is users spimming each other by sending requests. Users can block each other to prevent spimming, but with federation, if a malicious actor establishes a coordinated spim attack, it can be difficult to overcome unless you disable federation from the partner.

### Viruses and worms

A virus is a unit of code whose purpose is to reproduce more, similar code units. To work, a virus needs a host, such as a file, email, or program. Like a virus, a worm is a unit of code that reproduces more, similar code units, but that unlike a virus doesn't need a host. Viruses and worms primarily show up during file transfers between clients or when URLs are sent from other users. If a virus is on your computer, it can, for example, use your identity and send instant messages on your behalf. Standard client security best practices such as periodically scanning for viruses can mitigate this issue.

## Security Framework for Teams

Teams endorses security ideas like Zero Trust, and principles of Least Privilege access. This section gives an overview of fundamental elements that form a security framework for Microsoft Teams.

Core elements are:

- Azure Active Directory (Azure AD), which provides a single trusted back-end repository for user accounts. User profile information is stored in Azure AD through the actions of Microsoft Graph.
  - There may be multiple tokens issued which you may see if tracing your network traffic. Including Skype tokens you might see in traces while looking at chat and audio traffic.
- Transport Layer Security (TLS) encrypts the channel in motion. Authentication takes place using either mutual TLS (MTLS), based on certificates, or using Service-to-Service authentication based on Azure AD.
- Point-to-point audio, video, and application sharing streams are encrypted and integrity checked using Secure Real-Time Transport Protocol (SRTP).
- You will see OAuth traffic in your trace, particularly around token exchanges and negotiating permissions while switching between tabs in Teams, for example to move from Posts to Files. For an example of the OAuth flow for tabs, [see this document](/microsoftteams/platform/tabs/how-to/authentication/auth-flow-tab).
- Teams uses industry-standard protocols for user authentication, wherever possible.

The next sections discuss some of these core technologies.

### Azure Active Directory

Azure Active Directory functions as the directory service for Microsoft 365 and Office 365. It stores all user and application directory information and policy assignments.

### Traffic Encryption in Teams

This table shows the main Traffic types and what protocol is used for encryption.

|**Traffic type**|**Encrypted by**|
|:-----|:-----|
|Server-to-server|TLS (with MTLS or Service-to-Service OAuth)|
|Client-to-server, for example, instant messaging and presence|TLS|
|Media flows, for example, audio and video sharing of media|TLS|
|Audio and video sharing of media|SRTP/TLS|
|Signaling|TLS|
|Client-to-client enhanced encryption (for example, end-to-end encryption calls)|SRTP/DTLS|
|||

#### Certificate Revocation List (CRL) Distribution Points

Microsoft 365 and Office 365 traffic takes place over TLS/HTTPS encrypted channels, meaning that certificates are used for encryption of all traffic. Teams requires all server certificates to contain one or more CRL distribution points. CRL distribution points (CDPs) are locations from which CRLs can be downloaded for purposes of verifying that the certificate hasn't been revoked since the time it was issued and the certificate is still within the validity period. A CRL distribution point is noted in the properties of the certificate as a URL and is secure HTTP. The Teams service checks CRL with every certificate authentication.

#### Enhanced Key Usage

All components of the Teams service require all server certificates to support Enhanced Key Usage (EKU) for server authentication. Configuring the EKU field for server authentication means that the certificate is valid for authenticating servers. This EKU is essential for MTLS.

#### TLS for Teams

**Teams data is encrypted in transit and at rest in Microsoft services, between services, and between clients and services.** Microsoft does this using industry standard technologies such as TLS and SRTP to encrypt all data in transit. Data in transit includes messages, files, meetings, and other content. Enterprise data is also encrypted at rest in Microsoft services so that organizations can decrypt the content if needed, to meet security and compliance obligations through methods such as eDiscovery. For more information about encryption in Microsoft 365, see [Encryption in Microsoft 365](/microsoft-365/compliance/encryption)

TCP data flows are encrypted using TLS, and MTLS and Service-to-service OAuth protocols provide endpoint authenticated communications between services, systems, and clients. Teams uses these protocols to create a network of trusted systems and to ensure that all communication over that network is encrypted.

On a TLS connection, the client requests a valid certificate from the server. To be valid, the certificate must have been issued by a Certificate Authority (CA) that is also trusted by the client and the DNS name of the server must match the DNS name on the certificate. If the certificate is valid, the client uses the public key in the certificate to encrypt the symmetric encryption keys to be used for the communication, so only the original owner of the certificate can use its private key to decrypt the contents of the communication. The resulting connection is trusted and from that point is not challenged by other trusted servers or clients.

Using TLS helps prevent both eavesdropping and man-in-the middle attacks. In a man-in-the-middle attack, the attacker reroutes communications between two network entities through the attacker's computer without the knowledge of either party. TLS and Teams' specification of trusted servers mitigate the risk of a man-in-the middle attack partially on the application layer by using encryption that is coordinated using the Public Key cryptography between the two endpoints. An attacker would have to have a valid and trusted certificate with the corresponding private key and issued to the name of the service to which the client is communicating to decrypt the communication.

#### Encryption in Teams and Microsoft 365

There are multiple layers of encryption at work within Microsoft 365. Encryption in Teams works with the rest of Microsoft 365 encryption to protect your organization's content. This article describes encryption technologies that are specific to Teams. For an overview of encryption in Microsoft 365, see [Encryption in Microsoft 365](/microsoft-365/compliance/encryption).

#### Media encryption

Call flows in Teams are based on the [Session Description Protocol (SDP) RFC 8866](https://datatracker.ietf.org/doc/html/rfc8866) offer and answer model over HTTPS. Once the callee accepts an incoming call, the caller and callee agree on the session parameters.

Media traffic is encrypted by, and flows between, the caller and callee using Secure RTP (SRTP), a profile of Real-time Transport Protocol (RTP) that provides confidentiality, authentication, and replay attack protection to RTP traffic. SRTP uses a session key generated by a secure random number generator and exchanged using the signaling TLS channel. In most cases, client to client media traffic is negotiated through client to server connection signaling, and is encrypted using SRTP when going directly from client to client.

In normal call flows, negotiation of the encryption key occurs over the call signaling channel. In an end-to-end encrypted call, the signaling flow is the same as a regular one-to-one Teams call. However, Teams uses DTLS to derive an encryption key based on per-call certificates generated on both client endpoints. Since DTLS derives the key based on the client certificates, the key is opaque to Microsoft. Once both clients agree upon the key, the media begins to flow using this DTLS-negotiated encryption key over SRTP.

To protect against a man-in-the-middle attack between the caller and callee, Teams derives a 20-digit security code from the SHA-256 thumbprints of the caller’s and callee’s endpoint call certificates. The caller and callee can validate the 20-digit security codes by reading them to each other to see if they match. If the codes don’t match, then the connection between the caller and callee has been intercepted by a man-in-the-middle attack. If the call has been compromised, users can end the call manually.

Teams uses a credentials-based token for secure access to media relays over TURN. Media relays exchange the token over a TLS-secured channel.

### Federal Information Processing Standard (FIPS)

Teams uses FIPS compliant algorithms for encryption key exchanges. For more information on the implementation of FIPS, see [Federal Information Processing Standard (FIPS) Publication 140-2](/microsoft-365/compliance/offering-fips-140-2).

### User and Client Authentication

A trusted user is one whose credentials have been authenticated by Azure AD in Microsoft 365 or Office 365.

Authentication is the provision of user credentials to a trusted server or service. Teams uses the following authentication protocols, depending on the status and location of the user.

- **Modern Authentication (MA)** is the Microsoft implementation of OAUTH 2.0 for client to server communication. It enables security features such as multifactor authentication and Conditional Access. To use MA, both the online tenant and the clients need to be enabled for MA. The Teams clients across PC and mobile, and the web client, [all support MA](./sign-in-teams.md).

> [!NOTE]
> If you want more information on Azure AD authentication and authorization methods, this article's Introduction and 'Authentication basics in Azure AD' sections will help.

Teams authentication is accomplished through Azure AD and OAuth. The process of authentication can be simplified to:

- User sign in > token issuance > next request use issued token.

Requests from client to server are authenticated and authorized by Azure AD with the use of OAuth. Users with valid credentials issued by a federated partner are trusted and pass through the same process as native users. However, further restrictions can be put into place by administrators.

For media authentication, the ICE and TURN protocols also use the Digest challenge as described in the IETF TURN RFC.

### Windows PowerShell and Team Management Tools

In Teams, IT Admins can manage their service via the Microsoft 365 admin center or by using Tenant Remote PowerShell (TRPS). Tenant admins use Modern Authentication to authenticate to TRPS.

### Configuring access to Teams at your Internet boundary

For Teams to function properly, for example, for users to be able to join meetings, customers need to configure their internet access such that outbound UDP and TCP traffic to services in the Teams cloud is allowed. For more information, see [Office 365 URLs and IP address ranges](/office365/enterprise/urls-and-ip-address-ranges).

### UDP 3478-3481 and TCP 443

The UDP 3478-3481 and TCP 443 ports are used by clients to request service for audio visuals. A client uses these two ports to allocate UDP and TCP ports respectively to enable these media flows. The media flows on these ports are protected with a key that is exchanged over a TLS protected signaling channel.

### Federation safeguards for Teams

Federation provides your organization with the ability to communicate with other organizations to share IM and presence. In Teams federation is on by default. However, tenant admins have the ability to control federation through the Microsoft 365 admin center.

## Addressing threats to Teams Meetings

There are two options to control who arrives in Teams meetings and who will have access to the information you present.

1. You can control who joins your meetings through settings for the **lobby**.</p>

    |"Who can bypass the lobby" setting options available in Meeting options page   |User types joining the meeting directly  |User types going to the lobby   |
    |---------|---------|---------|
    |People in my organization     |  - In-tenant  </br>- Guest of tenant         |  - Federated</br>  - Anonymous</br>  - PSTN dial-in</br>     |
    |People in my organization and trusted organizations      |  - In-tenant</br> - Guest of tenant</br> - Federated</br>        |  - Anonymous</br>  - PSTN dial-in</br>      |
    |Everyone      |   - In-tenant</br>  - Guest of tenant</br>  - Federated Anonymous</br>  - PSTN dial-in</br>       |         |

2. The second way is through **structured meetings** (where Presenters can do about anything that should be done, and attendees have a controlled experience). After joining a structured meeting, presenters control what attendees can do in the meeting. </p>

    |Actions  |Presenters  |Attendees  |
    |---------|---------|---------|
    |Speak and share their video     |   Y      |   Y      |
    |Participate in meeting chat     |   Y    |    Y     |
    |Change settings in meeting options     |   Y      |  N       |
    |Mute other participants| Y | N |
    |Remove other participants      |  Y       |   N      |
    |Share content     |     Y    |     N    |
    |Admit other participants from the lobby|  Y       |   N      |
    |Make other participants presenters or attendees     |   Y      | N        |
    |Start or stop recording     |     Y    |    N     |
    |Take control when another participant shares a PowerPoint     |  Y         | N        |

Teams provides the capability for enterprise users to create and join real-time meetings. Enterprise users can also invite external users who don't have an Azure AD, Microsoft 365, or Office 365 account to participate in these meetings. Users who are employed by external partners with a secure and authenticated identity can also join meetings and, if promoted to do so, can act as presenters. Anonymous users can't create or join a meeting as a presenter, but they can be promoted to presenter after they join.

For Anonymous users to be able to join Teams meetings, the Participants meetings setting in the Teams Admin Center must be toggled on.

> [!NOTE]
> The term *anonymous users* means users that are not authenticated to the organizations tenant. In this context all external users are considered anonymous. Authenticated users include tenant users and Guest users of the tenant.

Enabling external users to participate in Teams meetings can be useful, but entails some security risks. To address these risks, Teams uses the following safeguards:

- Participant roles determine meeting control privileges.
- Participant types allow you to limit access to specific meetings.
- Scheduling meetings is restricted to users who have an AAD account and a Teams license.
- Anonymous, that is, unauthenticated, users who want to join a dial-in conference, dial one of the conference access numbers. If the "Always allow callers to bypass the lobby" setting is turned *On* then they also need to wait until a presenter or authenticated user joins the meeting.

  > [!CAUTION]
  > If you do not wish for Anonymous users (users you don't explicitly invite) to join a meeting, you need to ensure the **Anonymous users can join a meeting** is set to **Off** for the **Participant** meeting section.

It's also possible for an organizer to configure settings to let Dial-in callers be the first person in a meeting. This setting is configured in the Audio Conferencing settings for users and would apply to all meetings scheduled by the user.

> [!NOTE]
> For more information on Guest and External Access in Teams, see this [article](./communicate-with-users-from-other-organizations.md). It covers what features guest or external users can expect to see and use when they login to Teams. <p> If you're recording meetings and want to see a permissions matrix around accessing the content, consult [this article](./tmr-meeting-recording-change.md) and its matrix.

### Participant roles

Meeting participants fall into three groups, each with its own privileges and restrictions:

- **Organizer** The user who creates a meeting, whether impromptu or by scheduling. An organizer must be an authenticated in-tenant user and has control over all end-user aspects of a meeting.
- **Presenter** A user who is authorized to present information at a meeting, using whatever media is supported. A meeting organizer is by definition also a presenter and determines who else can be a presenter. An organizer can make this determination when a meeting is scheduled or while the meeting is under way.
- **Attendee** A user who has been invited to attend a meeting but who is not authorized to act as a presenter.

A presenter can also promote an attendee to the role of presenter during the meeting.

### Participant types

Meeting participants are also categorized by location and credentials. You can use both of these characteristics to decide which users can have access to specific meetings. Users can be divided broadly into the following categories:

- **Users that belong to the tenant**. These users have a credential in Azure Active Directory for the tenant.

    *People in my organization* – These users have a credential in Azure Active Directory for the tenant. *People in my organization* includes invited Guest accounts.

    *Remote users* – These users are joining from outside the corporate network. They can include employees who are working at home or on the road, and others, such as employees of trusted vendors, who have been granted enterprise credentials for their terms of service. Remote users can create and join meetings and act as presenters.

- **Users that do not belong to the tenant**. These users do not have credentials in Azure AD for the tenant.

    *Federated Users* - Federated users have valid credentials with federated partners and are therefore treated as authenticated by Teams, but are still external to the meeting organizer tenant. Federated users can join meetings and be promoted to presenters after they have joined the meeting, but they can't create meetings in enterprises with which they are federated.

    *Anonymous Users* - Anonymous users do not have an Active Directory identity and are not federated with the tenant.

Many meetings involve external users. Those same customers also want reassurance about the identity of external users before allowing those users to join a meeting. The next section describes how Teams limits meeting access to those user types that have been explicitly allowed, and requires all user types to present appropriate *credentials* when entering a meeting.

### Participant admittance

> [!CAUTION]
> If you do not want Anonymous users (users you don't explicitly invite) to join a meeting, you need to ensure the **Anonymous users can join a meeting** is set to **Off** for the **Participant** meeting section.

In Teams, anonymous users can be transferred to a waiting area called the lobby. Presenters can then either *admit* these users into the meeting or *reject* them. When these users are transferred to the lobby, the presenter and attendees are notified, and the anonymous users must then wait until they are either accepted or rejected, or their connection times out.

By default, participants dialing in from the PSTN go directly to the meeting once an authenticated user joins the meeting, but this option can be changed to force dial-in participants to go to the lobby.

Meeting organizers control whether participants can join a meeting without waiting in the lobby. Each meeting can be set up to enable access using any one of the following methods:

The defaults are:

- *People in my Organization* - Everyone external to the organization will wait in the lobby until admitted.
- *People from my organization and trusted organizations* - Authenticated users and external users from Teams and Skype for Business domains that are in the external access allowlist can bypass the lobby. All other users will wait in the lobby until admitted.
- *Everyone* - All meeting participants bypass the lobby once an authenticated user has joined the meeting.

### Presenter capabilities

Meeting organizers control whether participants can present during a meeting. Each meeting can be set up to limit presenters to any one of the following options:

- *People in my organization* - All in tenant users, including guests, can present
- *People in my organization and trusted organizations* - All in tenant users, including guests, can present and external users from Teams and Skype for Business domains that are in the external access allowlist can present.  
- *Everyone* - All meeting participants are presenters.

### Modify while meeting is running

You can modify the meeting options while a meeting is on-going. The change, when saved, will be noticeable in the running meeting within seconds. It also affects any future occurrences of the meeting.

## Related topics

[Top 12 tasks for security teams to support working from home](/microsoft-365/security/top-security-tasks-for-remote-work)

[Microsoft Trust Center](https://microsoft.com/trustcenter)

[Manage meeting settings in Microsoft Teams](./meeting-settings-in-teams.md)

[Optimize Microsoft 365 or Office 365 connectivity for remote users using VPN split tunneling](/Office365/Enterprise/office-365-vpn-split-tunnel)

- [Implementing VPN split tunneling](/Office365/Enterprise/office-365-vpn-implement-split-tunnel)

[Meeting recordings in Teams, where recordings are stored, and who can access them](./tmr-meeting-recording-change.md)
