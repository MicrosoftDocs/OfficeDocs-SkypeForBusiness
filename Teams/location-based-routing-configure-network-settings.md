---
title: Configure network settings for Location-Based Routing
author: LanaChin
ms.author: v-lanac
manager: serdars
ms.topic: article
ms.reviewer: roykuntz
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn how to create and set up network regions, sites, and subnets for Location-Based Routing for Direct Routing.
localization_priority: Normal
ms.collection: 
  - M365-voice
appliesto: 
  - Microsoft Teams
---

# Configure network settings for Location-Based Routing

> [!INCLUDE [Preview customer token](includes/preview-feature.md)]

If you haven't already done so, read [Plan Location-Based Routing for Direct Routing](location-based-routing-plan.md) to review other steps you'll need to take before you configure network settings for Location-Based Routing.

This article describes how to configure network settings for Location-Based Routing. After you deploy Phone System Direct Routing in your organization, the next steps are to create and set up network regions, network sites, and network subnets.

## Define network regions

A network region contains a collection of network sites and interconnects various parts of a network across multiple geographic areas. For steps on how to configure network regions, go to [Manage your network topology for cloud features in Teams](manage-your-network-topology.md).

## Define network sites

A network site represents a location where your organization has a physical venue, such as an office, a set of buildings, or a campus. You must associate each network site in your topology with a network region. For steps on how to configure network sites, see [Manage your network topology for cloud features in Teams](manage-your-network-topology.md).

A best practice for Location-Based Routing is to create a separate site for each location that has unique PSTN connectivity. You can create a site that's enabled for Location-Based Routing or a site that's not enabled for Location-Based Routing. For example, you may want to create a site that's not enabled for Location-Based Routing to allow users who are enabled for Location-Based Routing to make PSTN calls when they roam to that site.

## Define network subnets

Each subnet must be associated with a specific network site. You can associate multiple subnets with the same network site but you can't associate multiple sites with the same subnet. For steps on how to configure network subnets, go to  [Manage your network topology for cloud features in Teams](manage-your-network-topology.md).

For Location-Based Routing for Direct Routing, IP subnets at the location where Teams endpoints can connect to the network must be defined and associated to a defined network to enforce toll bypass. This association of subnets enables Location-Based Routing to locate the endpoints geographically to determine whether a given PSTN call should be allowed. Both IPv6 and IPv4 subnets are supported. When determining whether a Teams endpoint is located at a site, Location-Based Routing first checks for a matching IPv6 address. If an IPv6 address isn't present, Location-Based Routing checks for an IPv4 address.

## Define trusted IP addresses (external subnets)

Trusted IP addresses are the internet external IP addresses of the enterprise network and are used to determine whether the user's endpoint is inside the corporate network. For steps on how to configure trusted IP addresses, go to  [Manage your network topology for cloud features in Teams](manage-your-network-topology.md).

If the user’s external IP address matches an IP address that's in the trusted IP address list, Location-Based Routing checks to determine the internal subnet where the user’s endpoint is located. If the user’s external IP address doesn’t match any IP address that's defined in the trusted IP address list, the endpoint is classified as being at an unknown location and any PSTN calls to or from a user who is enabled for Location-Based Routing are blocked.

## Next steps

Go to [Enable Location-Based Routing for Direct Routing](location-based-routing-enable.md).

## Related topics

- [Plan Location-Based Routing for Direct Routing](location-based-routing-plan.md)

