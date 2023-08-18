---
title: Plan Location-Based Routing for Operator Connect for India
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.topic: conceptual
ms.service: msteams
audience: admin
ms.reviewer: roykuntz
ms.date: 03/15/2023
search.appverid: MET150
description: Learn how to plan and configure Location-Based Routing for Operator Connect for India.
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.collection: 
  - M365-voice
  - Tier1
appliesto: 
  - Microsoft Teams
---

# Plan Location-Based Routing for Operator Connect for India

In India, it's illegal to bypass the Public Switched Telephone Network (PSTN) provider. Because toll bypass is restricted, telecom service providers in India are required to block international calls made or received by customers who are roaming outside of their PSTN connection. 

This article describes what you need to know to use Location-Based Routing with Operator Connect for India. This article applies only to Location Based Routing for Operator Connect for India. (Note that the configuration for Location-Based Routing for Operator Connect for India differs from the configuration for Location-Based Routing for Direct Routing.)

> [!NOTE]
> You shouldn't use Location-Based Routing to dynamically route PSTN calls based on the location of the user. To do so may cause unintended results.

When you're ready to enable Location-Based Routing for Operator Connect for India, see:

- [Configure network settings for Location-Based Routing](location-based-routing-configure-network-settings.md)
- [Enable Location-Based Routing for Operator Connect India](location-based-routing-india-enable.md)


## Overview

Location-Based Routing for Operator Connect for India lets you ensure that Teams users don't violate toll bypass restrictions.

For fixed-line numbers, you must configure Location-Based Routing. The user must be located at a Network Communication Server (NCS) site associated with the number. Transfers are allowed only to other users with the same operator. 

Users are allowed in conferences with the following restrictions: 

**Fixed line (wired)**: All Teams users in the conference must be located at the same network site and with the same operator Teams Phone license when one leg is a PSTN call; users without the same operator Teams Phone license must be restricted.

Signaling and media from Teams clients must traverse the carrier’s data network between the network site and the Microsoft 365 cloud.


## Configure Location-Based Routing for fixed-line calls

Location-Based Routing for India fixed-line calls uses the network topology you define for network region, site, subnet, and public IPs. A **network site** represents a location where your organization has a physical venue, such as an office, a set of buildings or a campus. When toll bypass is restricted for a geographical location, you associate each IP network subnet and each PSTN gateway for that location to a network site. A **network region** is a collection of network sites. Each network site must be associated with a network region. 

India fixed-line phone numbers must be associated with the network site the phone number corresponds to.

**I THINK THE FOLLOWING DIAGRAM STIL APPLIES? TRUE?**

![Diagram showing network topology for Location-Based Routing.](media/lbr-network-topology.png "Diagram showing network topology for Location-Based Routing")

At the time of a PSTN call, a user’s location is determined by the IP subnet that the user’s Teams endpoints are connected to. If a user has multiple Teams clients located at different sites, Location-Based Routing enforces each client’s routing separately depending on the location of the Teams endpoints.

For more information about network settings, see [Network settings for cloud voice features in Teams](cloud-voice-network-settings.md).

Note:  Operator Connect for India doesn't require you to enable users, PSTN gateways, and network sites for Location-Based Routing.


### Toll bypass evaluation and outcome

When Location-Based Routing is used, a call between a Teams user and the PSTN is evaluated to determine if toll bypass is restricted. Depending on the results, the call will or will not complete.   

Toll bypass evaluation depends on whether the Teams user is located at the network site their assigned phone number corresponds to.

If a call can't complete, the Teams user is notified as follows:

**IS THE FOLLOWING TRUE?**

- For outbound PSTN calls, the following message appears in the call window: *Call not allowed due to your organization’s settings.*

- For inbound PSTN calls, the call is routed based on the called Teams user’s unanswered call forwarding settings, typically to voicemail. If the Teams user doesn’t have unanswered call settings configured, the call will disconnect.

## Apply Location-Based Routing

**NEED SPECIFICS ON WHAT DOES/DOESN'T APPLY**

