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

Note that the configuration for Location-Based Routing for Operator Connect for India differs from the configuration for Location-Based Routing for Direct Routing. To configure Location-Based Routing for Operator Connect for India, you'll need to:

- Ensure your network configuration settings are accurate.

- Associate your Operator Connect India fixed-line phone numbers to the appropriate network sites.

This article describes basic concepts and configuration information. The article applies to fixed-line numbers only.


## Configure Location-Based Routing for fixed-line calls

To configure Location-Based Routing for Operator Connect for India fixed-line calls, you must ensure that India fixed-line phone numbers are associated with the network site the phone number corresponds to. The user must be located at a Network Communication Server (NCS) site associated with the number at the time of the call. 

Note:  Operator Connect for India doesn't require you to enable users, PSTN gateways, and network sites for Location-Based Routing.

### Configure network settings

Location-Based Routing for Operator Connect for India fixed-line calls uses the network topology you define for network region, site, subnet, and trusted IP addresses. A **network site** represents a location where your organization has a physical venue, such as an office, a set of buildings or a campus. 

For toll bypass to be restricted for a geographical location, you associate each IP **network subnet** for that location to a network site. A **network region** is a collection of network sites. Each network site must be associated with a network region. 

**Trusted IP addresses** are the internet external IP addresses of the enterprise network. They determine whether the user's endpoint is inside the corporate network before checking for a specific site match.

At the time of a PSTN call, a user’s location is determined by the IP subnet that the user’s Teams endpoints are connected to. If a user has multiple Teams clients located at different sites, Location-Based Routing enforces each client’s routing separately depending on the location of the Teams endpoints.

Location-Based Routing checks that a user is inside the corporate network by first matching the user's external IP address against the NCS trusted IP address list.  Location-Based Routing then matches the Teams user's local IP address against the NCS site IP address list.

For more information about network settings, see [Network settings for cloud voice features in Teams](cloud-voice-network-settings.md) and [Configure network settings for Location-Based Routing](location-based-routing-configure-network-settings.md).


### Associate phone numbers to network sites

To associate your Operator Connect India fixed-line phone numbers to the appropriate network sites, you'll use the [Set-CsPhoneNumberAasignment](/powershell/module/teams/set-csphonenumberassignment) cmdlet as shown in the following example:


```powershell
Set-CsPhoneNumberAssignment -PhoneNumber <string> -NetworkSiteId <string>
```

## Toll bypass evaluation and outcome

When Location-Based Routing for Operator Connect for India is used, a call between a Teams user and the PSTN is evaluated to determine if toll bypass is restricted. Depending on the results, the call will or will not complete.   

Toll bypass evaluation depends on whether the Teams user is located at the network site their assigned phone number corresponds to. 

A network site might be in an unknown state, which means a site not configured using tenant network subnets and sites. Typically, such sites are either internal to the corporate network, but by design not configured, or external to the corporate network. 

If a call can't complete, the Teams user is notified as follows:

- For outbound PSTN calls, the following message appears in the call window: *Call not allowed due to your organization’s settings.*

- For inbound PSTN calls, the call is routed based on the called Teams user’s unanswered call forwarding settings, typically to voicemail. If the Teams user doesn’t have unanswered call settings configured, the call will disconnect.

The following tables describe specifics for outbound and inbound PSTN calls for users who have an Operator Connect for India number:

**Outbound and inbound PSTN calls**

| User location | Outbound call status | Inbound call status |
| --------- | --------- | --------- |
| Office location​  | Allowed​ | Allowed​ |
| Remote location | Not allowed​ | Not allowed​ |
| User at known site  |  Not allowed | Not allowed |
| User at unknown site  | Not allowed | Not allowed |


## Call transfers with Location-Based Routing for Operator Connect for India

Transfers are allowed only to other users with the same Operator Connect for India operator. When a user transfers a call, the system will decide to deny or allow this action based on the following possible scenarios: 

- For a 1:1 Teams VoIP call and transfer to PSTN: The transfer is permitted if the user being transferred and the user transferring the call are at the same site. 

- For an incoming or outgoing PSTN call and transfer to another Teams user: The transfer is permitted if the person receiving the transferred call is able to make or receive that PSTN call at their current location.  **TRUE?**

## Delegation with Location-Based Routing for Operator Connect for India

A Teams user may choose delegates who can make and receive calls on their behalf. Delegates need to be at the same network site as the delegator's phone number in order to be on a PSTN call--whether to answer an incoming PSTN call or make an outgoing PSTN call on behalf of the delegator.

Delegation capabilities in Teams are affected by Location-Based Routing as follows: 

- For outbound calls from a delegate on behalf of a delegator, the same rules apply. Call routing is based on the delegate’s call authorization policy, voice routing policy, and location. For more information, see [Teams user places an outbound call to the PSTN](location-based-routing-scenarios.md#teams-user-places-an-outbound-call-to-the-pstn). 

- For inbound PSTN calls to a delegator, the same Location-Based Routing rules that apply for call forwarding or simultaneously ringing to other users also apply to delegates. For more information, see [Teams user transfers or forwards call to another Teams user](location-based-routing-scenarios.md#teams-user-transfers-or-forwards-call-to-another-teams-user), [Teams user transfers or forwards call to PSTN endpoint](location-based-routing-scenarios.md#teams-user-transfers-or-forwards-call-to-pstn-endpoint), and [Simultaneous ringing](location-based-routing-scenarios.md#simultaneous-ringing). 
When a delegate sets a PSTN endpoint as a simultaneous ring target, the voice routing policy of the delegate is used to route the call to the PSTN. 


## Conferencing with Location-Based Routing for Operator Connect for India

Conferencing with Location-Based Routing for Operator Connect for India users depends on whether that user also has an Audio Conferencing license.

### User has an Audio Conferencing license

If a user with an assigned Operator Connect for India Teams Phone license also has an Audio Conferencing license, then the following rules apply:

- All scheduled meetings created by the user (including meet now) will allow participants to join the meeting by using the dial-in phone numbers available in the meeting invite. 

- If the tenant admin has enabled dial out from meetings for the user, participants can also dial out from the meeting to external PSTN users. 

- If a user with an assigned Operator Connect for India Teams Phone license is already on a 1:1 PSTN call, the user can add a participant or escalate the existing call to a conference. 

For more information, see [Outbound calling restrictions](outbound-calling-restriction-policies.md). 


### User doesn't have an Audio Conferencing license

If a user with an assigned Operator Connect for India Teams Phone license doesn't have an Audio Conferencing license, then the following rules apply:

- If there is or has been at least one Operator Connect for India Teams Phone user in the meeting, all scheduled meetings created by the user (including meet now) won't allow adding PSTN participants. 

- If any one PSTN participant is or was part of such a conference call before any Operator Connect for India Teams Phone users were invited to join the call, then Operator Connect for India Teams Phone users can't be added to the call.

- If the Operator Connect for India Teams Phone user is joining the conference call from an internal site, the restrictions in the preceding two list items are not enforced.

### Other considerations

Keep the following considerations in mind:

- On-network conferencing for Audio Conferencing must NOT be deployed with any telephony equipment in India.

- An Operator Connect for India user on a PSTN call is not allowed to merge that call with another call. 

- The following are not supported: recording and compliance recording of the PSTN call.
 



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

