---
title: Direct Routing Local Media Optimization
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.date: 01/28/2019
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-voice
ms.reviewer: crowe
search.appverid: MET150
f1.keywords: ms.teamsadmincenter.directrouting.overview
f1.keywords:
- NOCSH
description: Landing page for Direct Routing
appliesto: 
  - Microsoft Teams
---

# Local Media Optimization for Direct Routing

Public Switched Telephone Network (PSTN) voice is considered a business-critical application with high expectations for voice quality. Direct Routing lets you control media traffic flows to accommodate a multitude of network topologies and local telephony setups for various enterprises all over the world. 

Local Media Optimization for Direct Routing lets you manage voice quality by:

-	Controlling how media traffic flows between the Teams clients and the customer Session Border Controllers (SBCs).
-	Keeping media local within the boundaries of corporate network subnets.
-	Allowing media streams between the Teams clients and the SBCs even if the SBCs are behind corporate firewalls with private IPs and not visible to Microsoft directly.

Media Path Optimization supports two scenarios:

- Centralization of all local trunks through a centralized SBC connected to the main SIP trunk, providing telephony services to all local branch offices of the company.

- 	Building a virtual network topology of SBCs, where the SBCs in the local branch offices are connected to a centralized proxy SBC that is visible to, and communicating with, Microsoft Phone System through its external IP address. In a virtual network topology, downstream SBCs are communicating through internal IPs and are not directly visible to Microsoft Phone System.



## A customer scenario

Assume that Contoso runs multiple businesses across the globe as follows:

Note: Europe and APAC regions are used as examples only. Company might have several different regions with such or similar requirements.
 
- In Europe, Contose has offices in approximately 30 countries. Each office has its own PBX. 

  Contoso was offered an option to centralize the trunks in one location – Amsterdam for all 30 European offices. Contoso deployed the SBC in Amsterdam, provided enough bandwidth to run calls via the centralized location, connected a central SIP trunk to it and started serving all European locations from Amsterdam. 

- In APAC region, Contoso has multiple offices in different countries. 

  In many countries, the company still has TDM trunks in local branch offices. Centralization of the TDM trunks is not an option in the APAC region, so switching to SIP is not possible. Assume there are more than fifty Contoso branch offices across the APAC region with hundreds of gateways (SBCs). In this scenario, it is not possible to pair all gateways to the Direct Routing interface because of a  lack of public IP addresses and/or local internet breakouts. In addition, some countries impose regulatory requirements that cannot be fulfilled without having a local PSTN network connectivity.


## Supported scenarios

Contoso implemented two scenarios based on Local Media Optimization for Direct Routing:

- In Europe, all trunks are centralized and media flows between the central SBC and the users, based on the user location. 

  If a user is connected to the local subnet of a corporate network (that is, the user is internal), media flows between the internal IP of the central SBC and the user’s Teams client. 
  
  If a user is outside the boundaries of the corporate network--for example, if the user is using a public wireless internet connection, then the user is considered to be external. In this case, the media flows between the external IP of the central SBC and the Teams client.

- In the APAC region, a centralized proxy SBC is paired to Microsoft Direct Routing, which directs media between the Direct Routing interface and the downstream SBCs in local branch offices. 

  The downstream SBCs in the local branch offices are not directly visible to Direct Routing in APAC,  but they are paired by using the Set-CSOnlinePSTNGateway cmdlet creating a virtual network topology within Microsoft Phone System. Media always stays local when possible. External users have media flowing between the Teams client and the public IP of the proxy SBC.


## Central SBC with centralized trunks
In order to build a solution where PSTN services are provided to all local branch offices via single central SBC with connected centralized SIP trunk, Contoso tenant administrator paired one SBC (centralsbc.contoso.com) to the service, the SBC has a centralized SIP trunk connected to it. When user is in internal network of the company the SBC provides internal IP of the SBC for media, when user is outside of the corporate network, the SBC provides the external (public) IP of the SBC.

Note: All values within examples, tables or images below are presented only for illustration purposes and are not mandatory or recommended in any way


| Location | SBC FQDN | Internal subnet | External NAT for Internet egress | External IP address of the SBC | Internal IP Address of the SBC |
|:------------|:-------|:-------|:-------|:-------|:-------|
| Amsterdam | centralsbc.contoso.com | centralsbc.contoso.com | centralsbc.contoso.com |52.114.76.71| 192.168.5.5 |
| Germany | Not deployed | 192.168.6.0/24 | 52.114.76.74 | Not deployed |  Not deployed |
| France | Not deployed | 192.168.7.0/24 | 52.114.76.75 | Not deployed |  Not deployed ||||



