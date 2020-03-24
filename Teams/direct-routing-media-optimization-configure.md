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

To configure Media Path Optimization following steps are required (for more details please see Manage your network topology for cloud voice features in Microsoft Teams):

**Configure the user and the SBC sites**

1. Manage external trusted IP addresses 

2. Define network regions, network sites, and subnets 

3. Define virtual network topology by assigning SBC(s) to site(s) with relevant modes and proxy SBC values bu using the following command:

      ```
      Set-CSOnlinePSTNGateway -Identity <Identity> -GatewaySiteID <site ID>  -MediaBypass <true/false> -BypassMode <Always/OnlyForLocalUsers> -ProxySBC <proxy SBC FQDN or $null>
      ```
   Note the following: 
   - If the customer has a single SBC the -ProxySBC parameter must be either mandatory $null or SBC FQDN value (Central SBC with centralized trunks scenario)
   - The -MediaBypass parameter must be set to $true in order to support Media Path Optimization.
   - If the SBC doesn’t have the -BypassMode parameter set, X-MS headers will not be sent. 


**Configure SBC(s) for Media Path Optimization according to SBC vendor configuration specification**


This article describes configuration from the Microsoft side. For information on  SBC configuration, see your SBC vendor documenation
.
Media Path Optimization is supported by following SBC manufacturers:

INSERT TABLE - prior to publishing with SBC vendors and links to configuration spec

Overall view of network setup used in following examples

The following diagram  

INSERT DIAGRAM HERE

Note: For configuration via Microsoft Teams admin center refer to Manage your network topology for cloud voice features in Microsoft Teams page

To configure network settings using PowerShell following steps need to be performed (For more details refer to ‘Configure network settings using PowerShell’ section).

Note: All parameters are case sensitive. Make sure same casing is used during setup.



## Define network regions

Use the New-CsTenantNetworkRegion cmdlet to define network regions. Note that the RegionID parameter is a logical name that represents the geography of the region and has no dependencies or restrictions and the CentralSite <site ID> parameter is optional.

```
New-CsTenantNetworkRegion -NetworkRegionID <region ID>  
```

In this example, we create a network region named APAC.

```
New-CsTenantNetworkRegion -NetworkRegionID "APAC"  
```

## Define network sites

Use the New-CsTenantNetworkSite cmdlet to define network sites. Each network site must be associated with a network region.

```
New-CsTenantNetworkSite -NetworkSiteID <site ID> -NetworkRegionID <region ID>
```

In this example, we create three new network sites, Vietnam, Indonesia and Singapore in the APAC region.

```
New-CsTenantNetworkSite -NetworkSiteID "Vietnam" -NetworkRegionID "APAC"
New-CsTenantNetworkSite -NetworkSiteID "Indonesia" -NetworkRegionID "APAC"
New-CsTenantNetworkSite -NetworkSiteID "Singapore" -NetworkRegionID "APAC"
```

## Define network subnets

Use the New-CsTenantNetworkSubnet cmdlet to define network subnets and associate them to network sites. Each network subnet can only be associated with one site. 

```N
ew-CsTenantNetworkSubnet -SubnetID <Subnet IP address> -MaskBits <Subnet bitmask> -NetworkSiteID <site ID>
```

Example of adding sites from table 1.

```
New-CsTenantNetworkSubnet -SubnetID 192.168.1.0 -MaskBits 24 -NetworkSiteID “Vietnam”
New-CsTenantNetworkSubnet -SubnetID 192.168.2.0 -MaskBits 24 -NetworkSiteID “Indonesia”
New-CsTenantNetworkSubnet -SubnetID 192.168.3.0 -MaskBits 24 -NetworkSiteID “Singapore”
```


## Define external subnets (external trusted IP addresses)#

Use the New-CsTenantTrustedIPAddress cmdlet to define external subnets and assign them to the tenant. You can define an unlimited number of external subnets for a tenant.

```
New-CsTenantTrustedIPAddress -IPAddress <External IP address> -MaskBits <Subnet bitmask> -Description <description>
```

Example of adding trusted IP address from table 1.

```
New-CsTenantTrustedIPAddress -IPAddress 96.66.240.133 -MaskBits 24 -Description "Proxy SBC external address"
```


## Assigning SBCs to the sites

The tenant administrator also specified the Network Sites for PSTN Gateway objects using the following command:

