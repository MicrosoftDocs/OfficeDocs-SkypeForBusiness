---
title: Scenarios for Location-Based Routing for Direct Routing 
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.topic: conceptual
ms.service: msteams
audience: admin
ms.reviewer: roykuntz
ms.date: 08/10/2023
search.appverid: MET150
description: Learn how to plan Location-Based Routing for Teams Phone Direct Routing.
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.collection: 
  - M365-voice
  - Tier1
appliesto: 
  - Microsoft Teams
---

# Scenarios for Location-Based Routing for Direct Routing

Before reading this article, be sure you have read [Plan for Location-Based Routing](location-based-routing-plan.md).

This article describes different scenarios for restricting toll bypass by using Location-Based Routing. The scenarios compare how calls are routed for users who are and are not enabled for Location-Based Routing.

- [Teams user places an outbound call to the PSTN](#teams-user-places-an-outbound-call-to-the-pstn)
- [Teams user receives an inbound call from the PSTN](#teams-user-receives-an-inbound-call-from-the-pstn)
- [Teams user transfers or forwards call to another Teams user](#teams-user-transfers-or-forwards-call-to-another-teams-user)
- [Teams user transfers or forwards call to PSTN endpoint](#teams-user-transfers-or-forwards-call-to-pstn-endpoint)
- [Simultaneous ringing](#simultaneous-ringing)

The following diagram shows the restrictions enabled by Location-Based Routing in each scenario. Users, network sites, and gateways that are enabled for Location-Based Routing have a border around them. Use the diagram as a guide to help you understand how Location-Based Routing works in each scenario.  

![Diagram showing scenarios for Location-Based Routing.](media/lbr-direct-routing.png "Diagram showing scenarios for Location-Based Routing")

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
|Unknown internal network (Location4)    |  PSTN calling not allowed unless gateway has GatewayLbrEnabledUserOverride set to True       |
|Unknown external network (Location5)    | PSTN calling not allowed unless gateway has GatewayLbrEnabledUserOverride set to True       |

### Teams user receives an inbound call from the PSTN

#### User not enabled for Location-Based Routing

A user who isn't enabled for Location-Based Routing can receive an inbound call from the gateway that's not enabled for Location-Based Routing from which their assigned DID number ingresses. If the user roams to a site that's not enabled for Location-Based Routing, they can still receive calls through their normal PSTN gateways.
  
#### User enabled for Location-Based Routing

In comparison, users enabled for Location-Based Routing can receive inbound calls from the PSTN gateway their DID is assigned to when they are located at the same site, and when they are located in a different site with gateway that’s enabled for Location-Based Routing and GatewayLbrOverride set to True. The following table shows how User1 receives inbound calls when User1 moves to different network locations. If the call isn't routed to the endpoint of the user, it goes to the user’s unanswered call forwarding settings, if the settings are configured. Typically, calls are forwarded to voicemail.  

|User1 endpoint location  |Routing of inbound calls to User1  |
|---------|---------|
|Same site as where user's DID is assigned, site enabled for Location-Based Routing (Site1)   | Calls routed to User1's endpoint in Site1        |
|Different site than where user's DID is assigned, site enabled for Location-Based Routing (Site2)    | Calls not routed to endpoints in Site2        |
|Different site than where user's DID is assigned, site not enabled for Location-Based Routing (Site3)    | Calls not routed to endpoints in Site3        |
|Unknown internal network (Location4)   | Call is not routed unless gateway has GatewayLbrEnabledUserOverride set to True         |
|Unknown external network (Location5)     | Call is not routed unless gateway has GatewayLbrEnabledUserOverride set to True         |

### Teams user transfers or forwards call to another Teams user

When a PSTN endpoint is involved, Location-Based Routing analyzes whether one or both users are enabled for Location-Based Routing and determines whether the call should be transferred or forwarded depending on the location of both endpoints. 
 
Call transfer requires the initiating user to pick up the call while call forwarding doesn't require the initial call to be answered. Calls can be forwarded even if User1 isn't at a location to receive inbound calls (see the table in the [Teams user receives an inbound call from the PSTN](#teams-user-receives-an-inbound-call-from-the-pstn) section) and calls can't be transferred if User1 is unable to receive the inbound call. 

#### User not enabled for Location-Based Routing

A user who isn't enabled for Location-Based Routing can transfer or forward PSTN calls to other users who aren't enabled for Location-Based Routing. Users who are enabled for Location-Based Routing are generally co-located at Location-Based Routing enabled gateways for PSTN calls. Consequently, users who are not enabled are not allowed to transfer or forward a PSTN call to a user who is enabled for Location-Based Routing. The exception is when a Location-Based Routing enabled user roams to a site that's not enabled for Location-Based Routing. In this scenario, the transferred call is allowed.  

Likewise, a user who isn't enabled for Location-Based Routing can only receive a transfer or forwarded PSTN call from another user who isn't enabled for Location-Based Routing. 

#### User enabled for Location-Based Routing

Transferring and forwarding inbound PSTN calls from a gateway that's enabled for Location-Based Routing is allowed only if the target user is enabled for Location-Based Routing and is located at the same site. Otherwise, transferring and forwarding calls isn't allowed. 

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

    - If the caller is enabled for Location-Based Routing, they can be transferred only to a Location-Based Routing enabled gateway located at the same network site.
 
The following table shows how Location-Based Routing affects routing of a VOIP call from Location-Based Routing enabled User1 at Site1 to users in different locations who transfer or forward the call to a PSTN endpoint.  

|User initiating call transfer or forward  |Transfer or forward to PSTN  |
|---------|---------|
|Same network site, site enabled for Location-Based Routing (User2)   |The resulting PSTN call will be permitted only if the calculated route based on User2's voice routing policy results in a route through Location-Based Routing enabled Gateway1 at Site1         |
|Different network site, site enabled for Location-Based Routing (User3)    |The resulting PSTN call will be permitted only if the calculated route based on User3's voice routing policy results in a route through Location-Based Routing enabled Gateway1 at Site1 |
|Different network site, site not enabled for Location-Based Routing (User4)    |The resulting PSTN call will be permitted only if the calculated route based on User4's voice routing policy results in a route through Location-Based Routing enabled Gateway1 at Site1          |
|Unknown internal network (User5)     |The resulting PSTN call will be permitted only if the calculated route based on User5's voice routing policy results in a route through Location-Based Routing enabled Gateway1 at Site1          |
|Unknown external network (User6)   |The resulting PSTN call will be permitted only if the calculated route based on User6's voice routing policy results in a route through Location-Based Routing enabled Gateway1 at Site1          |

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

The following table shows Location-Based Routing behavior for an inbound VoIP call from Location-Based Routing enabled User1 located at Site1 to users in different locations with simultaneous ring set to a PSTN number. 

|Called user endpoint location  |Simultaneous ring target is PSTN endpoint |
|---------|---------|
|Same network site, site enabled for Location-Based Routing (User2)    |The resulting PSTN call will be permitted only if the calculated route based on User2's voice routing policy results in a route through Location-Based Routing enabled Gateway1 at Site1        |
|Different network site enabled for Location-Based Routing (User3)    |The resulting PSTN call will be permitted only if the calculated route based on User3's voice routing policy results in a route through Location-Based Routing enabled Gateway1 at Site1         |
|Different network site not enabled for Location-Based Routing (User4)    |The resulting PSTN call will be permitted only if the calculated route based on User4's voice routing policy results in a route through Location-Based Routing enabled Gateway1 at Site1          |
|Unknown internal network (User5)    |The resulting PSTN call will be permitted only if the calculated route based on User5's voice routing policy results in a route through Location-Based Routing enabled Gateway1 at Site1          |
|Unknown external network (User6)   |The resulting PSTN call will be permitted only if the calculated route based on User6's voice routing policy results in a route through Location-Based Routing enabled Gateway1 at Site1          |


## Related articles

- [Enable Location-Based Routing for Direct Routing](location-based-routing-enable.md)
- [Network settings for cloud voice features in Teams](cloud-voice-network-settings.md)
