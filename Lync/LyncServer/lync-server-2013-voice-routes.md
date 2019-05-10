---
title: 'Lync Server 2013: Voice routes'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Voice routes
ms:assetid: a2ddf327-2ec4-407b-af0f-276f2b13eefd
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412757(v=OCS.15)
ms:contentKeyID: 48185038
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Voice routes in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-22_

Call routes specify how Lync Server handles outbound calls placed by Enterprise Voice users. When a user dials a number, the Front End Server normalizes the dial string to E.164 format, if necessary, and attempts to match it to a SIP URI. If the server cannot make the match, it applies outgoing call routing logic based on the number. The final step in defining that logic is to create a separate named call route for each set of destination phone numbers that are listed in each dial plan.

Before you define outbound call routes, you should complete the following steps:

  - Deploy one or more trunks.

  - Create dial plans as needed for sites, individuals, and Contact objects.

  - Create public switched telephone network (PSTN) usage records.

Additionally, to enable outbound call routing, you must create and assign one or more voice policies. You can do this either before or after you define outbound call routes.

For each route, you must specify:

  - A name by which the route can be easily identified.

  - An optional description in cases where the name alone may not be sufficient to describe the route.

  - The regular expression matching pattern that identifies the destination phone numbers to which the route is applied, along with exceptions to which the matching pattern is not to be applied.

  - One or more trunks that you want to assign to the route.

  - The PSTN usage records that users must have in order to call numbers matching the destination phone number regular expression.

You can specify call routes in the Lync Server Control Panel. These call routes populate the server routing table, which Lync Server uses to route calls that are destined for the PSTN.

<div>

## M:N Trunk Support

Lync Server provides flexibility in how calls are routed to the PSTN. A voice route specifies a set of trunks to the PSTN that can be used for a particular voice call. A trunk associates a Mediation Server and a port number with a PSTN gateway and listening port number. This logical association enables a Mediation Server to be associated with multiple gateways and have multiple connections to the same gateway. When defining a call route, you specify the trunks associated with that route, but you do not specify which Mediation Servers are associated with the route. To create trunks by defining the relationships between Mediation Servers and PSTN gateways, IP-PBXs, and Session Border Controllers (SBCs), use the Topology Builder.

</div>

<div>

## Least-Cost Routing

The ability to specify the trunks to which various numbers are routed enables you to determine which routes incur the lowest costs and implement them accordingly. The general rule in selecting trunks is to choose the trunk with the closest gateway to the location of the destination number in order to minimize long-distance charges. For example, if you are in New York and calling a number in Rome, you would carry the call over the IP network to the trunk with the gateway in your Rome office, thereby incurring a charge only for a local call.

For an example of how least-cost routing might be used, consider the following: Fabrikam decides to enable German users to dial U.S. numbers by using the U.S. trunk. Fabrikam also wants to configure the system so that all calls from U.S. Lync Server users to Germany and adjacent countries/regions terminate on the trunk with the gateway in Germany. This routing will save money, because a call from Germany to Austria, for example, is less expensive than a call from the U.S. to Austria.

</div>

<div>

## Translating Outbound Dial Strings

Lync Server 2013, like its immediate predecessors, requires all dial strings to be normalized to E.164 format for the purpose of performing reverse number lookup (RNL). For trunks with gateways or private branch exchanges (PBXs) that require numbers translated in local dialing formats, Lync Server 2013 enables you to create one or more rules that assist in manipulating the called number (i.e. Request URI) prior to routing it to the trunk. For example, you could write a rule to remove +44 from the head of a dial string and replace it with 0144.

With Lync Server 2013, it is possible to create one or more rules that assist in manipulating the calling number prior to routing it to the trunk.

In planning your trunks that associate gateways:port pairs with Mediation Server:port pairs, it may be useful to group trunks with similar local dialing requirements, and therefore reduce the number of required translation rules and the time it takes to write them.

</div>

<div>

## Configuring Caller ID

Lync Server provides a way to manipulate the caller ID for outbound calls. For example, if an organization wants to mask employees’ direct-dial extensions and replace them with the generic corporate or departmental number, an administrator can do that by using Lync Server Control Panel to suppress the caller ID and replace it with a specified alternative caller ID. In planning your routing logic, consider which individuals, groups, sites you’ll want this option for—perhaps, even, for all employees.

<div>


> [!NOTE]  
> For calls that are rerouted over the PSTN, the generic caller ID will be presented instead of the original caller ID. This can cause the call to bypass Do Not Disturb or privacy settings that the callee may have configured.



</div>

</div>

<div>

## Additional Routing Logic

In creating outbound call routes, you should be aware of the following factors that can affect routing logic:

  - Where a call is established over a federated boundary, the domain portion of the URI is used to route the call over to the enterprise that is responsible for applying the outbound routing logic.

  - If the domain portion of the request URI does not contain a supported domain for the enterprise, the outbound routing component on the server does not process the call.

  - If a user is not enabled for Enterprise Voice, the server applies other routing logic, as appropriate.

  - If a call is routed to a gateway that is fully occupied (all trunk lines are busy), the gateway rejects the call and the outbound routing logic redirects the call to the next-least-cost route. Give this careful consideration, because a gateway sized for a small office overseas (for example, Zurich) may actually carry a significant amount of nonlocal traffic for international calls to Switzerland. If the gateway is not correctly sized for this additional traffic, calls to Switzerland may be routed by way of a gateway in Germany, resulting in larger toll charges.

</div>

</div>

<span> </span>

</div>

</div>

</div>