```
PS C:\> Set-CsOnlinePSTNGateway -Identity <Identity> -GatewaySiteID <site ID> -MediaBypass <true/false> -BypassMode <Always/OnlyForLocalUsers> -ProxySBC  <proxy SBC FQDN or $null>
```

Note that all parameters are case sensitive so you need to ensure that you use the same case that was used used during setup.  (For example, GatewaySiteID values “Vietnam” and “vietnam” will be treated as different sites.)

In this example, we add three SBCs to network sites Vietnam, Indonesia and Singapore in the APAC region with mode Always bypass:

```
Set-CSOnlinePSTNGateway -Identity “proxysbc.contoso.com” -GatewaySiteID “Singapore” -MediaBypass $true -BypassMode “Always” -ProxySBC $null

Set-CSOnlinePSTNGateway -Identity “VMsbc.contoso.com” -GatewaySiteID “Vietnam” -MediaBypass $true -BypassMode “Always” -ProxySBC “proxysbc.contoso.com”

Set-CSOnlinePSTNGateway -Identity “IDsbc.contoso.com” -GatewaySiteID “Indonesia” -MediaBypass $true -BypassMode “Always” -ProxySBC “proxysbc.contoso.com”
```

Based on the information above the Direct Routing will include three proprietary SIP Headers to SIP Invites and Re-invites presented in table below.

| Header name | Values | Comments | 
|:------------|:-------|:-------|
| X-MS-UserLocation | internal/external | Indicates if user is internal or external |
| Request-URI	INVITE sip: +84439263000@VMsbc.contoso.com SIP /2.0 | SBC FQDN | The FQDN which is targeted for the call even if the SBC is not directly connected to Direct Routing |
| X-MS-MediaPath | Example: proxysbc.contoso.com, VMsbc.contoso.com | Order of SBCs that should be used for Media path between the user and target SBC. The final SBC is always last |
| X-MS-UserSite | usersiteID | String defined by tenant administrator |


## Call flows 

**Mode 1: Always Bypass**
The simplest option to configure, tenant administrator can even configure single site for all users and SBCs if all SBCs can be reachable from any site.

| FQDN | External IP address | Internal IP Address | Internal subnet | Location | External NAT for Internet egress |
|:------------|:-------|:-------|:-------|:-------|:-------|
| proxysbc.contoso.com | 96.66.240.133 | 192.168.3.5 | 192.168.3.5 | Singapore | 99.66.240.130 |
| VNsbc.contoso.com | None | 192.168.1.5 | 192.168.1.0/24 | Vietnam | 99.66.240.130 |
| IDsbc.contoso.com | None | 192.168.2.5 | 192.168.2.0/24 | Indonesia | 99.66.240.120 |


For outbound calls:


| Mode	User |	Location |	Call direction
|:------------|:-------|:-------|
| AlwaysBypass |	Internal |	The same site as SBC	Outbound |





| User physical location| User makes or receives a call to/from number | User phone number	| Voice Routing Policy | Mode configured for SBC |
|:------------|:-------|:-------|:-------|:-------|
| Vietnam |	+84 4 3926 3000	| +84 4 5555 5555	| Priority 1: ^\+84(\d{9})$ -VMsbc.contoso.com <br> Priority 2: .* - proxysbc.contoso.com	| VMsbc.contoso.com – Always Bypass <br> proxysbc.contoso.com – Always Bypass


**Outbound call diagram**

INSERT DIAGRAM HERE



| Parameter	| Explanation |
|:------------|:-------|
| Invite +8443926300@VMsbc.contoso.com | The target name of the SBC as defined in voice routing policy is send in the Request URI | X-MS-UserLocation: internal |	The field indicated that user is located inside the corporate network |
X-MS-MediaPath: VMsbc.contoso.com |	Specifies which SBC the client must traverse to the target SBC. In this case as we have Always Bypass, and the client is internal the target name sent as the only name in the header. | 
X-MS-UserSite: Vietnam | 	The field indicated within which site the user is located. |


**Mode AlwaysBypass. Incoming call. User in the same location as the SBC**

| Mode | 	User | 	Location | 	Call direction |
|:------------|:-------|:-------|:-------|:-------|
| AlwaysBypass |	Internal | The same site as SBC |Incoming |


On incoming call, the location to the user is unknown. The SBC must guess where the user is. If guess is not correct a re-invite will be required. This case assumes user is internal, media can flow directly, and no further actions required (re-invite).
The SBC paired to Direct Routing service reports originating SBC location by providing Record-Route and Contact fields. Based on these fields the media path is calculated by Direct Routing.

