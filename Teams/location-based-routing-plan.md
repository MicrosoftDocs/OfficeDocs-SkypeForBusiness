---
title: Plan Location-Based Routing for Direct Routing
author: LanaChin
ms.author: v-lanac
manager: serdars
ms.date: 2/1/2019
ms.topic: conceptual
ms.service: msteams
ms.reviewer: roykuntz
search.appverid: MET150
description: Learn how to plan Location-Based Routing for Direct Routing.
localization_priority: Normal
ms.collection:  
- Teams_ITAdmin_Help
- M365-collaboration
- M365-voice
appliesto: 
- Microsoft Teams
---

# Plan Location-Based Routing for Direct Routing

> [!INCLUDE [Preview customer token](includes/preview-feature.md)]

## Overview of Location-Based Routing

In some countries and regions, it's illegal to bypass the Public Switched Telephone Network (PSTN) provider to decrease long-distance calling costs. This article describes how to use Location-Based Routing to restrict toll bypass for Microsoft Teams users based on their geographic location. This article applies only to Phone System Direct Routing.

Here you'll get an overview of Location-Based Routing and guidance to help you plan for it. When you're ready to apply and enable Location-Based Routing, see:
- [Deploy network settings for Location-Based Routing](location-based-routing-configure-network-settings.md)
- [Enable Location-Based Routing for Direct Routing](location-based-routing-enable.md)

Location-Based Routing is a feature that lets you restrict toll bypass based on policy and the user's geographic location at the time of an inbound or outbound PSTN call. 

When a Teams user is enabled for Location-Based Routing, the following applies:
- To make an outbound PSTN call, one of the following must be true:
    - The user's endpoint is located in a network site that's enabled for Location-Based Routing and calls egress through the corresponding gateway that's enabled for Location-Based Routing. 
    - The user's endpoint is located in a network site that's not enabled for Location-Based Routing and calls egress through a gateway that's not enabled for Location-Based Routing.

    Outbound calls aren't allowed in any other scenario.

- To receive an inbound PSTN call, the user's answering endpoint must be located in the same network site where the call ingresses through the gateway that's enabled for Location-Based Routing. In any other scenario, such as if the user is roaming, the call isn't allowed and is routed to the user's call forwarding settings (typically voicemail).
- To transfer a PSTN call to another Teams user, the target user's endpoint must be located in the same network site as the user who initiates the transfer. Transfers aren't allowed in any other scenario. 
- To transfer another Teams user to the PSTN, the call must be transferred through a Location-Based Routing enabled gateway located at the same network site as the initial caller. Transfers aren't allowed in any other scenario.

Location-Based Routing uses the same network region, site, and subnet definitions that Skype for Business Server uses. When toll bypass is restricted for a location, an admin associates each IP subnet and each PSTN gateway for that location to a network site. A user’s location is determined by the IP subnet that the user’s Teams endpoints are connected to at the time of a PSTN call. A user may have multiple Teams clients located at different sites, in which case Location-Based Routing enforces each client’s routing separately depending on the location of its endpoint. 

To get familiar with some of the network terminology used in this article, see [Location-Based Routing terminology](location-based-routing-terminology.md).

## Apply Location-Based Routing

You must apply Location-Based Routing to users, network sites, and PSTN gateways.  

### Apply Location-Based Routing at the user location

As mentioned earlier, Location-Based Routing only applies to users who are set up for Direct Routing. Location-Based Routing doesn't apply to users who are set up for Calling Plan. Users must be enabled for Location-Based Routing if they are under toll bypass restriction, which controls the conditions in which they can make and receive PSTN calls and the PSTN gateway that can be used. When a user who is enabled for Location-Based Routing is located at a site that's enabled for Location-Based Routing, the user must make calls through a Location-Based Routing enabled gateway connected to the site. 

