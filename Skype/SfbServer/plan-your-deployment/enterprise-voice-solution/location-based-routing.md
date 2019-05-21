---
title: "Plan for Location-Based Routing in Skype for Business"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection:
- IT_Skype16
- Strat_SB_Admin
ms.custom:
ms.assetid: 4aa494bd-0d66-4335-b9e8-f758d44a7202
description: "Planning for location-based routing in Skype for Business Server Enterprise Voice, including interaction with simultaneous ringing and delegation, and supported scenarios for location-based routing."
---

# Plan for Location-Based Routing in Skype for Business

Planning for location-based routing in Skype for Business Server Enterprise Voice, including interaction with simultaneous ringing and delegation, and supported scenarios for location-based routing.

Location-Based Routing makes it possible to restrict the routing of calls between VoIP endpoints and PSTN endpoints based on the location of the parties in the call. Location-Based Routing is a call management feature that controls how calls are routed by Skype for Business Server. It enforces call authorization rules on whether calls can be routed to PBX or PSTN endpoints based on the Skype for Business caller's geographic location.

Location-Based Routing introduces a new set of rules that modifies the routing of national and international PSTN calls to prevent toll bypass. Location-Based Routing provides the flexibility to scope these rules to specific regions, specific gateways or to specific set of users only.

The following scenarios illustrate the main types of restrictions Location-Based Routing can enforce:

- Egress calls - Location-Based Routing can enforce outgoing calls to egress to a PSTN gateway that is located in the same region as where the caller is to prevent PSTN toll bypass, which prevents calls to egress to a PSTN gateway located in a different region as the caller.

- Ingress calls - Location-Based Routing can prevent incoming PSTN calls to ring Skype for Business endpoints if the PSTN gateway routing the incoming call is not located in the same region as the called Skype for Business user.

- Unknown regions - Location-Based Routing restricts incoming and outgoing PSTN calls to and from users that are located in undetermined locations (i.e. remote users connecting from the Internet or located in unknown regions).

- International regions - Location-Based Routing enforces routing of outgoing calls through international PSTN gateways if a gateway local to the user's location cannot be found.

## Guidance for where to apply Location-Based Routing

Location-Based Routing depending on the situation can be applied at the user's endpoint network site location or at the PSTN gateway's network site location. This topic provides guidance on how Location-Based Routing is applied.

### Applying Location-Based Routing at the user's location

Location-Based Routing leverages the same network regions, sites and subnets as defined in Skype for Business Server used by E9-1-1, CAC and Media Bypass to apply call routing restrictions to prevent PSTN toll bypass. A user's location is determined by the IP subnet of the user's Skype for Business endpoint(s) are connected from. Each IP subnet is associated to a network site, which are aggregated into network regions defined by the administrator. Location-Based Routing is enforced based on the user's network site.

Location-Based Routing rules are applied on a per network site basis, meaning that a given set of rules will be applied to all endpoints enabled for Location-Based Routing that are located within the same network site. Administrators can apply Location-Based Routing to network sites that require it.

Voice routing policies can be defined on a per network site basis to define a particular PSTN gateway that should be used by all users located in the network site to call PSTN phone numbers. Such voice routing policies will take precedence over the routing defined by the user's voice policy when the user is located in a network site enabled for Location-Based Routing, and it will prevent the routing of calls via other PSTN gateways that are enabled for Location-Based Routing. When a Skype for Business user places a PSTN call, the user's voice policy determines whether the user can be authorized to place the call. If the user's voice policy allows the user to place the call, Location-Based Routing determines which PSTN gateway the call should egress from. Location-Based Routing makes this determination based on the user's location.

A user location can be categorized in the following ways:

- The user is located in a known network site enabled for Location-Based Routing and his DID (Direct Inward Dial) number terminates on a PSTN gateway placed in the same network site (i.e. office). The routing of outbound calls will be through the voice routing policy of the network site in which the user is located. Incoming PSTN calls to the user are routed to endpoints that are located in the same network site as the PSTN gateway.

- The user is located in a known network site that is in different from the network site where the PSTN gateway is located. (i.e. the user traveled to another corporate office). The routing of outbound calls will be using the voice routing policy of the network site in which the user is located. Incoming PSTN calls to the user will not be routed to endpoints that are located in different sites than the PSTN gateway to prevent PSTN toll bypassing.