### Internal user
The following diagram shows the traffic flow when a user is connected to the corporate network in the user’s home branch office or site. 

While on premises, the user is assigned to the local branch office in Germany.  When the user makes a Direct Routing based phone call through Teams, the user’s Teams client communicates to Phone System directly through the REST API, but the media generated during the call flows to the central SBC’s internal IP address. The SBC redirects the flow to  Phone System and the connected PSTN network. The central SBC is visible to  Phone System through the external IP address only. 

INSERT DIAGRAM HERE


### External user

The following diagram shows the traffic flow when a user is outside of the office and is not connected to the corporate network. 

The user is not on premises and is not within the boundaries of the corporate network (that is, the user’s device is connected to the internet through a  mobile device or public Wi-Fi). When the user makes a Direct Routing based phone call through Teams, the user’s Teams client communicates to Phone System directly through the REST API, but, in this case, the media generated during the call flows to the central SBC’s external IP address. The SBC redirects the flow to  Phone System and connected PSTN network. Central SBC is visible to Microsoft Phone System via external IP address only. In this case the behavior is similar no matter the user is local to Germany branch office or any other branch office. User is considered external, because of being outside the boundaries of corporate network.

INSERT DIAGRAM HERE

## Proxy SBC with connected downstream SBCs

In order to build a solution where PSTN services are provided in all local branch offices in APAC region where centralization of the TDM trunks is not an option, Contoso administrator paired one SBC (proxysbc.contoso.com) also called as proxy SBC to the Direct Routing service. 
Afterwards, Contoso administrator added some downstream SBCs using PowerShell cmdlet (more details on required steps below in Configuration chapter), indicating that they can be reached via the proxy SBC proxysbc.contoso.com. Downstream SBCs do not have public IPs, however they can be assigned to voice routes. The table below shows the example of network parameters and configuration.
When user is in the local branch office where the downstream SBC is located, the media traffic flows between the user and the local downstream SBC directly. If user is outside of the office (on a public internet or in a different office) the media flows from the user to the public IP of the Proxy SBC, which proxies it to the relevant downstream SBC (s).



| Location | SBC FQDN | Internal subnet | External NAT for Internet egress | External IP address of the SBC | Internal IP Address of the SBC |
|:------------|:-------|:-------|:-------|:-------|:-------|
| Singapore | 192.168.3.0/24 | 99.66.240.130 | proxysbc.contoso.com | 96.66.240.133 | 192.168.3.5 |
| Vietnam | 192.168.1.0/24 | 99.66.240.110 | VNsbc.contoso.com | None |  192.168.1.5 |
| Indonesia  | 192.168.2.0/24 | 99.66.240.120 | IDsbc.contoso.com | None |  192.168.2.5 |



### Internal user 

The illustration below shows the high-level traffic flow for the scenario when user is inside the office in APAC region. On the image below user assigned to local branch office in Vietnam, while on premises, makes a Direct Routing based phone call via Teams. User’s Teams client communicates with Microsoft Phone System directly via REST API, but media generated during the call flows to local SBC’s internal IP address. Local SBC redirects the flow to proxy SBC in Singapore and connected local PSTN network. Proxy SBC is visible to Microsoft Phone System via external IP address only and routes the flow from downstream SBC (in this case local SBC in Vietnam) to Microsoft Phone System. Downstream SBC in local branch office is not visible to Microsoft Phone System directly but is mapped within the virtual network topology that needs to be defined by Contoso administrator while setting up Media Path Optimization.
Note: The behavior might be different for local users and non-local users depending on the configured Media Path Optimization mode. More details on possible modes and relevant behavior is presented in next chapter. 

INSERT DIAGRAM HERE

### External user

The figure below shows the traffic flow when a user is outside of the corporate network boundaries. On the illustration user is not on premises (is not within the boundaries of corporate network). User makes a Direct Routing based phone call via Teams to Vietnamese phone number. User’s Teams client communicates with Microsoft Phone System directly via REST API, but media generated during the call flows first to external IP address of the proxy SBC in Singapore. Based on configuration and voice policies (more details in Configuration chapter below) proxy SBC redirects the flow to downstream SBC in Vietnam. Downstream SBC in Vietnam redirects the flow to connected local PSTN network. Proxy SBC is visible to Microsoft Phone System via external IP address only. Downstream SBC in local branch office is not visible to Microsoft Phone System directly but is mapped within the virtual network topology that needs to be defined by Contoso administrator while setting up Media Path Optimization. In the example user is considered external, because of being outside the boundaries of corporate network. 