Location-Based Routing works by determining the user’s current location based on the IP address of the user’s Teams endpoint and applies the rules accordingly. The location of a user who is enabled for Location-Based Routing can be categorized in the following ways: 
- **The user is located at the same Location-Based Routing enabled site associated to the PSTN gateway where their DID is assigned.**<br>In this scenario, the user is located in a known network site that's enabled for Location-Based Routing and the user's Direct Inward Dial (DID) number terminates on a PSTN gateway that's in the same network site. For example, the user is at their office. 
- **The user is located at a different Location-Based Routing enabled site not associated to PSTN gateway where their DID is assigned.**<br>In this scenario, the user is located in a known network site that’s enabled for Location-Based Routing, and that site isn't associated with the PSTN gateway where the user’s DID number is assigned. For example, the user travels to another office.  
- **The user is located at an internal site that's not enabled for Location-Based Routing.** <br>In this scenario, the user is located in a known internal network site that's not enabled for Location-Based Routing. 
- **The user is located at an unknown site.** 
    - The user is located within the internal network that's not defined as a network site. 
    - The user is located outside the internal network. For example, the user is on the Internet at home or in a coffee shop. 

### Apply Location-Based Routing at the network site 
Network sites must be enabled for Location-Based Routing to help determine which gateways to route Location-Based Routing enabled users when roaming. If a user who is enabled for Location-Based Routing roams to an site that's enabled for Location-Based Routing, only the PSTN gateway that's enabled for Location-Based Routing at that site can be used for outbound calls. If a user who is enabled for Location-Based Routing roams to a site that's not enabled for Location-Based Routing, any gateway that's not enabled for Location-Based Routing can be used for outbound calls.  

### Apply Location-Based Routing at the PSTN gateway 

Gateways are associated to sites to determine where a user who is enabled for Location-Based Routing can be located when they make or receive a PSTN call. Gateways must be enabled for Location-Based Routing to ensure that it's under toll bypass restrictions and can’t be used by users who aren't enabled for Location-Based Routing. The same gateway may be associated to multiple sites and it can be configured to be enabled for Location-Based Routing or not enabled for Location-Based Routing, depending on the site. 

## Scenarios for Location-Based Routing

This section describes different scenarios for restricting toll bypass by using Location-Based Routing and compares how calls are routed for users who aren't enabled for Location-Based Routing with users who are enabled for Location-Based Routing.