- When a user is located in a network site that is unknown to the Skype for Business Server deployment, the routing of outbound calls will be based on the voice policy assigned to the user to PSTN gateways not bound to Location-Based Routing restrictions. Incoming PSTN calls will not be routed to endpoints that are located in unknown network sites to prevent PSTN toll bypassing.

### Applying Location-Based Routing at the PSTN gateway's location

Calls routed via PSTN gateways and PBXs might require Location-Based Routing restrictions depending on the location of such systems. Location-Based Routing can be enabled at the granularity on a per trunk basis.

Location-Based Routing introduces the following set of rules when enabled on a trunk:

- When Location-Based Routing is enabled on a per trunk basis, the rules define on that trunk will be applied only to calls routed through that trunk.

- To prevent PSTN tolls bypass where calls originate from a network site different that the network site where the PSTN gateway is located, Location-Based Routing introduces the association of a network site to a given trunk. This defines the network site that allows calls to be routed to a given trunk.

Trunks can be enabled for Location-Based Routing in two ways:

- The trunk is defined for a PSTN gateway that egresses calls to the PSTN. Incoming calls routed by a trunk of this type will be routed only to endpoints located within the same network site as the trunk.

- The trunk is defined for a Mediation Server peer that doesn't egress calls to the PSTN and services users with legacy phones in a static locations (i.e. PBX phones). For this particular configuration, all incoming calls routed by a trunk of this type will be considered to be originating from the same network site as the trunk. Calls from PBX users will have the same Location-Based Routing enforcement as Skype for Business users who are located in the same network site as the trunk. If two PBX systems located in separate network sites are connected through Skype for Business Server, Location-Based Routing will allow routing from one PBX endpoint in one network site to another PBX endpoint in the other network site. This scenario will not be blocked by Location-Based Routing. In addition to this scenario and in a similar way as a Skype for Business user in the same location, endpoints connected to a Mediation Server peer with this configuration will be able to make or receive calls to and from other Mediation Server peer that do not route calls to the PSTN (i.e. an endpoint connected to a different PBX) regardless of the network site to which the Mediation Server peer is associated. All inbound calls, outbound calls, call transfers and call forwards involving PSTN endpoints will be subject to Location Based Routing to use only PSTN gateways that are defined as local to such Mediation Server peer.

## Scenarios for Location-Based Routing

Location-Based Routing applies the following general rules when routing calls in the following scenarios.

### Outgoing calls

The routing of outbound calls of users enabled for Location-Based Routing is affected by the network location of the user's endpoint. The following table illustrates how Location-Based Routing affects the routing of outbound calls depending on the location of the caller's endpoint.

**Caller placing an outbound call to the PSTN**

||**User endpoint located in a network site enabled for Location-Based Routing**|**User endpoint located in unknown network site or not enabled for Location-Based Routing**|
|:-----|:-----|:-----|
|Authorization of outbound calls  <br/> |Call is authorized based on user's voice policy  <br/> |Call is authorized based on user's voice policy  <br/> |
|Routing of outbound call  <br/> |Call is routed according to the network site's voice routing policy  <br/> |Call is routed according to user's voice policy and only through trunks not enabled for Location-Based Routing (if available)  <br/> |

### Incoming Calls

The routing of incoming calls to users enabled for Location-Based Routing depends on the location of the user's endpoint. The routing of incoming calls is affected in the following way. If a user has an incoming call to an endpoint located in a Location-Based Routing enabled network site, and the endpoint is located in the same network site as the PSTN gateway, the call will be routed. If a user has an incoming call to an endpoint located in a Location-Based Routing enabled network site, and the endpoint is located in a different network site than the PSTN gateway, the call will not be routed. When a user has no endpoints located in the same network site as the PSTN gateway where the incoming call is originating from, the incoming call will be routed directly to the user's voicemail and a missed call notification will be sent to the called party.

The call forwarding settings of a user that is enabled for Location-Based Routing will continue to be enforced, however, calls forwarded will be subject to Location-Based Routing restrictions of the user.

The following table illustrates how Location-Based Routing affects the routing of inbound calls depending on the location of the callee's endpoint. The network site of the PSTN gateway is enabled for Location-Based Routing, and Location-Based Routing only permits routing of PSTN calls to endpoints within the same network site.