You must apply Location-Based Routing to the [network sites](#apply-location-based-routing-at-the-network-site). The PSTN gateway must be configured with the flag GatewayLbrEnabledUserOverride set to True.

A network site might be in an unknown state - This means a site not configured using tenant network subnets and sites. Typically, such sites are either internal to the corporate network, but by design not configured, or external to the corporate network. In any case, these sites aren't enabled for Location-Based Routing. 


### Apply Location-Based Routing at the user location

Location-Based Routing works by determining the user’s current location based on Teams Endpoint IP and Trusted IP (Public IP) addresses. Conditions are then applied to determine which user can make and receive PSTN calls and the PSTN gateway that can be used. 

The network site at the location of the user will help determine which PSTN gateways to use.  

The location of a user is categorized as follows: 

- **The user is located at the same Location-Based Routing enabled site associated to the PSTN gateway where their DID is assigned. (Office location)**<br>In this scenario, the user is located at a configured network site that's enabled for Location-Based Routing and the user's Direct Inward Dial (DID) number terminates on a PSTN gateway that's in the same network site. For example, the user is at their office. 

- **The user is located at a different Location-Based Routing enabled site than the gateway through which the PSTN call routes. (Remote location)**<br>In this scenario, the user is located at a configured network site that's enabled for Location-Based Routing, and that site is not associated with the PSTN gateway through which the PSTN call routes. 

- **The user is located at a known site that's not enabled for Location-Based Routing.** <br>In this scenario, the user is located in a configured network site that's not enabled for Location-Based Routing. 

- **The user is located at an unknown site.** 
    - The user is located within the internal network that's not defined as a network site. 
    - The user is located outside the internal network. For example, the user is on the Internet at home or in a coffee shop. 

### Apply Location-Based Routing at the network site 

When users are roaming, network sites enabled for Location-Based Routing will help determine which gateways to use. 

For more scenarios, see [Location-Based Routing scenarios for Operator Connect for India.](location-based-routing-india-scenarios.md). 

#### User with Operator Connect for India number

The following tables describe specifics for outbound and inbound PSTN calls for users who have an Operator Connect for India number:

**Outbound and inbound PSTN calls**

| User location | Outbound call status | Inbound call status |
| --------- | --------- | --------- |
| Office location​  | Allowed​ | Allowed​ |
| Remote location | Not allowed​ | Not allowed​ |
| User at known site  |  Allowed | ? |
| User at unknown site  | Allowed | Allowed |


## Conditions for call transfers with Location-Based Routing 

When a user needs to transfer calls, the following applies: 

When a user transfers a call, the system will decide to deny or allow this action based on conditions applied to the PSTN gateway used to egress the call, the following are the two possible scenarios: 

- For a 1:1 Teams VoIP call and transfer to PSTN: The transfer will be permitted if the user being transferred is able to make that PSTN call at their location using the same PSTN Gateway as the user transferring the call. 

- For an incoming or outgoing PSTN call and transfer to another Teams user: The transfer will be permitted if the person receiving the transferred call is able to make or receive that PSTN call at their current location using the PSTN gateway used by the ongoing PSTN call.  

## Location-Based Routing for conferencing

**NEED INFO FROM MOHAMMED**

## Inbound calls through voice apps (Auto Attendant or Call Queue)

Inbound PSTN calls from a Location-Based Routing enabled gateway are allowed to connect to an auto attendant or call queue. 

Users enabled for Location-Based Routing are supported to receive inbound call transfers for these applications when they are located at the same site the inbound PSTN call originates from. To support Local Media Optimization and Media Bypass in these scenarios, Calls Queues must be configured for transfer mode (Conference Mode = OFF).
 
Call forwarding and simultaneous ringing to users and PSTN is allowed for voice app transfers. Completing the call to the target is subject to the same Location-Based Routing rules listed earlier.  
 
Forwarding to voicemail is also allowed.  

## Delegation

A Teams user may choose delegates who can make and receive calls on their behalf. Delegates need to be at the same network site as the delegator's phone number in order to be on a PSTN call--whether to answer an incoming PSTN call or make an outgoing PSTN call on behalf of the delegator.

Delegation capabilities in Teams are affected by Location-Based Routing as follows: 

- For outbound calls from a delegate on behalf of a delegator, the same rules apply. Call routing is based on the delegate’s call authorization policy, voice routing policy, and location. For more information, see [Teams user places an outbound call to the PSTN](location-based-routing-scenarios.md#teams-user-places-an-outbound-call-to-the-pstn). 

- For inbound PSTN calls to a delegator, the same Location-Based Routing rules that apply for call forwarding or simultaneously ringing to other users also apply to delegates. For more information, see [Teams user transfers or forwards call to another Teams user](location-based-routing-scenarios.md#teams-user-transfers-or-forwards-call-to-another-teams-user), [Teams user transfers or forwards call to PSTN endpoint](location-based-routing-scenarios.md#teams-user-transfers-or-forwards-call-to-pstn-endpoint), and [Simultaneous ringing](location-based-routing-scenarios.md#simultaneous-ringing). 
When a delegate sets a PSTN endpoint as a simultaneous ring target, the voice routing policy of the delegate is used to route the call to the PSTN. 


## Other planning considerations

The following sections describe other planning considerations for Location-Based-Routing.

### Technical considerations for Location-Based Routing

IPv4 and IPv6 subnets are supported, however, IPv6 takes precedence when checking for a match.

### Client support for Location-Based Routing

The following Teams clients are supported:
- Teams desktop clients (Windows and Mac)
- Teams mobile clients (iOS and Android)
- Teams IP phones

The Teams web client is not supported.

### Capabilities not supported by Location-Based Routing

Location-Based Routing doesn't apply to the following interactions:

- An on-premises Skype for Business user calls a Teams user  


## Related articles

- [Enable Location-Based Routing for Direct Routing](location-based-routing-enable.md)
- [Network settings for cloud voice features in Teams](cloud-voice-network-settings.md)
