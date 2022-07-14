---
title: "Plan for media bypass with Direct Routing"
ms.author: crowe
author: CarolynRowe
manager: serdars
audience: ITPro
ms.reviewer: NMuravlyannikov
ms.topic: article
ms.service: msteams
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-voice
appliesto: 
  - Microsoft Teams
f1.keywords:
- NOCSH
description: Learn how to plan for media bypass with Phone System Direct Routing, which enables you to shorten the path of media traffic and improve performance.
ms.custom: seo-marvel-apr2020
---

# Plan for media bypass with Direct Routing

## About media bypass with Direct Routing

Media bypass enables you to shorten the path of media traffic and reduce the number of hops in transit for better performance. With media bypass, media is kept between the Session Border Controller (SBC) and the client instead of sending it via the Microsoft Phone System. To configure media bypass, the SBC and the client must be in the same location or network.

You can control media bypass for each SBC by using the **Set-CSOnlinePSTNGateway** command with the **-MediaBypass** parameter set to true or false. If you enable media bypass, this does not mean that all media traffic will stay within the corporate network. This article describes the call flow in different scenarios.

The diagrams below illustrate the difference in call flow with and without media bypass.

Without media bypass, when a client makes or receives a call, both signaling and media flow between the SBC, the Microsoft Phone System, and the Teams client, as shown in the following diagram:

> [!div class="mx-imgBorder"]
> ![Shows signaling and media flow without media bypass.](media/direct-routing-media-bypass-1.png)


But let's assume that a user is in the same building or network as the SBC. For example, assume a user who is in a building in Frankfurt makes a call to a PSTN user: 

- **Without media bypass**, media will flow via either Amsterdam or Dublin (where Microsoft datacenters are deployed) and back to the SBC in Frankfurt. 

  The datacenter in Europe is selected because the SBC is in Europe, and Microsoft uses the datacenter closest to the SBC. While this approach does not affect call quality due to optimization of traffic flow within Microsoft networks in most geographies, the traffic has an unnecessary loop.     

- **With media bypass**, the media is kept directly between the Teams user and the SBC as shown in the following diagram:

  > [!div class="mx-imgBorder"]
  > ![Shows signaling and media flow with media bypass.](media/direct-routing-media-bypass-2.png)

Media bypass leverages protocols called Interactive Connectivity Establishment (ICE) on the Teams client and ICE lite on the SBC. These protocols enable Direct Routing to use the most direct media path for optimal quality. ICE and ICE Lite are WebRTC standards. For detailed information about these protocols, see RFC 5245.


## Call flow and firewall planning

Call flow and firewall planning depends on whether the user has direct access to the public IP address of the SBC, and whether the user is inside or outside of the network.

### Call flow if the user has direct access to the public IP address of the SBC

If the user has direct access to the public IP address of the SBC, the call flow is as follows:

- For media bypass, the Teams client must have access to the public IP address of the SBC even from an internal network. If direct media is not desired, the media can flow via Transport Relays.

- This is the recommended solution when a user is in the same building and/or network as the SBC – remove Microsoft Cloud components from the media path.

- Signaling always flows via the Microsoft cloud.

The following diagram shows call flow when media bypass is enabled, the client is internal, and the client can reach the public IP address of the SBC (direct media): 

- The arrows and numeric values of the paths are in accordance with [Microsoft Teams call flows](./microsoft-teams-online-call-flows.md).

- The SIP signaling always takes paths 4 and 4' (depending on the direction of the traffic). Media stays local and takes path 5b.

> [!div class="mx-imgBorder"]
> ![Shows Call flow with Media Bypass enabled, client is internal.](media/direct-routing-media-bypass-3.png)


### Call flow if the user does not have access to the public IP address of the SBC

The following describes call flow if the user does not have access to the public IP address of the SBC. 

For example, assume the user is external, and the tenant administrator decided not to open the public IP address of the SBC to everyone in the Internet, but only to the Microsoft Cloud. The internal components of traffic can flow via the Teams Transport Relays. Consider the following:

- Teams Transport Relays are used.

- For media bypass, Microsoft uses a version of Transport Relays that requires opening ports 50 000 to 59 999 between the Teams Transport Relays and the SBC (in the future we plan to move to the version which requires 3478-3481 ports).


The following diagram shows call flow when media bypass is enabled, the client is external, and the client cannot reach the public IP address of the Session Border Controller (media is relayed by Teams Transport Relay).

- The arrows and numeric values of the paths are in accordance with [Microsoft Teams call flows](./microsoft-teams-online-call-flows.md).