- [Teams user places an outbound call to the PSTN](#teams-user-places-an-outbound-call-to-the-pstn)
- [Teams user receives an inbound call from the PSTN](#teams-user-receives-an-inbound-call-from-the-pstn)
- [Teams user transfers or forwards call to another Teams user](#teams-user-transfers-or-forwards-call-to-another-teams-user)
- [Teams user transfers or forwards call to PSTN endpoint](#teams-user-transfers-or-forwards-call-to-pstn-endpoint)
- [Simultaneous ringing](#simultaneous-ringing)
- [Delegation](#delegation)

The following diagram shows the restrictions enabled by Location-Based Routing in each scenario. Users, network sites, and gateways that are enabled for Location-Based Routing have a border around them. Use the diagram as a guide to help you understand how Location-Based Routing works in each scenario.  

![Diagram showing scenarios for Location-Based Routing](media/lbr-direct-routing.png "Diagram showing scenarios for Location-Based Routing")

### Teams user places an outbound call to the PSTN

#### User not enabled for Location-Based Routing

A user who isn't enabled for Location-Based Routing can make outbound calls using any gateway at any site that’s not enabled for Location-Based Routing through their assigned voice routing policy. However, if a gateway is enabled for Location-Based Routing, the user can't make outbound calls through the gateway even if it’s assigned to their voice routing policy. If the user roams to a site that's enabled for Location-Based Routing, they can only make calls through their normal routing gateways that aren't enabled for Location-Based Routing.
 
#### User enabled for Location-Based Routing
In comparison, the routing of outbound calls for users who are enabled for Location-Based Routing is affected by the network location of the user’s endpoint. The following table shows how Location-Based Routing affects the routing of outbound calls of User1, depending on the location of User1. 

|User1 endpoint location  |Routing of outbound calls for User1  |
|---------|---------|
|Same site where user's DID is assigned, site enabled for Location-Based Routing (Site1)      |Call routed through gateway that's enabled for Location-Based Routing (GW1) at Site1, based on the user’s voice routing policy         |
|Different site than where user's DID is assigned, site enabled for Location-Based Routing (Site2)    |Call routed through gateway that's enabled for Location-Based Routing (GW2) at roam Site2, based on user's voice routing policy        |
|Different site than where user's DID is assigned, site not enabled for Location-Based Routing (Site3)  |Call routed through gateway that's not enabled for Location-Based Routing at site that's not enabled for Location-Based Routing (GW3), based on user's voice routing policy       |
|Unknown internal network (Location4)    |  PSTN calling not allowed       |
|Unknown external network (Location5)    | PSTN calling not allowed        |

### Teams user receives an inbound call from the PSTN

#### User not enabled for Location-Based Routing

A user who isn't enabled for Location-Based Routing can receive an inbound call from the gateway that's not enabled for Location-Based Routing from which their assigned DID number ingresses. If the user roams to a site that's not enabled for Location-Based Routing, they can still receive calls through their normal PSTN gateways.
  
#### User enabled for Location-Based Routing

In comparison, users enabled for Location-Based Routing can only receive inbound calls from the PSTN gateway their DID is assigned to when they are located at the same site. The following table shows how User1 receives inbound calls when User1 moves to different network locations. If the call isn't routed to the endpoint of the user, it goes to the user’s call forwarding settings, if the settings are configured. Typically, this is voicemail.  

|User1 endpoint location  |Routing of inbound calls to User1  |
|---------|---------|
|Same site as where user's DID is assigned, site enabled for Location-Based Routing (Site1)   | Calls routed to User1's endpoint in Site1        |
|Different site than where user's DID is assigned, site enabled for Location-Based Routing (Site2)    | Calls not routed to endpoints in Site2        |
|Different site than where user's DID is assigned, site not enabled for Location-Based Routing (Site3)    | Calls not routed to endpoints in Site3        |
|Unknown internal network (Location4)   | Calls not routed to endpoints in Location4        |
|Unknown external network (Location5)     | Calls not routed to endpoints in Location5        |

### Teams user transfers or forwards call to another Teams user

When a PSTN endpoint is involved, Location-Based Routing analyzes whether one or both users are enabled for Location-Based Routing and determines whether the call should be transferred or forwarded depending on the location of both endpoints. 
 
Call transfer requires the initiating user to pick up the call while call forwarding doesn't require the initial call to be answered. This means that calls can be forwarded even if User1 isn't at a location to receive inbound calls (see the table in the [Teams user receives an inbound call from the PSTN](#teams-user-receives-an-inbound-call-from-the-pstn) section) and calls can't be transferred if User1 is unable to receive the inbound call. 

#### User not enabled for Location-Based Routing

A user who isn't enabled for Location-Based Routing can transfer or forward PSTN calls to other users who aren't enabled for Location-Based Routing. The user will typically not be allowed to transfer or forward a PSTN call to a user who is enabled for Location-Based Routing because Location-Based Routing enabled users are generally only allowed to be co-located at Location-Based Routing enabled gateways for PSTN calls. The exception is when a Location-Based Routing enabled user roams to a site that's not enabled for Location-Based Routing. In this scenario, the transferred call is allowed.  

Likewise, a user who isn't enabled for Location-Based Routing can only receive a transfer or forwarded PSTN call from another user who isn't enabled for Location-Based Routing. 

#### User enabled for Location-Based Routing

Generally, transferring and forwarding inbound PSTN calls from a gateway that's enabled for Location-Based Routing is allowed only if the target user is enabled for Location-Based Routing and is located at the same site. Otherwise, transferring and forwarding calls isn't allowed. 

The following table shows whether call forwarding and call transfers are allowed, depending on the location of the target user. In this table, User1, located in Site1, initiates the transfer or forward to other Teams users who are also enabled for Location-Based Routing and who are in different locations.  

|Target user endpoint location|User1 initiates call transfer |User1 initiates call forward|
|---------|---------|---------|
|Same network site as initiator (User2)|Allowed|Allowed|
|Different network site, site enabled for Location-Based Routing (User3)|Not allowed|Not allowed|
|Different network site, site not enabled for Location-Based Routing (User4)|Not allowed|Not allowed|
|Unknown internal network (User5)| Not allowed|Not allowed|
|Unknown external network (User6)| Not allowed|Not allowed|

### Teams user transfers or forwards call to PSTN endpoint

#### User not enabled for Location-Based Routing

- Transferring and forwarding a PSTN call to another PSTN number is allowed. 
- Transferring and forwarding an inbound VOIP call to the PSTN must honor the caller’s toll bypass restrictions. 
    - If the caller isn't enabled for Location-Based Routing, they can be transferred to any PSTN gateway that's not enabled for Location-Based Routing.
    - If the caller is enabled for Location-Based Routing, they can only be transferred to a Location-Based Routing enabled gateway located at the same network site. 

#### User enabled for Location-Based Routing

- Transferring and forwarding inbound a PSTN call to another PSTN number must be routed out the same Location-Based Routing enabled gateway that the inbound call arrived on. 
- Transferring and forwarding an inbound VOIP call to the PSTN must honor both the caller and called user’s toll bypass restrictions. 
    - If the caller isn't enabled for Location-Based Routing, they can be transferred to any PSTN gateway that's not enabled for Location-Based Routing.
    - If the caller is enabled for Location-Based Routing, they can be only be transferred to a Location-Based Routing enabled gateway located at the same network site.
 
The following table shows how Location-Based Routing affects routing of a VOIP call from User1 at Site1 to users in different locations who transfer or forward the call to a PSTN endpoint.  

|User initiating call transfer or forward  |Transfer to PSTN  |Forward to PSTN  |
|---------|---------|---------|
|Same network site, site enabled for Location-Based Routing (User2)   |Call transfer can only be routed through Location-Based Routing enabled Gateway1 at Site1, based on User2's voice routing policy         |Call forward can only routed through Location-Based Routing enabled Gateway1 at Site1, based on User2's voice routing policy         |
|Different network site, site enabled for Location-Based Routing (User3)    |Call transfer can only be routed through Location-Based Routing enabled Gateway1 at Site1, based on User3's voice routing policy         |Call forward can only be routed through Location-Based Routing enabled Gateway1 at Site1, based on User3's voice routing policy         |
|Different network site, site not enabled for Location-Based Routing (User4)    |Call transfer can only be routed through Location-Based Routing enabled Gateway1 at Site1, based on User4's voice routing policy         |Call forward can only be routed through Location-Based Routing enabled Gateway1 at Site1, based on User4's voice routing policy         |
|Unknown internal network (User5)     |Call transfer can only be routed through Location-Based Routing enabled Gateway1 at Site1, based on User5's voice routing policy         |Call forward can only be routed through Location-Based Routing enabled Gateway1 at Site1, based on User5's voice routing policy         |
|Unknown external network (User6)   |Call transfer can only be routed through Location-Based Routing enabled Gateway1 at Site1, based on User6's voice routing policy        |Call forward can only be routed through Location-Based Routing enabled Gateway1 at Site1, based on User6's voice routing policy         |

### Simultaneous ringing

When a user who's enabled for Location-Based Routing receives a call and has simultaneous ringing enabled, Location-Based Routing analyzes the location of the calling party and the endpoints of the called parties to determine whether the call should be routed. Simultaneous ringing follows the same Location-Based rules as call transfers and forwards. 

#### Simultaneous ringing for another Teams user

The following table shows whether Location-Based Routing allows simultaneous ringing to different users for an inbound PSTN call for User1.

|Target user endpoint location|Simultaneous ring  |
|---------|---------|
|Same network site as initiator (User2)   |Allowed         |
|Different roamed network site enabled for Location-Based Routing (User3)   |Not allowed         |
|Roamed network site not enabled for Location-Based Routing (User4)   |Not allowed        |
|Unknown internal network (User5)    | Not allowed        |
|Unknown external network (User6)    |Not allowed        |
|Target user is a PSTN number    |Call can only be routed through Location-Based Routing enabled Gateway1 at Site1, based on User1's voice routing policy      |

#### Simultaneous ringing to a PSTN endpoint

The following table shows Location-Based Routing behavior for an inbound VOIP call from User1 located at Site1 to users in different locations with simultaneous ring set to a PSTN number. 

|Called user endpoint location  |Simultaneous ring target is PSTN endpoint |
|---------|---------|
|Same network site, site enabled for Location-Based Routing (User2)    |Call can be only be routed through Location-Based Routing Gateway1 at Site1, based on User2's voice routing policy       |
|Different network site enabled for Location-Based Routing (User3)    |Call can only be routed through Location-Based Routing Gateway1 at Site1, based on User3's voice routing policy        |
|Different network site not enabled for Location-Based Routing (User4)    |Call can only be routed through Location-Based Routing Gateway1 at Site1, based on User4's voice routing policy         |
|Unknown internal network (User5)    |Call can only be routed through Location-Based Routing Gateway1 at Site1, based on User5's voice routing policy         |
|Unknown external network (User6)   |Call can only be routed through Location-Based Routing Gateway1 at Site1, based on User6's voice routing policy         |

#### Inbound calls through voice app (Auto Attendant or Call Queue)

Inbound PSTN calls from a Location-Based Routing enabled gateway are allowed to connect to an auto attendant or call queue. Users enabled for Location-Based Routing can only receive inbound call transfers from these applications when they are located at the same site the inbound PSTN call originates from. 
 
Call forwarding and simultaneous ringing to users and PSTN is allowed for voice app transfers. Completing the call to the target is subject to the same Location-Based Routing rules listed earlier.  
 
Forwarding to voicemail is also allowed.  

### Delegation

A Teams user may choose delegates who can make and receive calls on their behalf. Delegation capabilities in Teams are affected by Location-Based Routing as follows: 
- For outbound calls from a Location-Based Routing enabled delegate on behalf of a delegator, the same rules apply. Call routing is based on the delegate’s call authorization policy, voice routing policy, and location. For more information, see [Teams user places an outbound call to the PSTN](#teams-user-places-an-outbound-call-to-the-pstn). 
- For inbound PSTN calls to a delegator, the same Location-Based Routing rules that apply for call forwarding or simultaneously ringing to other users also apply to delegates. For more information, see [Teams user transfers or forwards call to another Teams user](#teams-user-transfers-or-forwards-call-to-another-teams-user), [Teams user transfers or forwards call to PSTN endpoint](#teams-user-transfers-or-forwards-call-to-pstn-endpoint), and [Simultaneous ringing](#simultaneous-ringing). 
When a delegate sets a PSTN endpoint as a simultaneous ring target, the voice routing policy of the delegate is used to route the call to the PSTN. 
- For delegation, it's recommended that the delegator and associated delegates be located in the same network site. 

## Other planning considerations

### Changes from an on-premises Location-Based Routing deployment

Network site voice routing policy is no longer used. Instead, we use the user’s voice routing policy. This means that to allow users to roam to other sites, the voice routing policy must include the gateways of the roamed sites. 

### Technical considerations for Location-Based Routing

IPv4 and IPv6 subnets are supported, however, IPv6 takes precedence when checking for a match.

### Client support for Location-Based Routing

The following Teams clients are supported:
- Teams desktop clients (Windows and Mac)
- Teams mobile clients (iOS and Android)
- Teams IP phones

The Teams web client and Skype for Business clients aren't supported.

### Capabilities not supported by Location-Based Routing

Location-Based Routing doesn't apply to the following types of interactions. Location-Based Routing isn't enforced when Teams endpoints interact with PSTN endpoints in the following scenarios: 
- Call park or retrieval of PSTN calls through Call Park 
- An on-premises Skype for Business user or a Skype for Business Online user calls a Teams user  

### Location-Based Routing for conferencing

A Location-Based Routing enabled user on a PSTN call isn't allowed to start a conference with another user or PSTN number. Connecting to auto attendants or call queues is allowed. 
If the user has a conferencing license, the user must start a conference with the relevant users and call the PSTN through the conference bridge to start a conference call.  

## Next steps
Go to [Configure network settings for Location-Based Routing](location-based-routing-configure-network-settings.md).

### Related topics
- [Enable Location-Based Routing for Direct Routing](location-based-routing-enable.md)
- [Location-Based Routing terminology](location-based-routing-terminology.md)
