---
title: Plan Location-Based Routing for Operator Connect for India
author: CarolynRowe
ms.author: crowe
manager: pamgreen
ms.topic: conceptual
ms.service: msteams
audience: admin
ms.reviewer: roykuntz
ms.date: 09/01/2023
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

In India, it's illegal to bypass the Public Switched Telephone Network (PSTN) provider. Because toll bypass is restricted, telecom service providers in India are required to block PSTN calls made or received by customers who are roaming outside of their PSTN location. 

Location-Based Routing for Operator Connect for India lets you ensure that Teams users don't violate toll bypass restrictions.

This article describes what you need to know to use Location-Based Routing with Operator Connect for India. 

The configuration for Location-Based Routing for Operator Connect for India differs from the configuration for Location-Based Routing for Direct Routing. To configure Location-Based Routing for Operator Connect for India, you'll need to:

- Ensure your network configuration settings are accurate.

- Associate your Operator Connect India fixed-line phone numbers to the appropriate network sites.

This article describes basic concepts and configuration information. The article applies to fixed-line numbers only.


## Configure Location-Based Routing for fixed-line number calls

To configure Location-Based Routing for Operator Connect for India fixed-line number calls, you must ensure that India fixed-line phone numbers are associated with the network site the phone number corresponds to. The user must be located at a Network Communication Server (NCS) site associated with the number at the time of the call. 

Note: Unlike Direct Routing, Operator Connect for India doesn't require you to enable users, PSTN gateways, and network sites for Location-Based Routing.

### Configure network settings

Location-Based Routing for Operator Connect for India fixed-line calls uses the network topology you define for network region, site, subnet, and trusted IP addresses. A **network site** represents a location where your organization has a physical venue, such as an office, a set of buildings or a campus. 

For toll bypass to be restricted for a geographical location, you associate each IP **network subnet** for that location to a network site. A **network region** is a collection of network sites. Each network site must be associated with a network region. 

**Trusted IP addresses** are the internet external IP addresses of the enterprise network. They determine whether the user's endpoint is inside the corporate network before checking for a specific site match.

At the time of a PSTN call, a user’s location is determined by the IP subnet that the user’s Teams endpoints are connected to. If a user has multiple Teams clients located at different sites, Location-Based Routing enforces each client’s routing separately depending on the location of the Teams endpoints.

Location-Based Routing checks that a user is inside the corporate network by first matching the user's external IP address against the NCS trusted IP address list.  Location-Based Routing then matches the Teams user's local IP address against the NCS site IP address list.

For more information about network settings, see [Network settings for cloud voice features in Teams](cloud-voice-network-settings.md) and [Configure network settings for Location-Based Routing](location-based-routing-configure-network-settings-india.md).


### Associate phone numbers to network sites

To associate your Operator Connect India fixed-line phone numbers to the appropriate network sites, you'll use the [Set-CsPhoneNumberAasignment](/powershell/module/teams/set-csphonenumberassignment) cmdlet as shown in the following example:


```powershell
Set-CsPhoneNumberAssignment -PhoneNumber <string> -NetworkSiteId <string>
```

## Toll bypass evaluation and outcome

When Location-Based Routing for Operator Connect for India is used, a call between a Teams user and the PSTN is evaluated to determine if toll bypass is restricted. Depending on the results, the call will or won't complete.   

Toll bypass evaluation depends on whether the Teams user is located at the network site their assigned phone number corresponds to. 

A network site might be in an unknown state, which means a site not configured using tenant network subnets and sites. Typically, such sites are either internal to the corporate network, but by design not configured, or external to the corporate network. 

If a call can't complete, the Teams user is notified as follows:

- For outbound PSTN calls, the following message appears in the call window: *Call not allowed due to your organization’s settings.*

- For inbound PSTN calls, the call is routed based on the called Teams user’s unanswered call forwarding settings, typically to voicemail. If the Teams user doesn’t have unanswered call settings configured, the call will disconnect.