INSERT DIAGRAM HERE


## Local Media Optimization modes
Local Media Optimization technology supports two modes:

- Mode 1: Always bypass. In this case if user is internal, the media will flow via local downstream SBC’s internal IP address no matter the actual location of the internal user (e.g. within the same branch office where downstream SBC is located or in some other branch office)

- Mode 2: Only for local users. In this mode media will flow directly to local downstream SBC’s internal IP address only when generated by internal user located in the same branch office as the downstream SBC. 

To distinguish between Media Path Optimization modes, the tenant administrator needs to set the -BypassMode parameter to either ‘Always’ or ‘OnlyForLocalUsers’ in PowerShell cmdlet Set-CSonlinePSTNGateway for every SBC. More details presented in Configuration chapter below.

Modes applicability, best practices
### Mode 1: Always Bypass

Good connection between branch offices – recommended mode is “Always bypass”.

Example: A company has a centralized SIP trunk in Amsterdam, which serves 30 countries and has good connectivity between all these 30 sites and local users. Also, there is a branch in Hungary where a local SBC is deployed. In this case the SBC in Hungary can be configured in “Always bypass” mode. Users regardless of the location will connect to the SBC directly via internal IP address of the SBC (for example from Germany to Hungary, see pictures below for reference).
Case One. The user is in the same location as the SBC defined in Voice Routing Policy
SBC in Amsterdam is configured to be a proxy SBC for a local downstream SBC in Hungary. User is in Hungary within the same subnet of corporate network as local SBC. Both SBCs (proxy and downstream) are configured for Always Bypass mode. Voice routing policies specify that in case of Hungarian calls (with area code +36) they should be routed to local Hungarian SBC. All other calls and, in case Hungarian SBC fails, Hungarian calls should be routed to proxy SBC in Amsterdam. Table below summarizes the example configuration. 


| User physical location | User makes a call to a number | Voice Routing Policy | Mode configured for SBC | Media Flow | 
|:------------|:-------|:-------|:-------|:-------|
| Hungary | +36 1 437 2800 | Priority 1: ^\+36(\d{8})$ -HUsbc.contoso.com <br> Priority 2: .* - proxysbc.contoso.com | HUsbc.contoso.com – Always Bypass <br> proxysbc.contoso.com – Always Bypass | Teams User <–> HUsbc.contoso.com |

The diagram below shows the high-level traffic flow for internal user in Hungary making a Direct Routing based phone call via Teams to Hungarian number. User’s Teams client communicates with Microsoft Phone System directly via REST API, and media generated during the call flows to local SBC’s internal IP address. Local SBC redirects the flow to proxy SBC in Amsterdam and connected local PSTN network. Proxy SBC is visible to Microsoft Phone System via external IP address only and routes the flow from downstream SBC (in this case local SBC in Hungary) to Microsoft Phone System. Downstream SBC in local branch office is not visible to Microsoft Phone System directly but is mapped within the virtual network topology that needs to be defined by Contoso administrator while setting up Media Path Optimization.


INSERT DIAGRAM HERE



**User and gateways are in different sites**
SBC in Amsterdam is configured to be a proxy SBC for a local downstream SBC in Hungary. Both SBCs (proxy and downstream) are configured for Always Bypass mode. Internal user in Germany located in local branch office is making a Direct Routing call to Hungary. Voice routing policies specify that in case of Hungarian calls (with area code +36) they should be routed to local Hungarian SBC. All other calls and, in case Hungarian SBC fails, Hungarian calls should be routed to proxy SBC in Amsterdam. Table below summarizes the example configuration. 


| User physical location | User makes a call to a number | Voice Routing Policy | Mode configured for SBC | Media Flow | 
|:------------|:-------|:-------|:-------|:-------|
| Germany | +36 1 437 2800 | Priority 1: ^\+36(\d{8})$ -HUsbc.contoso.com <br>Priority 2: .* - proxysbc.contoso.com |  HUsbc.contoso.com – Always Bypass proxysbc.contoso.com – Always Bypass | Teams User <– > HUsbc.contoso.com |


The diagram below shows the high-level traffic flow when internal Hungarian user in Germany makes a Direct Routing based phone call via Teams to Hungarian number. User’s Teams client communicates with Microsoft Phone System directly via REST API, and media generated during the call flows directly to Hungarian SBC’s internal IP address. Hungarian SBC redirects the flow to proxy SBC in Amsterdam and connected local PSTN network. 