**Callee receiving an inbound call from the PSTN**

||**Callee's endpoint located in the same network site as PSTN gateway**|**Callee's endpoint not located in the same network site as PSTN gateway**|**Callee's endpoint located in unknown network site or not enabled for Location-Based Routing**|
|:-----|:-----|:-----|:-----|
|Routing of inbound PSTN call  <br/> |Incoming call is routed to callee's endpoints  <br/> |Incoming call is not routed to callee's endpoints  <br/> |Incoming call is not routed to callee's endpoints  <br/> |

### Call transfers and call forwarding

When a PSTN endpoint is involved, Location-Based Routing analyzes the location of the calle's endpoint and the endpoint where the call will be transferred or forwarded to (i.e. transfer/forward target). Location-Based Routing determines whether the call should be transferred or forwarded depending on the location of both endpoints.

The following table illustrates the scenario of a Skype for Business user in a call with a PSTN endpoint, and the Skype for Business user transfers the call to another Skype for Business user. Depending on the network site location of the transferee's endpoint, Location-Based Routing affects the routing of the call transfer or forward.

**Initiating call transfer or forward**

|**User initiating the call transfer/forward**|**Target endpoint is in same network site as user initiating call transfer or forward**|**Target endpoint is in different network site as user initiating call transfer or forward**|**Target endpoint is in unknown network site or network site not enabled for Location-Based Routing**|
|:-----|:-----|:-----|:-----|
|Skype for Business user  <br/> |Call forward or transfer is allowed  <br/> |Call forward or transfer is not allowed  <br/> |Call forward or transfer is not allowed  <br/> |

For example: a Skype for Business user in a call with a PSTN endpoint transfers the call to another Skype for Business user that is in the same network site. In this case, the call transfer is allowed.

The following table illustrates the scenario of a Skype for Business user in a call with another Skype for Business user, and one of the users transfers the call to a PSTN endpoint. Depending on the location of the user the call is being transferred to, the table details how Location-Based Routing affects the call.

**Call transfer or forward to PSTN endpoint**

|**Call transfer/forward endpoint target**|**Skype for Business users in same network site**|**Skype for Business users in different network sites**|**One or both Skype for Business users in unknown network site or network site not enabled for Location-Based Routing**|
|:-----|:-----|:-----|:-----|
|PSTN endpoint  <br/> |Call forward or transfer allowed by the transferred user's site voice routing policy  <br/> |Call forward or transfer allowed by the transferred user's site voice routing policy  <br/> |Call forward or transfer allowed by the transferred user's voice policy only through trunks not enabled for Location-Based Routing  <br/> |

For example: a Skype for Business user in a call with another Skype for Business user that is in the same network site transfers the call to a PSTN endpoint and the call transfer is allowed.

### Simultaneous ringing

When the called party has simultaneous ringing enabled, Location-Based Routing analyzes the location of the calling party and the endpoints of the called parties to determine whether the call should be routed.

The following table illustrates a user configured with simultaneous ringing, and the simultaneous ringing target is a user in the same network site, in a different network site, or in an unknown network site.

****

|**Incoming PSTN call for**|**Located in the same network site as callee**|**Located in different network site than callee**|**Located in unknown network site or not enabled for Location-Based Routing**|
|:-----|:-----|:-----|:-----|
|Skype for Business user  <br/> |Simultaneous ring allowed  <br/> |Simultaneous ring not allowed  <br/> |Simultaneous ring not allowed  <br/> |

The following table illustrates a call from a Skype for Business user (i.e. Skype for Business caller) in the same network site, in a different network site, or from an unknown network site. The callee has a PSTN endpoint (i.e. cellphone) configured as a simultaneous ring target. In this scenario, Location-Based Routing will determine whether the call should be routed to the simultaneous ring target (i.e. cellphone) of the callee or not.

****

|**Simultaneous ring target**|**Located in the same network site as callee**|**Located in different network site than callee**|**Located in unknown network site or not enabled for Location-Based Routing**|
|:-----|:-----|:-----|:-----|
|PSTN endpoint  <br/> |Simultaneous ring allowed through the caller's site voice routing policy  <br/> |Simultaneous ring allowed through the caller's site voice routing policy  <br/> |Simultaneous ring allowed through the caller's voice policy to trunks not enabled for Location-Based Routing  <br/> |

