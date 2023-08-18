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

# Plan and configure Location-Based Routing for Operator Connect for India

In India, it's illegal to bypass the Public Switched Telephone Network (PSTN) provider. Because toll bypass is restricted, telecom service providers in India are required to block international calls made or received by customers who are roaming outside of their PSTN connection. 

Location-Based Routing for Operator Connect for India lets you ensure that Teams users don't violate toll bypass restrictions.

This article describes what you need to know to use Location-Based Routing with Operator Connect for India. This article applies only to Location Based Routing for Operator Connect for India. 

Note that the configuration for Location-Based Routing for Operator Connect for India differs from the configuration for Location-Based Routing for Direct Routing. To configure Location-Based Routing for Operator Connect for India, you will need to:

- Ensure your network configuration settings are accurate
- Associate your Operator Connect India phone numbers to the appropriate network sites

> [!NOTE]
> You shouldn't use Location-Based Routing to dynamically route PSTN calls based on the location of the user. To do so may cause unintended results.

This article describes basic concepts and configuration information.


## Configure Location-Based Routing for fixed-line calls

To configure Location-Based Routing for Operator Connect for India fixed-line calls, you must ensure that India fixed-line phone numbers are associated with the network site the phone number corresponds to. The user must be located at a Network Communication Server (NCS) site associated with the number. 

Note:  Operator Connect for India doesn't require you to enable users, PSTN gateways, and network sites for Location-Based Routing.

### Configure network settings

Location-Based Routing for Operator Connect for India fixed-line calls uses the network topology you define for network region, site, subnet, and public IPs. A **network site** represents a location where your organization has a physical venue, such as an office, a set of buildings or a campus. When toll bypass is restricted for a geographical location, you associate each IP network subnet and each PSTN gateway for that location to a network site. A **network region** is a collection of network sites. Each network site must be associated with a network region. 

![Diagram showing network topology for Location-Based Routing.](media/lbr-network-topology.png "Diagram showing network topology for Location-Based Routing")

At the time of a PSTN call, a user’s location is determined by the IP subnet that the user’s Teams endpoints are connected to. If a user has multiple Teams clients located at different sites, Location-Based Routing enforces each client’s routing separately depending on the location of the Teams endpoints.

For more information about network settings, see [Network settings for cloud voice features in Teams](cloud-voice-network-settings.md) and [Configure network settings for Location-Based Routing](location-based-routing-configure-network-settings.md).


### Associate phone numbers to network sites

To associate your Operator Connect India phone numbers to the appropriate network sites, you'll use the [set-csphonenumberassignment](/powershell/module/teams/set-csphonenumberassignment) cmdlet as shown in the following example:

**GET CORRECT SYNTAX/EXAMPLES FROM JENS**

```powershell
set-csphonenumberassignment -telephone number '12345' -networksiteid 'dehli'
```


## Toll bypass evaluation and outcome

When Location-Based Routing for Operator Connect for India is used, a call between a Teams user and the PSTN is evaluated to determine if toll bypass is restricted. Depending on the results, the call will or will not complete.   

Toll bypass evaluation depends on whether the Teams user is located at the network site their assigned phone number corresponds to. 

A network site might be in an unknown state, which means a site not configured using tenant network subnets and sites. Typically, such sites are either internal to the corporate network, but by design not configured, or external to the corporate network. 

If a call can't complete, the Teams user is notified as follows:

**IS THE FOLLOWING TRUE?**

- For outbound PSTN calls, the following message appears in the call window: *Call not allowed due to your organization’s settings.*

- For inbound PSTN calls, the call is routed based on the called Teams user’s unanswered call forwarding settings, typically to voicemail. If the Teams user doesn’t have unanswered call settings configured, the call will disconnect.

The following tables describe specifics for outbound and inbound PSTN calls for users who have an Operator Connect for India number:

**Outbound and inbound PSTN calls**

| User location | Outbound call status | Inbound call status |
| --------- | --------- | --------- |
| Office location​  | Allowed​ | Allowed​ |
| Remote location | Not allowed​ | Not allowed​ |
| User at known site  |  Allowed | ? |
| User at unknown site  | ? | ? |


## Call transfers with Location-Based Routing for Operator Connect for India

Transfers are allowed only to other users with the same Operator Connect for India operator. When a user transfers a call, the system will decide to deny or allow this action based on conditions applied to the PSTN gateway used to egress the call, the following are the two possible scenarios: 

- For a 1:1 Teams VoIP call and transfer to PSTN: The transfer will be permitted if the user being transferred is able to make that PSTN call at their location using the same PSTN Gateway as the user transferring the call. 

- For an incoming or outgoing PSTN call and transfer to another Teams user: The transfer will be permitted if the person receiving the transferred call is able to make or receive that PSTN call at their current location using the PSTN gateway used by the ongoing PSTN call.  

## Conferencing with Location-Based Routing for Operator Connect for India

**NEED INFO FROM MOHAMMED**

Users are allowed in conferences with the following restrictions: 

**Fixed line (wired)**: All Teams users in the conference must be located at the same network site and with the same operator Teams Phone license when one leg is a PSTN call; users without the same operator Teams Phone license must be restricted.

Signaling and media from Teams clients must traverse the carrier’s data network between the network site and the Microsoft 365 cloud.



## Delegation with Location-Based Routig for Operator Connect for India

A Teams user may choose delegates who can make and receive calls on their behalf. Delegates need to be at the same network site as the delegator's phone number in order to be on a PSTN call--whether to answer an incoming PSTN call or make an outgoing PSTN call on behalf of the delegator.

Delegation capabilities in Teams are affected by Location-Based Routing as follows: 

- For outbound calls from a delegate on behalf of a delegator, the same rules apply. Call routing is based on the delegate’s call authorization policy, voice routing policy, and location. For more information, see [Teams user places an outbound call to the PSTN](location-based-routing-scenarios.md#teams-user-places-an-outbound-call-to-the-pstn). 

- For inbound PSTN calls to a delegator, the same Location-Based Routing rules that apply for call forwarding or simultaneously ringing to other users also apply to delegates. For more information, see [Teams user transfers or forwards call to another Teams user](location-based-routing-scenarios.md#teams-user-transfers-or-forwards-call-to-another-teams-user), [Teams user transfers or forwards call to PSTN endpoint](location-based-routing-scenarios.md#teams-user-transfers-or-forwards-call-to-pstn-endpoint), and [Simultaneous ringing](location-based-routing-scenarios.md#simultaneous-ringing). 
When a delegate sets a PSTN endpoint as a simultaneous ring target, the voice routing policy of the delegate is used to route the call to the PSTN. 


## Client support for Location-Based Routing

The following Teams clients are supported:
- Teams desktop clients (Windows and Mac)
- Teams mobile clients (iOS and Android)
- Teams IP phones

The Teams web client is not supported.

## Other planning considerations

This section describe other planning considerations for Location-Based-Routing for India:

- IPv4 and IPv6 subnets are supported, however, IPv6 takes precedence when checking for a match.

- Location-Based Routing for Operator Connect for India doesn't apply when an on-premises Skype for Business user calls a Teams user.

## Related articles

- [Plan Operator Connect for India](operator-connect-india-plan.md)
- [Configure Operator Connect for India](operator-connect-india-configure.md)
- [Network settings for cloud voice features in Teams](cloud-voice-network-settings.md)
- [Configure network settings for Location-Based Routing](location-based-routing-configure-network-settings.md)