The following table describes specifics for outbound and inbound PSTN calls for users who have an Operator Connect for India number:

**Outbound and inbound PSTN calls**

| User location | Outbound call status | Inbound call status |
| --------- | --------- | --------- |
| Office location​  | Allowed​ | Allowed​ |
| Remote location | Not allowed​ | Not allowed​ |
| User at known site  |  Not allowed | Not allowed |
| User at unknown site  | Not allowed | Not allowed |

The location and call completion behavior described in the table applies to both of the following:

- PSTN calls to and from numbers assigned directly to the user. 

- PSTN calls indirectly assigned through an Auto attendant or Call queue. The user on the PSTN call must be located at the same site that the Auto attendant or Call queue number is associated with. 


## Call transfers, delegation, and conferencing 

The following sections describe the behavior for call transfers, delegation, and conferencing with Location-Based Routing for Operator Connect for India. Transfers, delegation, and conferencing are allowed only if all users involved in the operation are located at the same network site as the PSTN number of the Operator Connect for India user. 

Note: transfers, forwards, delegation, and conferencing of an Operator Connect for India PSTN call are allowed only to other Operator Connect for India users with the same operator. 

### Call transfers

The following table describes behaviors for call transfers with Operator Connect for India.  Assume the following: 

- **User 1** is an Operator Connect for India user on a VoIP call.
- **User 2** is an Operator Connect for India user on a PSTN call.


| Location | User 1 adds a PSTN user | User 2 adds a VoIP user | User 1 transfers to a PSTN number | User 2 transfers to a VoIP user | 
| --------- | --------- | --------- | --------- | --------- | 
| Users are at the same site as the PSTN number of the Operator Connect user | Allowed | Allowed | Allowed | Allowed | 
| Any user is at a different site than the PSTN number of the Operator Connect user | Not allowed | Not allowed | Not allowed | Not allowed | 

### Delegation

The following table describes behaviors for delegation with Operator Connect for India:

| Delegate location | Delegate makes or receives a PSTN Call for delegator |
| --------- | --------- |
| Same site as number of delegator | Allowed |
| Different site than number of delegator  | Not allowed |

### Audio conferencing

Audio conferencing with Location-Based Routing for Operator Connect for India users depends on whether the Operators Connect for India user also has an Audio conferencing license.

**With an Audio conferencing license** - If a user with an assigned Operator Connect for India Teams Phone license also has an Audio Conferencing license, then the following rules apply:

- All scheduled meetings created by the user (including meet now) will allow participants to join the meeting by using the dial-in phone numbers available in the meeting invite. 

- If the tenant admin has enabled dial out from meetings for the user, participants can also dial out from the meeting to external PSTN users. 

For more information, see [Outbound calling restrictions](outbound-calling-restriction-policies.md). 

**Without an Audio conferencing license** - If a user with an assigned Operator Connect for India Teams Phone license doesn't have an Audio Conferencing license, then the following rules apply.  Assume that **User A** and **User B** are both Operator Connect for India users. 

| Location | User A is in a VoIP meeting that User A scheduled with User B, and User A attempts to add a PSTN call | User A is in a VoIP meeting scheduled by User B, and User B  attempts to add a PSTN call |  
| --------- | --------- | --------- | 
| Other VoIP meeting participants are at the same site as the PSTN number of the meeting organizer | Allowed | Allowed | 
| Any participant is at a different site than the PSTN number of the meeting organizer | Not allowed | Not allowed | 


## Client support for Location-Based Routing

The following Teams clients are supported:
- Teams desktop clients (Windows and Mac)
- Teams mobile clients (iOS and Android)
- Teams IP phones

The Teams web client isn't supported.


## Related articles

- [Plan Operator Connect for India](operator-connect-india-plan.md)
- [Configure Operator Connect for India](operator-connect-india-configure.md)
- [Network settings for cloud voice features in Teams](cloud-voice-network-settings.md)
- [Configure network settings for Location-Based Routing](location-based-routing-configure-network-settings-india.md)