Note: Given that a user can have multiple endpoints support of 183 is not possible. The Direct Routing will always use 180 Ringing in this case. 

Picture 11. SIP Ladder. Mode AlwaysBypass. Incoming call. User in the same location as the SBC 

INSERT DIAGRAM HERE


**Mode AlwaysBypass. Outgoing call and user is external**


| Mode |	User |	Site |	Call direction
|:------------|:-------|:-------|:-------|
AlwaysBypass |	External |	N/A | 	Outgoing |


Picture 12. SIP Ladder. Case AlwaysBypass. Outgoing call and user is external 

INSERT DIAGRAM HERE


The Direct Routing sends the following information:
Table 11. X-MS headers send by Direct Routing 


| Parameter |	Explanation |
|:------------|:-------|
Invite +8443926300@VMsbc.contoso.com | The target name of the SBC as defined in voice routing policy is send in the Request URI.| X-MS-UserLocation: external |	The field indicated that user is located outside the corporate network. |
X-MS-MediaPath: proxysbc.contoso.com, VMsbc.contoso.com	 | Specifies which SBC the client must traverse to the target SBC. In this case as we have Always Bypass, and the client is external. |

**Mode AlwaysBypass. Incoming and user is external**


| Mode 	User | Site |	Call direction |
|:------------|:-------|:-------|:-------|

| Mode 	User | Site |	Call direction |
|:------------|:-------|:-------|:-------|
AlwaysBypass |	External |	N/A |	Incoming |

In incoming call, the SBC paired to Direct Routing needs to send a re-invite (by default local media candidates always offered) if location of the user is external.
X-MediaPath calculated based on Record-Route and the SBC user specified.
Picture 13. SIP Ladder. Mode AlwaysBypass. Incoming call and user is external 

INSERT DIAGRAM HERE


## Mode 2: Only for local users

Local media candidates of the target SBC will be offered only if a user is in the same location as the SBC. In all other cases media will flow via either internal or external IP of the proxy SBC
Table 12. End user configuration and action

| User physical location |	User makes or receives a call to/from number |	User phone number |	Voice Routing Policy |	Mode configured for SBC |
|:------------|:-------|:-------|:-------|:-------|
| Vietnam | +84 4 3926  3000 |	+84 4 5555 5555 | Priority 1: ^\+84(\d{9})$ -VMsbc.contoso.com <br> Priority 2: .* - proxysbc.contoso.com | VMsbc.contoso.com – OnlyForLocalUsers Proxysbc.contoso.com – Always Bypass |



**Mode OnlyForLocalUsers. Outgoing call and user is in the same location as the SBC**


| Mode | User | Site | Call direction |
|:------------|:-------|:-------|:-------|
| OnlyForLocalUsers |	Internal |Same as SBC	| Outgoing



Picture 14: Mode OnlyForLocalUsers. Outgoing call and user is in the same location as the SBC. Same flow as with Mode Always Bypass (Picture 10).

INSERT DIAGRAM HERE


**Mode OnlyForLocalUsers. Incoming call and user is in the same location as the SBC**

| Mode | User | Site | Call direction |
|:------------|:-------|:-------|:-------|
| OnlyForLocalUsers |	Internal | Same as SBC |Incoming |


Picture 15. Mode OnlyForLocalUsers. Incoming call and user is in the same location as the SBC. Same flow as with Mode Always Bypass (Picture 11).

INSERT DIAGRAM here





**Case Two. User is not at the same location as the SBC but in corporate network**


Mode OnlyForLocalUsers. Outgoing call, internal user but not at the same location as the SBC

| Mode | User | Site |Call direction |
|:------------|:-------|:-------|:-------|
| OnlyForLocalUsers	 | Internal |	Different from SBC | Outgoing |

Direct routing calculates X-MediaPath based on the reported location of the user and mode configured on the SBC.
Picture 16. Mode OnlyForLocalUsers. Outgoing call, internal user but not at the same location as the SBC

INSERT DIAGRAM HERE



**Mode OnlyForLocalUsers. Incoming call. Internal user but not at the same location as the SBC**

| Mode |	User |	Site |	Call direction |
|:------------|:-------|:-------|:-------|
| OnlyForLocalUsers	| Internal |	Different from SBC |	Incoming |

Picture 17. Mode OnlyForLocalUsers. Incoming call. Internal user but not at the same location as the SBC

INSERT DIAGRAM HERE








