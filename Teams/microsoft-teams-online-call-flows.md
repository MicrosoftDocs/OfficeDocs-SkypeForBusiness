---
title: Microsoft Teams Online Call Flows
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 06/08/2018
ms.topic: conceptual
ms.service: msteams
ms.reviewer: sonua 
localization_priority: Normal
search.appverid: MET150
ms.collection:  
- Teams_ITAdmin_Help
- M365-collaboration
- M365-voice
appliesto: 
- Microsoft Teams
description: Describes how Teams uses Office 365 flows in various topologies.
---

# Microsoft Teams Online Call Flows

> [!Tip]
> Watch the following session to learn how Teams leverages your network and how to plan for optimal network connectivity: [Teams Network Planning](https://aka.ms/teams-networking)

## Overview
This document describes how Teams uses Office 365 call flows in various topologies. In addition, it describes unique Teams flows that are used for peer-to-peer media communication. The document describes these flows, their purpose, and their origin/termination networks. For example, assume the following:

- Flow X is used by the Office 365 client on premises to communicate with the Office 365 service in the cloud, originated from the customer network, and terminated by an endpoint in Office 365 cloud.

- Flow Y is used by the Office 365 client on premises to communicate with a service on the Internet that Office 365 has dependency on, originated from the customer network, and terminated by an endpoint on the Internet.

The document has three main sections:

- It provides background information, such as networks (that Office 365 flows may traverse), type of traffic, connectivity guidance from the customer network to Office 365 service endpoints, interoperability with third-party components and principals that are used by Teams to select media flows.
- 
- It illustrates the usage of these flows in various topologies. For each topology, it enumerates all supported flows and illustrates how these flows are used via several use cases. For each use case, it describes the sequence and selection of flows via a flow diagram. 

- It describes how these flows are used when Express Route is deployed for optimization, illustrated via a simple topology.

## Background
### Network Segments
**Customer Network**: This is the network segment that you control and manage. This includes all customer connections within customer offices, whether wired or wireless, between office buildings, to on-premises datacenters, and your connections to Internet providers, Express Route, or any other private peering. 

Typically, a customer network has several network perimeters with firewalls and/or proxy servers, which enforce your organization's security policies, and that only allow certain network traffic that you have set up and configured. Because you manage this network, you have direct control over the performance of the network, and it is highly recommended that you complete network assessments to validate performance both within sites in your network and from your network to the Office 365 network. Skype for Business on-premises deployment and Microsoft Direct Routing to connect with PSTN through your network are optional.

**Internet**: This is the network segment that is part of your overall network that will be used by users who are connecting to Office 365 from outside of the Customer Network. It is also used by some traffic from the Customer Network to Office 365. 

**Visited/Guest private Network**: This is the network segment outside your Customer Network, but not in the public Internet, that your users and/or their guests may visit. For example, home private network or an Enterprise private Network, that does not deploy Teams, where your users and/or their customers that interact with Teams services, may reside.

>**Note**: Connectivity to Office 365 is also applicable to these networks.

**Office 365**: This is the network segment that supports Office 365 services. It is distributed worldwide with edges in proximity to Customer Network in most locations. Functions mentioned in this document include Transport Relay, conferencing server, and Media Processor. 

**Express Route (Optional)**: This is the network segment that is part of your overall network that will give you a dedicated, private connection to the Office 365 network.

### Types of traffic

**Real-time media**: Data encapsulated within RTP (Real-time Transport Protocol) and supports audio, video and screen sharing workloads. In general, media traffic is highly latency sensitive, so you would want this traffic to take the most direct path possible, and to use UDP versus TCP as the transport layer protocol, which is the best transport for interactive real time media from a quality perspective. (Note: As a last resort, media can use TCP/IP and also be tunneled within the HTTP protocol, but it is not recommended due to bad quality implications.) RTP flow is secured via SRTP, in which only the payload is encrypted.

**Signaling**: The communication link between the client and server, or other clients that are used to control activities (for example, when a call is initiated), and deliver instant messages. Most signaling traffic uses the HTTPS-based REST interfaces, though in some scenarios (for example, connection between Office 365 Cloud and a Session Border Controller) uses SIP Protocol. It's important to understand that this traffic is much less sensitive to latency but may cause service outages or call timeouts if latency between the endpoints exceed several seconds. 

### Connectivity to Office 365

Teams service requires [connectivity to the Internet](https://support.office.com/article/connectivity-to-the-internet-64b420ef-0218-48f6-8a34-74bb27633b10). Teams endpoints URLs and IP address ranges are listed in [Office 365 URLs and IP address ranges](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges). (Note: It requires to open connectivity to TCP ports 80 and 443 and UDP ports 3478 through 3481.) Furthermore, Teams service has dependency on Skype for business online service, hence it is required to connect also this service to the Internet.

Teams media flows connectivity is implemented via standard IETF ICE (Interactive Connectivity Establishment) procedures.

### Interoperability Restrictions
**Third party media relays**: A Teams media flow (i.e., one of the media endpoints is Teams) may traverse only Teams or Skype for Business native media relays. Interoperability with a third party media relay is not supported. (Note: A third party SBC on the boundary with PSTN MUST terminate RTP/RTCP stream, secured via SRTP, and not relay it to the next hop.)

**Third party SIP Proxy Servers**: A Teams signaling SIP dialog with a third party SBC and/or Gateway may traverse Teams or Skype for Business native SIP proxies. Interoperability with a third party SIP Proxy is not supported.

**Third party B2BUA (i.e., SBC)**: A Teams media flow from/to PSTN is terminated by a third party SBC. However, interoperability with a third party SBC within Teams network (i.e., third party SBC mediates two Teams/Skype For Business endpoints) is not supported.

### Technologies that are strongly not recommended with Microsoft Teams

**VPN Network**: It is strongly not recommended for media traffic (i.e., flow 2'). VPN client SHOULD use split VPN and route media traffic like any external non-VPN user, as specified in https://blogs.technet.microsoft.com/nexthop/2011/11/14/enabling-lync-media-to-bypass-a-vpn-tunnel/ 

>**Note**: Although the title is Lync, it is applicable to Teams as well.

**Packet Shapers**: Any kind of packet snippers, packet inspection, or packet shaper devices are strongly not recommended and may degrade quality significantly. 

### Principles
There are four general principles that help you understand call flows for Microsoft Teams:
 
1.	A Microsoft Teams conference is hosted by Office 365 cloud in the same region where the first participant joined. (Note: If there will be exceptions to this rule in some topologies, then they will be described in this document, illustrated by an appropriate call flow.)

2.	A Teams media endpoint (MP) in Office 365 cloud is used based on media processing needs and not based on call type. (For example, a point to point call may use a media endpoint in the cloud to process media for transcription and/or recording, while a conference with two participants may not use any media endpoint in the cloud.) However, most conferences will use an MP for mixing and routing purposes, allocated where the conference is hosted. The media traffic sent from a client to the MP may be routed directly or use a Transport Relay, in Office 365 Cloud, if required due to Customer Network firewall restrictions. 

3.	Media traffic for peer-to-peer calls take the most direct route that is available, assuming that the call doesn't mandate an MP in the cloud (see #2 above). The preferred route is direct to the remote peer (client), but if that route isn't available, then one or more Transport Relays will relay traffic. It is recommended that media traffic shall not transverse servers such as packet shapers, VPN servers, etc., since this will impact the media quality.

4.	Signaling traffic always goes to the closest server to the user. 

To learn more about the details on the media path that is chosen, see https://www.youtube.com/watch?v=1tmHMIlAQdo.

## Call Flows in Various Topologies
### Teams Online ("pure") Topology
This topology is used by customers that leverage Teams services from the cloud without deploying any on-premises server, such as Skype for Business Server, or Microsoft Direct Routing. In addition, the interface to Office 365 is done via the Internet without Azure Express Route. 

[![Microsoft Teams Online Call Flows Figure 01](media/microsoft-teams-online-call-flows-figure01.png)](media/microsoft-teams-online-call-flows-figure01.png)

*Figure 1 - Teams Online ('pure') Topology*

>**Notes**:
>- The direction of the arrows on the diagram above reflect the initiation direction of the communication that affects connectivity at the enterprise perimeters. In the case of UDP for media, the first packet(s) may flow in the reverse direction, but these packets may be blocked until packets in the other direction will flow.
>- Teams is deployed side by side with Skype for Business Online, hence clients are displayed as "Teams/SFB user".

- Optional Skype for Business on premises deployment is described in this document in the section **Teams Online Hybrid Topology**
- Optional Direct Routing for PSTN is described in this document in the section **Teams Online with Direct Routing Topology**
- Optional Express Route is described in this document in the section **Teams w/ Express Route optimization**

**Flows Descriptions**:
- **Flow 2** – Represents a flow initiated by a user on Customer Network to the Internet as a part of his Teams experience. Examples of these flows are DNS and peer-to-peer media.
- **Flow 2'** – Represents a flow initiated by a remote mobile Teams user, which VPN to Customer Network. 
- **Flow 3** – Represents a flow initiated by a remote mobile Teams user to Office 365/Teams endpoints. 
- **Flow 4** – Represents a flow initiated by a user on the Customer Network to Office 365/Teams endpoints.
- **Flow 5** – Represents a peer-to-peer media flow between a Teams user and another Teams or Skype for Business user within the Customer Network.
- **Flow 6** – Represents a peer-to-peer media flow between a remote mobile Teams user and another remote mobile Teams or Skype for Business user, over the Internet.

#### Use Case: One-to-one
One-to-one calls use a common model in which the caller will obtain a set of candidates consisting of IP addresses/ports--including local, relay, and reflexive (public IP address of client as seen by the relay) candidates. The caller sends these candidates to the called party; the called party also obtains a similar set of candidates and sends them to the caller. STUN connectivity check messages are used to find which caller/called party media paths work, and the best working path is selected. Media (i.e., RTP/RTCP packets secured via SRTP) are then sent using the selected candidate pair. The Transport relay is deployed as part of Office 365.

If the local IP address/port candidates or the reflexive candidates have connectivity, then the direct path between the clients (or via a NAT) will be selected for media. If the clients are both on the Customer Network, then the direct path should be selected. This requires direct UDP connectivity within the Customer Network. If the clients are both nomadic cloud users, then depending on the NAT/firewall, media may use direct connectivity.

If one client is internal on the Customer Network and one client is external (e.g., mobile cloud user), then it is unlikely that direct connectivity between the local or reflexive candidates is working. In this case, an option is to use one of the Transport Relay candidates from either client (e.g., the internal client obtained a relay candidate from the Transport relay in Office 365 Cloud, the external client needs to be able to send STUN/RTP/RTCP packets to the transport relay). Another option is the internal client sends to the relay candidate obtained by the mobile cloud client. Note that although UDP connectivity for media is highly recommended, TCP is supported.

**High Level Steps**:
1. Teams User A resolves URL domain name (DNS) via flow2
2. Teams User A allocates a media Relay port on Teams Transport Relay via flow 4
3. Teams User A sends "invite" with ICE candidates via flow 4 to Office 365
4. OFFICE 365 sends notification to Teams User B via flow 4
5. Teams User B allocates a media Relay port on Teams Transport Relay via flow 4
6. Teams User B sends "answer" with ICE candidates via flow 4, which is forwarded back to Teams User A via Flow 4
7. Teams User A and Teams User B invoke ICE connectivity tests and the best available media path is selected (see diagrams below for various use cases)
8. Teams Users send telemetry to Office 365 via flow 4

**Within Customer Network:**

[![Microsoft Teams Online Call Flows Figure 02](media/microsoft-teams-online-call-flows-figure02-thumbnail.png)](media/microsoft-teams-online-call-flows-figure02.png)

*Figure 2 - Within Customer Network*
 
In step 7, "peer to peer" media flow 5 is selected 
>**Note**: Media is bidirectional. The direction of flow 5 indicates that one side initiates the communication from connectivity perspective, consistent with all the flows in this document. In this case, it doesn't matter which direction is used because both endpoints are within the Customer Network.

**Customer Network to External User (media relayed by Teams Transport Relay):**

[![Microsoft Teams Online Call Flows Figure 03](media/microsoft-teams-online-call-flows-figure03-thumbnail.png)](media/microsoft-teams-online-call-flows-figure03.png)

*Figure 3 - Customer Network to External User (media relayed by Teams Transport Relay)*
 
In step 7, flow 4, from Customer Network to Office 365, and flow 3, from remote mobile Teams user to Office 365, are selected. These flows are relayed by Teams Transport Relay within Office 365.

>**Note**: Media is bidirectional, where direction indicates which side initiates the communication from connectivity perspective. In this case, these flows are used for signaling and media, via different transport protocols and addresses.

**Customer Network to External User (direct media):**

[![Microsoft Teams Online Call Flows Figure 04](media/microsoft-teams-online-call-flows-figure04-thumbnail.png)](media/microsoft-teams-online-call-flows-figure04.png)

*Figure 4 - Customer Network to External User (direct media)*
 
In step 7, flow 2, from Customer Network to Internet (client's peer), is selected.
>**Notes**: 
>- Direct media with remote mobile user (i.e., not relayed through Office 365 cloud) is optional. In other words, customer may block this path and by doing so, enforce a media path through Transport Relay in Office 365 cloud.
>- Media is bidirectional. The direction of flow 2 to remote mobile user indicates that one side initiates the communication from a connectivity perspective. 

**VPN User to Internal User (media relayed by Teams Transport Relay)**

[![Microsoft Teams Online Call Flows Figure 05](media/microsoft-teams-online-call-flows-figure05-thumbnail.png)](media/microsoft-teams-online-call-flows-figure05.png)

*Figure 5 - VPN User to Internal User (media relayed by Teams Transport Relay)*
 
Signaling VPN to Customer Network via flow 2' and flow 4 to Office 365. However, media "bypass" VPN and routed via flows 3 and 4 through Teams media relay in Office 365 cloud.

**VPN User to Internal User (direct media)**

[![Microsoft Teams Online Call Flows Figure 06](media/microsoft-teams-online-call-flows-figure06-thumbnail.png)](media/microsoft-teams-online-call-flows-figure06.png)

*Figure 6 - VPN User to Internal User (direct media)*

Signaling VPN to Customer Network via flow 2' to Customer Network and flow 4 to Office 365. However, media "bypass" VPN and routed via flow 2 from Customer Network to the internet.

>**Note**: Media is bidirectional. The direction of flow 2 to remote mobile user indicates that one side initiates the communication from a connectivity perspective.

**VPN User to External User (direct media)**

[![Microsoft Teams Online Call Flows Figure 07](media/microsoft-teams-online-call-flows-figure07-thumbnail.png)](media/microsoft-teams-online-call-flows-figure07.png)

*Figure 7 - VPN User to External User (direct media)*

Signaling VPN to Customer Network via flow 2' to Customer Network and flow 4 to Office 365. However, media "bypass" VPN and routed via flow 6.

>**Note**: Media is bidirectional. The direction of flow 6 to remote mobile user indicates that one side initiates the communication from a connectivity perspective.

#### Use Case: Teams to PSTN through Office 365 Trunk
Office 365 has a Phone System that allows placing and receiving calls from the Public Switched Telephone Network. If the PSTN trunk is connected via the Office 365 Phone System Calling Plan, then there are no special connectivity requirements for this use case. (If you want to connect your own on-premises PSTN trunk to Office 365, you can use Phone System Direct Routing.)

[![Microsoft Teams Online Call Flows Figure 08](media/microsoft-teams-online-call-flows-figure08-thumbnail.png)](media/microsoft-teams-online-call-flows-figure08.png)

*Figure 8 - Teams to PSTN through Office 365 Trunk*

#### Use Case: Teams Meeting

The audio/video/screen sharing (VBSS) conferencing server is part of Office 365. It has a public IP address that must be reachable from the Customer Network and must be reachable from a Nomadic Cloud client. Each client/endpoint needs to be able to connect to the conferencing server.

Internal clients will obtain local, reflexive, and relay candidates in the same manner as described for one-to-one calls. The clients will send these candidates to the conference server in an invite. The conferencing server does not use a relay since it has a publicly reachable IP address, so it responds with its local IP address candidate. The client and conferencing server will check connectivity in the same manner described for one-to-one calls. 

>**Notes**:
>- Teams clients cannot join Skype for Business meetings, and Skype for Business clients cannot join Teams meetings.
>- PSTN user optionally "Dials IN" or "Dialed OUT", depends on meeting's organizer PSTN Calling and/or conferencing provisioning. 
>- A guest user or a customer user may join from a guest private network, which is protected via FW/NAT with strict rules.

[![Microsoft Teams Online Call Flows Figure 09](media/microsoft-teams-online-call-flows-figure09-thumbnail.png)](media/microsoft-teams-online-call-flows-figure09.png)

*Figure 9 - Teams Meeting*

#### Use Case: Federation with Skype for Business on premises

**Media relayed by Teams Transport Relay in Office 365 Cloud**

[![Microsoft Teams Online Call Flows Figure 10](media/microsoft-teams-online-call-flows-figure10-thumbnail.png)](media/microsoft-teams-online-call-flows-figure10.png)

*Figure 10 - Media relayed by Teams Transport Relay in Office 365 Cloud*

>**Notes**: 
>- "Federation" is, by definition, a communication between two Tenants. In this case, tenant A, which uses Teams Online, federates with tenant B, which uses Skype for Business on premises. If tenant B is also using Office 365, then the Skype for Business client would have used flow 3 to connect with Office 365.
>- Signaling and media from federated Skype for Business client to on-premises Skype for Business Server is out of scope of this document. However, it is illustrated here for clarity.

Signaling between Teams and Skype for Business is "bridged" by a Gateway in Office 365.

Media in this case is relayed by Teams Transport Relay in Office 365 to Customer Network and remote Skype for Business client via flow 4.

**Media relayed by Skype for Business Media Relay in federated tenant**

[![Microsoft Teams Online Call Flows Figure 11](media/microsoft-teams-online-call-flows-figure11-thumbnail.png)](media/microsoft-teams-online-call-flows-figure11.png)

*Figure 11 - Media relayed by Skype for Business Media Relay in federated tenant*

>**Note**: Signaling and media from federated Skype For Business client to an on-premises Skype for Business Server is out of scope of this document. However, it is illustrated here for clarity.

Signaling between Teams and Skype for Business is "bridged" by a Gateway in Office 365.

Media in this case is relayed by Skype for Business on premises Media Relay to Customer Network via flow 2. (Note that traffic from Teams user to the remote Media Relay in federated customer network will be initially blocked by the Media Relay until traffic in the reverse direction starts to flow. However, the bidirectional flow will open connectivity in both directions.)

**Direct (peer to peer)**

[![Microsoft Teams Online Call Flows Figure 12](media/microsoft-teams-online-call-flows-figure12-thumbnail.png)](media/microsoft-teams-online-call-flows-figure12.png)

*Figure 12 - Direct (peer to peer)*

### Teams Hybrid Topology
This topology is similar to Teams default ("pure") but "adds on" Skype for Business on premises.

[![Microsoft Teams Online Call Flows Figure 13](media/microsoft-teams-online-call-flows-figure13-thumbnail.png)](media/microsoft-teams-online-call-flows-figure13.png)

*Figure 13 - Teams Hybrid Topology*
 
>**Notes**:
>- The direction of the arrows on the diagram above reflect the initiation direction of the communication that affects connectivity at the enterprise perimeters. In the case of UDP for media, the first packet(s) may flow in the reverse direction, but these packets may be blocked until packets in the other direction will flow.
>- Teams is deployed side by side with Skype for Business Online, hence clients are displayed as "Teams/SFB user".

Additional Flows (on top of Teams "pure" topology):
- **Flow 5A** – Represents a peer-to-peer media flow between a Teams user within the Customer Network and a Skype for Business on-premises media relay at the Customer Network edge.

#### Use Case: Teams to Skype for Business one-to-one
**Hybrid within Customer Network**

[![Microsoft Teams Online Call Flows Figure 14](media/microsoft-teams-online-call-flows-figure14-thumbnail.png)](media/microsoft-teams-online-call-flows-figure14.png)

*Figure 14 - Hybrid within Customer Network*
 
Signaling between Teams and Skype for Business is "bridged" by a Gateway in Office 365. However, media is routed directly "peer to peer" within the Customer Network via flow 5.

**Hybrid Customer Network with External Skype for Business user – relayed by Office 365**

[![Microsoft Teams Online Call Flows Figure 15](media/microsoft-teams-online-call-flows-figure15-thumbnail.png)](media/microsoft-teams-online-call-flows-figure15.png)

*Figure 15 - Hybrid Customer Network with external Skype for Business user - relayed by Office 365*
 
>**Note**: Signaling and media from the Skype for Business client to an on-premises Skype for Business Server is out of scope of this document. However, it is illustrated here for clarity.

Signaling between Teams and Skype for Business is "bridged" by a Gateway in Office 365.

Media is relayed through Teams Transport Relay in Office 365 to Customer Network through flow 4.

**Hybrid Customer Network with External Skype for Business user – relayed by on premises edge**

[![Microsoft Teams Online Call Flows Figure 16](media/microsoft-teams-online-call-flows-figure16-thumbnail.png)](media/microsoft-teams-online-call-flows-figure16.png)

*Figure 16 - Hybrid Customer Network with External Skype for Business user - relayed by on premises edge*
 
>**Note**: Signaling and media from Skype for Business client to an on-premises Skype for Business Server is out of scope of this document. However, it is illustrated here for clarity.

Signaling is "bridged" by a Gateway in Office 365.

Media is relayed by Skype for Business Media Relay within Skype for Business on premises Edge to Teams user within Customer Network via media flow 5A.

### Teams with Phone System Direct Routing Topology
This topology is similar to Teams ("pure") but with Phone System Direct Routing. 

Direct Routing enables you to use a third-party Public Switched Telephone Service provider by pairing a supported on-premises customer-owned Session Border Controller hardware device to Office 365, and connecting the telephony trunk to that device. 

To support this scenario, the customer must deploy a certified SBC(s) for Direct Routing from one of Microsoft's certified partners. The SBC must be configured properly, as recommended by the vendor, and be routable from Office 365 for direct UDP traffic. The media may flow directly from Teams and/or Skype for Business client to the SBC (bypass Teams Gateway (i.e., MP)) or traverse through Teams Gateway. The connectivity with the SBC, when the trunk is configured to bypass Teams Gateway, is based on ICE, where SBC supports ICE-Lite, while Teams/Skype for Business media endpoint supports ICE Full. 

[![Microsoft Teams Online Call Flows Figure 17](media/microsoft-teams-online-call-flows-figure17-thumbnail.png)](media/microsoft-teams-online-call-flows-figure17.png)

*Figure 17 - Teams with Phone System Direct Routing topology

>**Notes**:
>- The direction of the arrows on the diagram above reflect the initiation direction of the communication that affects connectivity at the enterprise perimeters. In the case of UDP for media, the first packet(s) may flow in the reverse direction, but these packets may be blocked until packets in the other direction will flow.
>- Teams is deployed side by side with Skype for Business Online, hence clients are displayed as "Teams/SFB user".

Additional Flows (on top of Teams Online "pure" topology):
- **Flow 4'** - Represents a flow from Office 365 cloud to Customer Network, used to establish a connection between Teams media server in the cloud with the SBC on premises.
- **Flow 5B** – Represents a media flow between Teams user within Customer Network with Direct Routing SBC in "bypass" mode.
- **Flow 5C** – Represents a media flow between Direct Routing SBC to another Direct Routing SBC in PSTN hairpin call "bypass" mode.

**Internal User Direct Routing (media relayed by Teams Transport Relay in Office 365)**

[![Microsoft Teams Online Call Flows Figure 18](media/microsoft-teams-online-call-flows-figure18-thumbnail.png)](media/microsoft-teams-online-call-flows-figure18.png)

*Figure 18 - Internal User Direct Routing (media relayed by Teams Transport Relay in Office 365)*
 
>**Note**: SBC MUST have a public IP address that is routable from Office 365.

Signaling and Media from SBC to Office 365 and vice versa use flow 4 and/or flow 4'.

Signaling and Media from client within Customer Network to Office 365 use flow 4.


**Remote User Direct Routing (media is routed through a media server (MP) in Office 365)**

[![Microsoft Teams Online Call Flows Figure 19](media/microsoft-teams-online-call-flows-figure19-thumbnail.png)](media/microsoft-teams-online-call-flows-figure19.png)

*Figure 19 - Remote User Direct Routing (media is routed through a media server (MP) in Office 365)*
 
>**Note**: SBC MUST have a public IP address that is routable from Office 365.

Signaling and Media from SBC to Office 365 and vice versa use flow 4 and/or flow 4'.

Signaling and Media from client on the Internet to Office 365 cloud use flow 3.

**Internal user Direct Routing (media bypass)**

[![Microsoft Teams Online Call Flows Figure 20](media/microsoft-teams-online-call-flows-figure20-thumbnail.png)](media/microsoft-teams-online-call-flows-figure20.png)

*Figure 20 - Internal user Direct Routing (media bypass)*
 
>**Note**: SBC MUST have a public IP address that is routable from Office 365.

Signaling from SBC to Office 365 and vice versa use flow 4 and/or flow 4'.

Signaling from client within Customer Network to Office 365 cloud use flow 4.

Media from client within Customer Network to SBC within Customer Network use flow 5B.

**Remote user Direct Routing (media bypass relayed by Teams Transport Relay in Office 365)**

[![Microsoft Teams Online Call Flows Figure 21](media/microsoft-teams-online-call-flows-figure21-thumbnail.png)](media/microsoft-teams-online-call-flows-figure21.png)

*Figure 21 - Remote user Direct Routing (media bypass relayed by Teams Transport Relay in Office 365)*
 
>**Note**: SBC MUST have a public IP address that is routable from Office 365 and Internet.

Signaling from SBC to Office 365 and vice versa use flow 4 and/or flow 4'.

Signaling from client on the Internet to Office 365 cloud use flow 3.

Media from client on the Internet to SBC within Customer Network use flows 3 and 4, relayed by Teams Transport Relay in Office 365 cloud. 

**Remote user Direct Routing (media bypass direct)**

[![Microsoft Teams Online Call Flows Figure 22](media/microsoft-teams-online-call-flows-figure22-thumbnail.png)](media/microsoft-teams-online-call-flows-figure22.png)

*Figure 22 - Remote user Direct Routing (media bypass direct)*
 
>**Note**: SBC MUST have a public IP address that is routable from Office 365 and Internet.

Signaling from SBC to Office 365 and vice versa use flow 4 and/or flow 4'.

Signaling from client on the Internet to Office 365 cloud use flow 3.

Media from client on the Internet to SBC within Customer Network use flow 2.

**Direct Routing (media bypass) – PSTN hairpin call (due to call forward/transfer)**

[![Microsoft Teams Online Call Flows Figure 23](media/microsoft-teams-online-call-flows-figure23-thumbnail.png)](media/microsoft-teams-online-call-flows-figure23.png)

*Figure 23 - Direct Routing (media bypass) - PSTN hairpin call (due to call forward/transfer)*
 
>**Note**: SBC MUST have a public IP address that is routable from Office 365.

Signaling from SBC to Office 365 and vice versa use flow 4 and/or flow 4'.

Client is out of the signaling and media loop after the call is hairpin from PSTN to PSTN.

Media from SBC instance A within Customer Network to SBC instance B within Customer Network (where, A and B can be the same instance) use flow 5C.

**Direct Routing (media through Office 365) – PSTN hairpin call across two tenants**

[![Microsoft Teams Online Call Flows Figure 24](media/microsoft-teams-online-call-flows-figure24-thumbnail.png)](media/microsoft-teams-online-call-flows-figure24.png)

*Figure 24 - Direct Routing (media through Office 365) – PSTN hairpin call across two tenants*
 
>**Note**: SBC MUST have a public IP address that is routable from Office 365.

Signaling from SBC to Office 365 and vice versa use flow 4 and/or flow 4'.

Client is out of the signaling and media loop after the call is hairpin from PSTN to PSTN.

Media from SBC instance A within Customer Network X to SBC instance B must be relayed through the Office 365 Media Server and can't use bypass mode.

## Teams w/ Express Route optimization

[![Microsoft Teams Online Call Flows Figure 25](media/microsoft-teams-online-call-flows-figure25-thumbnail.png)](media/microsoft-teams-online-call-flows-figure25.png)

*Figure 25 - Teams with Express Route optimization*
 
In the case that Express Route is justified and deployed, then Teams flows could be re-routed from flow 4 to flow 1 and from flow 4' to flow 1'. However, Teams Application has a hard dependency on other Office 365 flows over the internet via flows 4 and 4'; hence these flows must not be blocked. 

Note that Skype for Business hybrid Edge traffic is routed to the Internet and not to Express Route to communicate with external users and "federation" with other tenants. 

To prevent asymmetrical flows, re-routing must be in both directions. In other words, an address within Customer Network is routable either through Internet or Express Route, based on optimization, but not through both.

For example:

**Customer Network to External User (media relayed by Teams Transport Relay):**

[![Microsoft Teams Online Call Flows Figure 26](media/microsoft-teams-online-call-flows-figure26-thumbnail.png)](media/microsoft-teams-online-call-flows-figure26.png)

*Figure 26 - Customer Network to External User (media relayed by Teams Transport Relay)*
 
**High Level Steps:**
1. Teams User within Customer Network resolves URL domain name (DNS) via flow2
2. Teams User within Customer Network allocates a media Relay port on Teams Transport Relay via flow 1
3. Teams User within Customer Network sends "invite" with ICE candidates via flow 1 to Office 365
4. OFFICE 365 sends notification to external Teams User via flow 3
5. Teams external User allocates a media Relay port on Teams Transport Relay via flow 3
6. Teams external User sends "answer" with ICE candidates via flow 3, which is forwarded back to Teams User A via Flow 1
7. Teams User A and Teams User B invoke ICE connectivity tests and selects flows 1 and 3, which are relayed by Teams Transport Relay in Office 365 cloud.
8. Teams Users send telemetry to Office 365 via flows 1 and 3

>**Note**: Flow 4 must be enabled to support dependencies of Teams application on other micro-services that mandates flow 4.