### Skype for Business Cumulative Update 4

With Cumulative Update 4, you're going to see the following:

- Location-Based Routing will continue to be enabled via Voice Policy, including Skype for Business Mobile clients.

- The calling behavior for Skype for Business Mobile clients will be based on whether they're enabled for Location-Based Routing, and the communicating client. This is designed to be static, but there may be, in certain situations, an effort to associate a Skype for Business Mobile client to a local PSTN gateway, and allow certain behaviors, such as an escalation

- Regardless of your OS, your Skype for Business Mobile client should have the same functionality.

The following table will walk you through some of the post-Cumulative Update 4 scenarios:

|**Location-Based Routing User**|**Other Party**|**Action**|**Result**|
|:-----|:-----|:-----|:-----|
|Skype for Business Mobile  <br/> |PSTN  <br/> |Skype for Business Mobile receives an incoming PSTN call.  <br/> |The call is routed via Call via Work (CvW), and not VoIP.  <br/> |
|Skype for Business Mobile  <br/> |PSTN  <br/> |Skype for Business Mobile makes an outgoing PSTN call.  <br/> |The call is routed via CvW, and not VoIP.  <br/> |
|Skype for Business Mobile  <br/> |PSTN  <br/> |Skype for Business Mobile is in a PSTN call. Skype for Business Mobile then escalates the call to another user or contact.  <br/> |The call is routed via VoIP if the user or contact is local to the PSTN gateway leg.  <br/> If the user or contact is remote from the PSTN gateway leg, the call is routed via CvW.  <br/> If the target user is not reachable via the PSTN, then the call fails.  <br/> If the target contact is a Conference Auto Attendant (CAA), the call is blocked.  <br/> |
|Skype for Business Mobile  <br/> |Skype for Business client or Federated user  <br/> |A Skype for Business Mobile initiates a voice call to another Skype for Business client or Federated user.  <br/> |The call is completed via VoIP.  <br/> |
|Skype for Business Mobile  <br/> |Skype for Business client or Federated user  <br/> | A Skype for Business client or Federated user initiates a voice call to a Skype for Business Mobile Location-Based Routing user. <br/> |The call is completed via VoIP.  <br/> |
|Skype for Business Mobile  <br/> |Skype for Business client or Federated user  <br/> |A Skype for Business client or Federated user is on a VoIP call to a Skype for Business Mobile user. Either party escalates to an additional Skype for Business or Federated user.  <br/> |The call is completed via VoIP.  <br/> |
|Skype for Business Mobile  <br/> |Federated User  <br/> |A Federated User is on voice call to a Skype for Business Mobile Location-Based Routing user; a Skype for Business Mobile party escalates to a PSTN user.  <br/> |The call is blocked.  <br/> |
|Skype for Business Mobile  <br/> |Federated User  <br/> |A Federated user is on a VoIP call to a Skype for Business Mobile Location-Based Routing user; either party escalates to a CAA contact.  <br/> |The escalated call is blocked, with an appropriate error message.  <br/> |
|Skype for Business Mobile  <br/> |Federated User  <br/> |A Federated user is on a VoIP call to a Skype for Business Mobile Location-Based Routing user, and the Federated user escalates to a PSTN user.  <br/> |The escalation will be allowed or disallowed based on the Location-Based Routing of the Federated user. The Skype for Business Mobile Location-Based Routing user's application doesn't take any action.  <br/> |

### Delegation

The delegation capabilities in Skype for Business are affected by Location-Based Routing in the following manner:

- When a delegate enabled for Location-Based Routing places a call on behalf of a manager, the delegate's voice policy is used to authorize the call and the delegate's site voice routing policy will be used to route the call

- For incoming PSTN calls to a manager, the same rules applicable for call forwarding or simultaneously ringing will apply as described in the Call transfers and forwarding and Simultaneous ringing topics.

- When a delegate sets a PSTN endpoint as a simultaneous ring target, for an incoming call to the manager, the voice routing policy of the site that is associated to the incoming trunk will be used to route the call to the delegate's PSTN endpoint.

- For delegation, it's recommended that the manager and his associated delegates to be usually located in the same network site.

## Other planning considerations

When planning Location-Based Routing, you should consider the impact to the following scenarios.

### Disaster Recovery