INSERT DIAGRAM HERE

### Mode 2: Only for local users


Bad connection between local branch offices but good connection between each local branch office and regional office – recommended mode is “Only For Local Users”

Example: In APAC region Contoso has multiple offices in different countries. In many countries switching to SIP is not possible, company still has TDM trunks in many local branch offices. Centralization of the TDM trunks is not an option in the APAC region. Moreover, there are more than fifty Contoso branch offices across APAC region with hundreds of gateways (SBCs). In order to build a solution where PSTN services are provided in all local branch offices in APAC region where centralization of the TDM trunks is not an option, Contoso administrator paired one regional SBC in Singapore as proxy SBC to the Direct Routing service. Direct connection between local branch offices is bad but there is a good connection between each local branch office and regional SBC in Singapore. For regional SBC administrator chose ‘Always Bypass’ mode and for local downstream SBCs ‘Only For Local Users’ mode.

**Case One. The user is in the same location as the SBC defined in Voice Routing Policy**
SBC in Singapore is configured to be a proxy SBC for local downstream SBCs in Vietnam and Indonesia. User is in Vietnam within the same location as local SBC. Voice routing policies specify that in case of Vietnamese calls (with area code +84) they should be routed to local Vietnamese SBC. All other calls and, in case Vietnamese SBC fails, Vietnamese calls should be routed to proxy SBC in Singapore. Table below summarizes the example configuration. 

| User physical location | User makes a call to a number | Voice Routing Policy | Mode configured for SBC | Media Flow | 
|:------------|:-------|:-------|:-------|:-------|
| Vietnam | +84 4 3926 3000 | Priority 1: ^\+84(\d{9})$ -VNsbc.contoso.com <br>Priority 2: .* - proxysbc.contoso.com | VNsbc.contoso.com – Only For Local Users <br> proxysbc.contoso.com – Always Bypass | Teams User <–> VNsbc.contoso.com |


In the following diagram, a user assigned to local branch office in Vietnam, while on premises, makes a Direct Routing based phone call via Teams. User’s Teams client communicates with Microsoft Phone System directly via REST API and media generated during the call flows to local SBC’s internal IP address. Local SBC redirects the flow to proxy SBC in Singapore and connected local PSTN network. Proxy SBC is visible to Microsoft Phone System via external IP address only and routes the flow from downstream SBC (in this case local SBC in Vietnam) to Microsoft Phone System. Downstream SBC in local branch office is not visible to Microsoft Phone System directly but is mapped within the virtual network topology.

INSERT DIAGRAM HERE


**Case two. User and gateways are in different sites**

SBC in Singapore is configured to be a proxy SBC for local downstream SBCs in Vietnam and Indonesia. Internal user in Indonesia located in local branch office is making a Direct Routing call to Vietnam. Voice routing policies specify that in case of Vietnamese calls (with area code +84) they should be routed to local Vietnamese SBC. All other calls and, in case Vietnamese SBC fails, Vietnamese calls should be routed to proxy SBC in Singapore. Proxy SBC in Singapore is set to ‘Always Byass’ mode and local SBC in Vietnam is set to ‘Only For Local Users’ mode. Table below summarizes the example configuration. 

| User physical location | User makes a call to a number | Voice Routing Policy | Mode configured for SBC | Media Flow | 
|:------------|:-------|:-------|:-------|:-------|
| Indonesia | +84 4 3926 3000 | Priority 1: ^\+84(\d{9})$ -VNsbc.contoso.com <br> Priority 2: .* - proxysbc.contoso.com |VNsbc.contoso.com – Only For Local Users <br> proxysbc.contoso.com – Always Bypass | Teams User <–> proxysbc.contoso.com <–> VNsbc.contoso.com |


In the following diagram, internal user, while on premises in Indonesian branch office, makes a Direct Routing based phone call via Teams to Vietnamese number. User’s Teams client communicates with Microsoft Phone System directly via REST API and media generated during the call flows to proxy SBC’s internal IP address first. Proxy SBC in Singapore redirects the flow to internal IP address of the downstream SBC in Vietnam and to Microsoft Phone System. Downstream SBC in Vietnam routes the flow to connected local PSTN network. Proxy SBC is visible to Microsoft Phone System via external IP address only. Downstream SBCs in local branch offices are not visible to Microsoft Phone System directly but are mapped within the virtual network topology.

INSERT DIAGRAM HERE




