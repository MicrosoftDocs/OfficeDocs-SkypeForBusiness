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

# Configure Local Media Optimization for Direct Routing

Configuration for Local Media Optimization is based on network settings that are common to other cloud voice features, such as Location-Based Routing and dynamic emergency calling. To learn more about network regions, network sites, network subnets, and trusted IP addresses, see [Network settings for cloud voice features](cloud-voice-network-settings.md).

To configure Media Path Optimization, the following steps are required. You can use the Teams Admin Center or PowerShell. For details, see [Manage your network topology](manage-your-network-topology.md).

1. Configure the user and the SBC sites
2. Configure the SBCs for Local Media Optimization according to your SBC vendor specification


## Configure the user and the SBC sites

To configure the user and the SBC sites, you will need to:

1. [Manage external trusted IP addresses](#manage-external-trusted-ip-addresses)  

   External trusted IPs are the Internet external IPs of the enterprise network and are used to determine if the user's endpoint is inside the corporate network before checking for a specific site match. These need to be added for each site.

2. [Define the network regions, network sites, and subnets](#define-network-regions,-sites,-and-subnets).

3. [Define the virtual network topology](#define-virtual-network-topology) by assigning SBC(s) to site(s) with relevant modes and proxy SBC values.


## Configure SBC(s) for Local Media Optimization according to the SBC vendor specification

This article describes configuration from the Microsoft side. For information on SBC configuration, see your SBC vendor documenation.
.
Media Path Optimization is supported by following SBC manufacturers:

INSERT TABLE - prior to publishing with SBC vendors and links to configuration spec

Diagram 1. The network setup used in the examples throughout this article:

![Diagram showing network setup for examples](media/direct-routing-media-op-9.png "Network setup for examples")


Note: All parameters are case sensitive. Make sure same casing is used during setup.


## Manage external trusted IP addresses

To add public IP addresses of each local branch office, use the New-CsTenantTrustedIPAddress cmdlet . This is the IP address used to connect each local branch office to Microsoft Phone System. Trusted IPs are the Internet external IPs of the enterprise network and are used to determine if the user's endpoint is inside the corporate network before checking for a specific site match. You can define an unlimited number of trusted IP addresses for a tenant. Both IPv4 and IPv6 addresses need to be defined separately.

```
New-CsTenantTrustedIPAddress -IPAddress <External IP address> -MaskBits <Subnet bitmask> -Description <description>
```


Example of adding trusted IP addresses.

```
New-CsTenantTrustedIPAddress -IPAddress 172.16.240.110 -MaskBits 24 -Description "Vietnam site trusted IP"
New-CsTenantTrustedIPAddress -IPAddress 172.16.240.120 -MaskBits 24 -Description "Indonesia site trusted IP"
New-CsTenantTrustedIPAddress -IPAddress 172.16.240.130 -MaskBits 24 -Description "Singapore site trusted IP"
```


## Define network regions, sites, and subnets

### Define network regions

To define network regions, use the New-CsTenantNetworkRegion cmdlet. Note that the RegionID parameter is a logical name that represents the geography of the region and has no dependencies or restrictions. The CentralSite <site ID> parameter is optional.

```
New-CsTenantNetworkRegion -NetworkRegionID <region ID>  
```

The following example creates a network region named APAC:

```
New-CsTenantNetworkRegion -NetworkRegionID "APAC"  
```

###  Define network sites

To define network sites, use the New-CsTenantNetworkSite cmdlet. Each network site must be associated with a network region.

```
New-CsTenantNetworkSite -NetworkSiteID <site ID> -NetworkRegionID <region ID>
```

The following example creates three new network sites, Vietnam, Indonesia and Singapore in the APAC region:

```
New-CsTenantNetworkSite -NetworkSiteID "Vietnam" -NetworkRegionID "APAC"
New-CsTenantNetworkSite -NetworkSiteID "Indonesia" -NetworkRegionID "APAC"
New-CsTenantNetworkSite -NetworkSiteID "Singapore" -NetworkRegionID "APAC"
```

### Define network subnets

To define network subnets and associate them to network sites, use the New-CsTenantNetworkSubnet cmdlet. Each network subnet can only be associated with one site. 

```
New-CsTenantNetworkSubnet -SubnetID <Subnet IP address> -MaskBits <Subnet bitmask> -NetworkSiteID <site ID>
```

The following example defines three network subnets and associates them with the three network sites:  Vietnam, Indonesia, and Singapore:

```
New-CsTenantNetworkSubnet -SubnetID 192.168.1.0 -MaskBits 24 -NetworkSiteID “Vietnam”
New-CsTenantNetworkSubnet -SubnetID 192.168.2.0 -MaskBits 24 -NetworkSiteID “Indonesia”
New-CsTenantNetworkSubnet -SubnetID 192.168.3.0 -MaskBits 24 -NetworkSiteID “Singapore”
```

## Define the virtual network topology 

The tenant administrator defines the virtual network topology by specifying the network sites for the PSTN gateway objects using the Set-CsOnlinePSTNGateway command:

```
PS C:\> Set-CsOnlinePSTNGateway -Identity <Identity> -GatewaySiteID <site ID> -MediaBypass <true/false> -BypassMode <Always/OnlyForLocalUsers> -ProxySBC  <proxy SBC FQDN or $null>
```

Note the following: 
   - If the customer has a single SBC, the -ProxySBC parameter must be either mandatory $null or SBC FQDN value (Central SBC with centralized trunks scenario).
   - The -MediaBypass parameter must be set to $true in order to support Local Media Optimization.
   - If the SBC doesn’t have the -BypassMode parameter set, X-MS headers will not be sent. 
   - All parameters are case sensitive so you need to ensure that you use the same case that was used used during setup.  (For example, GatewaySiteID values “Vietnam” and “vietnam” will be treated as different sites.)

The following example adds three SBCs to network sites Vietnam, Indonesia, and Singapore in the APAC region with mode Always bypass:

```
Set-CSOnlinePSTNGateway -Identity “proxysbc.contoso.com” -GatewaySiteID “Singapore” -MediaBypass $true -BypassMode “Always” -ProxySBC $null

Set-CSOnlinePSTNGateway -Identity “VMsbc.contoso.com” -GatewaySiteID “Vietnam” -MediaBypass $true -BypassMode “Always” -ProxySBC “proxysbc.contoso.com”

Set-CSOnlinePSTNGateway -Identity “IDsbc.contoso.com” -GatewaySiteID “Indonesia” -MediaBypass $true -BypassMode “Always” -ProxySBC “proxysbc.contoso.com”
```

Based on the information above, Direct Routing will include three proprietary SIP Headers to SIP Invites and Re-invites as shown shown in the following table:

Table 1. X-MS Headers introduced in Direct Routing on Invites and Re-Invites if BypassMode defined

| Header name | Values | Comments | 
|:------------|:-------|:-------|
| X-MS-UserLocation | internal/external | Indicates if user is internal or external |
| Request-URI	INVITE sip: +84439263000@VMsbc.contoso.com SIP /2.0 | SBC FQDN | The FQDN which is targeted for the call even if the SBC is not directly connected to Direct Routing |
| X-MS-MediaPath | Example: proxysbc.contoso.com, VMsbc.contoso.com | Order of SBCs that should be used for Media path between the user and target SBC. The final SBC is always last |
| X-MS-UserSite | usersiteID | String defined by tenant administrator |


## Call flows 

The following shows call flows for two modes:

- Mode 1:  Always bypass
- Mode 2:  Only for local users

### Mode 1: Always Bypass

Always Bypass mode is the simplest option to configure.  The tenant administrator can configure a single site for all users and SBCs if all SBCs can be reachable from any site.

Examples show Always bypass mode for the following:

- Outbound calls when the user is in the same location as the SBC
- Inbound calls when the user is in the same location as the SBC
- Outbound call when the user is external
- Incoming call when the user is external

Table 2. Example FQDN and IP addresses 

| FQDN | External IP address | Internal IP Address | Internal subnet | Location | External NAT for Internet egress |
|:------------|:-------|:-------|:-------|:-------|:-------|
| VNsbc.contoso.com | None | 192.168.1.5 | 192.168.1.0/24 | Vietnam | 172.16.240.110 |
| IDsbc.contoso.com | None | 192.168.2.5 | 192.168.2.0/24 | Indonesia | 172.16.240.120 |
| proxysbc.contoso.com | 172.16.240.133 | 192.168.3.5 | 192.168.3.0/24 | Singapore | 172.16.240.130 |



#### Outbound calls when the user is in the same location as the SBC

Table 3. For outbound calls; AlwaysBypass mode. User in the same location as the SBC

| Mode |	User |	Location |	Call direction |
|:------------|:-------|:-------| :-------|
| AlwaysBypass |	Internal |	The same site as SBC |	Outbound |



Table 4.  End user configuration and action

| User physical location| User makes or receives a call to/from number | User phone number	| Voice Routing Policy | Mode configured for SBC |
|:------------|:-------|:-------|:-------|:-------|
| Vietnam |	+84 4 3926 3000	| +84 4 5555 5555	| Priority 1: ^\+84(\d{9})$ -VMsbc.contoso.com <br> Priority 2: .* - proxysbc.contoso.com	| VMsbc.contoso.com – Always Bypass <br> proxysbc.contoso.com – Always Bypass


Diagram 2 shows the SIP ladder for an outbound call; Always bypass mode; with user in the same location as the SBC.

![Diagram showing outbound calls](media/direct-routing-media-op-10.png "Outbound calls")

Table 5 shows the X-MS headers sent by Direct Routing:

| Parameter	| Explanation |
|:------------|:-------|
| Invite +8443926300@VMsbc.contoso.com | The target name of the SBC as defined in voice routing policy is send in the Request URI | X-MS-UserLocation: internal |	The field indicated that user is located inside the corporate network |
X-MS-MediaPath: VMsbc.contoso.com |	Specifies which SBC the client must traverse to the target SBC. In this case as we have Always Bypass, and the client is internal the target name sent as the only name in the header. | 
X-MS-UserSite: Vietnam | 	The field indicated within the site the user is located. |


#### For inbound calls when the user is in the same location as the SBC

 Incoming call. User in the same location as the SBC

Table 6.  

| Mode | 	User | 	Location | 	Call direction |
|:------------|:-------|:-------|:-------|:-------|
| AlwaysBypass |	Internal | The same site as SBC |Incoming |


On an incoming call, the location of the user is unknown, and the SBC must guess where the user is. If the guess is not correct, a re-invite will be required. This case assumes user is internal, media can flow directly, and no further actions are required (re-invite).
The SBC paired to Direct Routing service reports originating SBC location by providing Record-Route and Contact fields. Based on these fields the media path is calculated by Direct Routing.

Note: Given that a user can have multiple endpoints support of 183 is not possible. The Direct Routing will always use 180 Ringing in this case. 

Diagram 3 shows the SIP Ladder. Mode AlwaysBypass. Incoming call. User in the same location as the SBC.

![Diagram showing SIP ladder](media/direct-routing-media-op-11.png)


#### Outbound calls and user is external

Teble 7...


| Mode |	User |	Site |	Call direction
|:------------|:-------|:-------|:-------|
AlwaysBypass |	External |	N/A | 	Outgoing |


Diagram 4 shows the SIP ladder; Case AlwaysBypass; Outgoing call and user is external.

![Diagram showing SIP ladder](media/direct-routing-media-op-12.png)



The Direct Routing sends the following information:

Table 8. X-MS headers send by Direct Routing 


| Parameter |	Explanation |
|:------------|:-------|
Invite +8443926300@VMsbc.contoso.com | The target name of the SBC as defined in voice routing policy is send in the Request URI.| X-MS-UserLocation: external |	The field indicated that user is located outside the corporate network. |
X-MS-MediaPath: proxysbc.contoso.com, VMsbc.contoso.com	 | Specifies which SBC the client must traverse to the target SBC. In this case as we have Always Bypass, and the client is external. |

#### Inbound calls and user is external

Table 9

| Mode | User | Site |	Call direction |
|:------------|:-------|:-------|:-------|
AlwaysBypass |	External |	N/A |	Incoming |

For an incoming call, the SBC connected to Direct Routing needs to send a re-invite (by default local media candidates always offered) if location of the user is external.
X-MediaPath calculated based on Record-Route and the SBC user specified.

Diagram 5 shows the SIP Ladder; AlwaysBypass mode; incoming call; and user is external.

![Diagram showing SIP ladder](media/direct-routing-media-op-13.png)



### Mode 2: Only for local users

Local media candidates of the target SBC will be offered only if a user is in the same location as the SBC. In all other cases media will flow via either internal or external IP of the proxy SBC
Table 10 . End user configuration and action

Table 10

| User physical location |	User makes or receives a call to/from number |	User phone number |	Voice Routing Policy |	Mode configured for SBC |
|:------------|:-------|:-------|:-------|:-------|
| Vietnam | +84 4 3926  3000 |	+84 4 5555 5555 | Priority 1: ^\+84(\d{9})$ -VMsbc.contoso.com <br> Priority 2: .* - proxysbc.contoso.com | VMsbc.contoso.com – OnlyForLocalUsers Proxysbc.contoso.com – Always Bypass |



#### Outgoing call and user is in the same location as the SBC

Table 11

| Mode | User | Site | Call direction |
|:------------|:-------|:-------|:-------|
| OnlyForLocalUsers |	Internal |Same as SBC	| Outgoing



Diagram 6 shows OnlyForLocalUsers mode; outgoing call; and the user is in the same location as the SBC. Same flow as with Mode Always Bypass (Picture 10).

![Diagram showing SIP ladder](media/direct-routing-media-op-14.png)


#### Incoming call and user is in the same location as the SBC

Table 12

| Mode | User | Site | Call direction |
|:------------|:-------|:-------|:-------|
| OnlyForLocalUsers |	Internal | Same as SBC |Incoming |


Diagram 7 shows OnlyForLocalUsers mode; incoming call; and the user is in the same location as the SBC. Same flow as with Mode Always Bypass (Picture 11).

![Diagram showing SIP ladder](media/direct-routing-media-op-15.png)


#### User is not at the same location as the SBC but in corporate network


Mode OnlyForLocalUsers. Outgoing call, internal user but not at the same location as the SBC

| Mode | User | Site |Call direction |
|:------------|:-------|:-------|:-------|
| OnlyForLocalUsers	 | Internal |	Different from SBC | Outgoing |

Direct routing calculates X-MediaPath based on the reported location of the user and mode configured on the SBC.


Diagram 8 shows OnlyForLocalUsers mode; outgoing call; and the internal user is not at the same location as the SBC.

![Diagram showing SIP ladder](media/direct-routing-media-op-16.png)




#### Incoming call. Internal user but not at the same location as the SBC**

| Mode |	User |	Site |	Call direction |
|:------------|:-------|:-------|:-------|
| OnlyForLocalUsers	| Internal |	Different from SBC |	Incoming |

Diagram 9 shows OnlyForLocalUsers mode. Incoming call. Internal user but not at the same location as the SBC

![Diagram showing SIP ladder](media/direct-routing-media-op-17.png)