- Media is relayed via paths 3, 3', 4 and 4'

> [!div class="mx-imgBorder"]
> ![Shows Call flow if user does not have access to public IP of the SBC.](media/direct-routing-media-bypass-4.png)


### Call flow if a user is outside the network and has access to the public IP of the SBC

> [!NOTE]
> This is not a recommended configuration because it does not take advantage of Teams Transport Relays. Instead, you should consider the previous scenario where the user does not have access to the public IP address of the SBC. 

The following diagram shows call flow when media bypass is enabled, the client is external, and the client can reach the public IP address of the SBC (direct media).

- The arrows and numeric values of the paths are in accordance with the [Microsoft Teams call flows](./microsoft-teams-online-call-flows.md) article.

- The SIP signaling always takes paths 3 and 3' (depending on the direction of the traffic). Media flows using path 2.

> [!div class="mx-imgBorder"]
> ![Shows Call flow if user does not have access to public IP of the SBC.](media/direct-routing-media-bypass-5.png)



## Use of Media Processors and Transport Relays

There are two components in the Microsoft Cloud that can be in the path of media traffic: Media Processors and Transport Relays. 

- The Media Processor is a public facing component that handles media in non-bypass cases and handles media for voice applications.

   Media Processors are always in the path for end user non-bypassed calls, but never in the path for bypassed calls. Media Processors are always in the path for all voice applications such as Call Park, Organizational Auto Attendant, and Call Queues.

- The Transport Relay is used to connect to the closest Transport Service to send real time traffic.

   Transport Relays might or might not be in the path for bypassed calls--originating from or destined to end users--depending on where the user is and how the network is configured .

The following diagram shows two call flows – one with media bypass enabled and the second with media bypass disabled.

> [!NOTE]
> The diagram only illustrates traffic originating from--or destined to--end users.  

- The Media Controller is a microservice in Azure that assigns Media Processors and creates Session Description Protocol (SDP) offers.

- The SIP Proxy is a component that translates HTTP REST signaling used in Teams to SIP.    

> [!div class="mx-imgBorder"]
> ![Shows call flows with Media Bypass enabled and disabled.](media/direct-routing-media-bypass-6.png)


The table below summarizes the difference between Media Processors and Transport Relays.

|  &nbsp; | Media Processors | Transport Relays|
| :--------------|:---------------|:------------|
|In media path for non-bypassed calls for end users | Always | If client cannot reach the Media Processor directly |
|In media path for bypassed calls for end users | Never | If client cannot reach the SBC on the public IP address |
|In media path for voice applications | Always | Never |
|Can do transcoding (B2BUA)\* | Yes | No, only relays audio between endpoints |
|Number of instances worldwide and location | 15 total: 3 in US East, West, and South Central; 4 in Amsterdam, Dublin, UK South, and France Central; 2 in Hong Kong and Singapore; 2 in Japan; 2 in Australia East and Southeast; 1 in Brazil South; 1 in South Africa North | Multiple|

The IP ranges are:
- 52.112.0.0/14 (IP addresses from 52.112.0.1 to 52.115.255.254)
- 52.120.0.0/14 (IP addresses from 52.120.0.1 to 52.123.255.254)

\* Transcoding explanation: 

- Media Processor is B2BUA, which means it can change a codecs (for example, SILK from Teams client to MP and G.711 between MP and SBC).

- Transport Relays are not B2BUA, which means the codec is never changed between the client and the SBC--even if traffic flows via relays.

### Use of Teams Media Processors if trunk is configured for media bypass

Teams Media Processors are always inserted in the media path in the following scenarios:

- Call is escalated from 1:1 to a group call
- Call is going to a federated Teams user
- Call is forwarded or transferred to a Skype for Business user

Ensure your SBC has access to the Media Processors and Transport Relays ranges as described below.    


## SIP Signaling: FQDNs

For SIP signaling, the FQDN and firewall requirements are the same as for non-bypassed cases. 

Direct Routing is offered in the following Microsoft 365 or Office 365 environments:
- Microsoft 365 or Office 365
- Office 365 GCC
- Office 365 GCC High
- Office 365 DoD
Learn more about [Office 365 and US Government environments](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/office-365-us-government) such as GCC, GCC High, and DoD.

### Microsoft 365, Office 365, and Office 365 GCC environments

The connection points for Direct Routing are the following three FQDNs:

- **sip.pstnhub.microsoft.com** – Global FQDN – must be tried first. When the SBC sends a request to resolve this name, the Microsoft Azure DNS servers return an IP address pointing to the primary Azure datacenter assigned to the SBC. The assignment is based on performance metrics of the datacenters and geographical proximity to the SBC. The IP address returned corresponds to the primary FQDN.

- **sip2.pstnhub.microsoft.com** – Secondary FQDN – geographically maps to the second priority region.

- **sip3.pstnhub.microsoft.com** – Tertiary FQDN – geographically maps to the third priority region.

You must place these three FQDNs in order to:

- Provide optimal experience (less loaded and closest to the SBC datacenter assigned by querying the first FQDN).

- Provide failover when a connection from an SBC is established to a datacenter that is experiencing a temporary issue. For more information, see Failover mechanism below.


The FQDNs **sip.pstnhub.microsoft.com**, **sip2.pstnhub.microsoft.com**, and **sip3.pstnhub.microsoft.com** will be resolved to IP addresses from the following subnets:
- 52.112.0.0/14
- 52.120.0.0/14

You need to open ports for all these IP ranges in your firewall to allow incoming and outgoing traffic to and from the addresses for signaling.

### Office 365 GCC DoD environment

The connection point for Direct Routing is the following FQDN:

**sip.pstnhub.dod.teams.microsoft.us** – Global FQDN. As the Office 365 DoD environment exists only in the US data centers, there is no secondary and tertiary FQDNs.

The FQDN sip.pstnhub.dod.teams.microsoft.us will be resolved to an IP address from the following subnet:

- 52.127.64.0/21

You need to open ports for all these IP ranges in your firewall to allow incoming and outgoing traffic to and from the addresses for signaling.  If your firewall supports DNS names, the FQDN  sip.pstnhub.dod.teams.microsoft.us resolves to all these IP subnets. 

### Office 365 GCC High environment

The connection point for Direct Routing is the following FQDN:

**sip.pstnhub.gov.teams.microsoft.us** – Global FQDN. As the GCC High environment exists only in the US data centers, there is no secondary and tertiary FQDNs.

The FQDN sip.pstnhub.gov.teams.microsoft.us will be resolved to an IP address from the following subnet:

- 52.127.88.0/21

You need to open ports for all these IP ranges in your firewall to allow incoming and outgoing traffic to and from the addresses for signaling.  If your firewall supports DNS names, the FQDN  sip.pstnhub.gov.teams.microsoft.us resolves to all these IP subnets. 

## SIP Signaling: Ports

Port requirements are the same for all Office 365 environments where Direct Routing is offered:
- Microsoft 365 or Office 365
- Office 365 GCC
- Office 365 GCC High
- Office 365 DoD

You must use the following ports:

| Traffic | From | To | Source port | Destination port|
| :-------- | :-------- |:-----------|:--------|:---------|
| SIP/TLS| SIP Proxy | SBC | 1024 - 65535 | Defined on the SBC |
| SIP/TLS | SBC | SIP Proxy | Defined on the SBC | 5061 |


## Media traffic: IP and Port ranges

Media traffic flows between the SBC and Teams client if direct connectivity is available or via Teams Transport Relays if the client cannot reach the SBC using the public IP address.

### Requirements for direct media traffic (between the Teams client and the SBC) 

The client must have access to the specified ports (see table) on the public IP address of the SBC. 

> [!NOTE]
> If the client is in an internal network, the media flows to the public IP address of the SBC. You can configure hair pinning on your NAT device so traffic never leaves the enterprise network equipment.

| Traffic | From | To | Source port | Destination port|
| :-------- | :-------- |:-----------|:--------|:---------|
| UDP/SRTP | Client | SBC | 50000-50019| Defined on the SBC |
| UDP/SRTP | SBC | Client | Defined on the SBC | 50000-50019  |


> [!NOTE]
> If you have a network device that translates the client's source ports, please make sure that translated ports are opened between the network equipment and the SBC. 

### Requirements for using Transport Relays

Transport Relays are in the same range as Media Processors (for non-bypass cases): 

### Microsoft 365, Office 365, and Office 365 GCC environments

- 52.112.0.0 /14 (IP addresses from 52.112.0.1 to 52.115.255.254)

### Office 365 GCC DoD environment

- 52.127.64.0/21

### Office 365 GCC High environment

- 52.127.88.0/21


The port range of the Teams Transport Relays (applicable to all environments) is shown in the following table:


| Traffic | From | To | Source port | Destination port|
| :-------- | :-------- |:-----------|:--------|:---------|
| UDP/SRTP | Transport Relay | SBC | 50 000 -59 999    | Defined on the SBC |
| UDP/SRTP | SBC | Transport Relay | Defined on the SBC | 50 000 – 59 999, 3478-3481     |


> [!NOTE]
> Microsoft recommends at least two ports per concurrent call on the SBC. Because Microsoft has two versions of Transport Relays, the following are required:
> 
> - v4, which can only work with port range 50 000 to 59 999
> 
> - v6, which works with ports 3478-3481

At this time, media bypass only supports v4 version of Transport Relays. We will introduce support of v6 in the future. 

You need to open ports 3478-3481 for transitioning. When Microsoft introduces support for v6 Transport Relays with Media Bypass, you will not need to reconfigure your network equipment or SBCs. 

### Requirements for using media processors

Media Processors are always in the media path for voice applications and for Web clients (for example, Teams clients in Edge or Google Chrome). The requirements are the same as for non-bypass configuration.


The IP range for media traffic is 

### Office 365 and Office 365 GCC environments

- 52.112.0.0 /14 (IP addresses from 52.112.0.1 to 52.115.255.254)

### Office 365 GCC DoD environment

- 52.127.64.0/21

### Office 365 GCC High environment

- 52.127.88.0/21

The port range of the Media Processors (applicable to all environments) is shown in the following table:

| Traffic | From | To | Source port | Destination port|
| :-------- | :-------- |:-----------|:--------|:---------|
| UDP/SRTP | Media Processor | SBC | 3478-3481 and 49 152 – 53 247    | Defined on the SBC |
| UDP/SRTP | SBC | Media Processor | Defined on the SBC | 3478-3481 and 49 152 – 53 247     |

## Configure separate trunks for media bypass and non-media bypass  

If you are migrating to media bypass from non-media bypass and want to confirm functionality before migrating all usage to media bypass, you can create a separate trunk and separate Online Voice Routing policy to route to the media bypass trunk and assign to specific users. 

High-level configuration steps:

- Identify users to test media bypass.

- Create two separate trunks with different FQDNs: one enabled for media bypass; the other not. 

  Both trunks point to the same SBC. The ports for TLS SIP signaling must be different. The ports for media must be the same.

- Create a new Online Voice Routing policy and assign the media bypass trunk to the corresponding routes associated with the PSTN usage for this policy.

- Assign the new Online Voice Routing policy to users you have identified to test media bypass.

The example below illustrates this logic.

| Set of users | Number of users | Trunk FQDN assigned in OVRP | Media bypass enabled |
| :------------ |:----------------- |:--------------|:--------------|
| Users with non-media bypass trunk | 980 | sbc1.contoso.com:5061 | false |
| Users with media bypass trunk | 20 | sbc2.contoso.com:5060 | true | 

Both trunks can point to the same SBC with the same public IP address. The TLS signaling ports on the SBC must be different, as shown in the following diagram. Note you will need to make sure that your certificate supports both trunks. In SAN, you need to have two names (**sbc1.contoso.com** and **sbc2.contoso.com**) or have a wildcard certificate.

> [!div class="mx-imgBorder"]
> ![Shows both trunks can point to the same SBC with the same public IP.](media/direct-routing-media-bypass-7.png)

For information about how to configure two trunks on the same SBC, see the documentation provided by your SBC vendor:

 - [AudioCodes deployment documentation](https://www.audiocodes.com/solutions-products/products/products-for-microsoft-365/direct-routing-for-microsoft-teams)
- [Oracle deployment documentation](https://www.oracle.com/industries/communications/enterprise-session-border-controller/microsoft.html)
- [Ribbon Communications deployment documentation](https://ribboncommunications.com/solutions/enterprise-solutions/microsoft-solutions/direct-routing-microsoft-teams-calling)
- [TE-Systems (anynode) deployment documentation](https://www.anynode.de/anynode-and-microsoft-teams/)

## Client endpoints supported with media bypass

Media bypass is supported with all standalone Teams Desktop clients, Android and iOS clients and Teams Phone Devices. 

For all other endpoints that do not support media bypass, we will convert the call to non-bypass even if it started as a bypass call. This happens automatically and does not require any actions from the administrator. This includes Skype for Business 3PIP Phones, and Teams Web Clients that support Direct Routing calling (WebRTC based clients running on Microsoft Edge, Google Chrome, Mozilla Firefox). 
 
## See also

[Configure media bypass with Direct Routing](direct-routing-configure-media-bypass.md)