During a failover from the primary pool to a backup pool as well as when restoring normal operations to the primary pool, Location-Based Routing remains enforced at all times during a disaster and recovery procedure.

### Survivable Branch Appliance

Configuring Location-Based Routing impacts the planning of where you deploy the gateways associated to your Survivable Branch Appliances. The gateway associated to your SBA must be located in the same network site as your Survivable Branch Appliance; otherwise, users homed on your Survivable Branch Appliance will not be permitted to place outbound calls if Location-Based Routing is configured. When the WAN connection between your Survivable Branch Appliance and the central site is down, Location-Based Routing restrictions remains enforced.

## Client and server support for Location-Based Routing

Location-Based Routing is enforced by Skype for Business Server. Skype for Business Server can identify the network sites where users are connecting from within the corporate network. Since remote users are outside the corporate network, their location is considered to be unknown.

### Server Support

Location-Based Routing requires that Skype for Business Server or Lync Server 2013 CU1 is deployed on all Front End pools and Standard Edition servers in a given topology. If these versions of the server are not installed,Location-Based Routing restrictions cannot be fully enforced.

The following table identifies the combination of server roles and versions that is supported for Location-Based Routing.

****

|**Pool version**|**Mediation Server version**|**Supported**|
|:-----|:-----|:-----|
|Skype for Business Server or Lync Server 2013 February 2013 Cumulative Update  <br/> |Skype for Business Server or Lync Server 2013 February 2013 Cumulative Update  <br/> |yes  <br/> |
|Skype for Business Server or Lync Server 2013 February 2013 Cumulative Update  <br/> |Lync Server 2013  <br/> |no  <br/> |
|Skype for Business Server or Lync Server 2013 February 2013 Cumulative Update  <br/> |Lync Server 2010  <br/> |no  <br/> |
|Skype for Business Server or Lync Server 2013 February 2013 Cumulative Update  <br/> |Office Communications Server 2007 R2  <br/> |no  <br/> |
|Lync Server 2013  <br/> |any  <br/> |no  <br/> |
|Lync Server 2010  <br/> |any  <br/> |no  <br/> |
|Office Communications Server 2007 R2  <br/> |any  <br/> |no  <br/> |

### Client Support

The following table identifies the clients that Location-Based Routing supports.

****

|**Client type**|**Supported**|**Details**|
|:-----|:-----|:-----|
|Skype for Business  <br/> |yes  <br/> ||
|Lync 2013  <br/> |yes  <br/> ||
|Lync 2010  <br/> |yes  <br/> ||
|Office Communicator 2007 R2  <br/> |no  <br/> ||
|Lync Phone Edition  <br/> |yes  <br/> ||
|Lync Attendant  <br/> |yes  <br/> ||
|Lync for Windows 8  <br/> |no  <br/> ||
|Lync Mobile 2013  <br/> |no  <br/> |VoIP must be disabled for Lync Mobile 2013 clients if used by users with Location-Based Routing enabled.  <br/> |
|Lync Mobile 2010  <br/> |yes  <br/> ||

> [!NOTE]
> To disable VoIP for Skype for Business clients, assign a mobility policy with the setting, IP Audio/Video, disabled for all users enabled for Location-Based Routing. For more details about mobility policy, see [New-CsMobilityPolicy](https://docs.microsoft.com/powershell/module/skype/new-csmobilitypolicy?view=skype-ps).

## Capabilities not supported by Location-Based Routing

Location-Based Routing does not apply to the following types of interactions. Location-Based Routing is not enforced when Skype for Business endpoints interact with PSTN endpoints using these capabilities.

- PSTN dial-in to conferences

- Incoming and outgoing PSTN calls through Response Group

- Call park or retrieval of PSTN calls through Call Park

- Incoming PSTN calls to Announcement Service

- Incoming PSTN calls retrieved via Group Call Pickup

To enforce Location-Based Routing rules to the types of interactions in the following list, you must enable Location-Based Routing for Conferencing:

- PSTN dial-out from conferences

- Escalations from peer-to-peer audio conversations to conferencing involving PSTN endpoints

- Consultative transfers involving PSTN endpoints

To enable Location-Based Routing for Conferencing, see [Location-Based Routing for Conferencing](https://technet.microsoft.com/library/e1acb1ba-0ed2-4abf-8a7b-1ca3049e95e3.aspx).


