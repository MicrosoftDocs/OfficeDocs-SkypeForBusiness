---
title: Network settings for cloud voice features in Microsoft Teams
author: LanaChin
ms.author: v-lanac
manager: serdars
ms.topic: conceptual
ms.reviewer: roykuntz
ms.service: msteams
audience: admin
search.appverid: MET150
description: Learn about the network settings that you must configure for Location-Based Routing for Direct Routing and enhanced emergency services.
localization_priority: Normal
ms.collection: 
  - M365-voice
appliesto: 
  - Microsoft Teams
---

# Network settings for cloud voice features in Microsoft Teams

Learn about network regions, network sites, network subnets, and trusted IP addresses. These terms and concepts are used throughout our cloud voice documentation for [Location-Based Routing for Direct Routing](location-based-routing-plan.md) and enhanced emergency services [LINK TO WHICH ARTICLE?]. If you're deploying any of these cloud voice features in your organization, you must configure network settings for use with these features in Microsoft Teams.

These cloud voice features have common configuration requirements for which you must define network regions, network sites, and subnets. For example, you must associate each network site in your topology with a network region and associate each subnet with a network site.

This article gives you an overview of the configuration requirements that are common to Location-Based Routing for Direct Routing and enhanced emergency services. For steps on how to configure each of these settings, see [Manage your network topology for cloud features in Teams](manage-your-network-topology.md).

## Network region

A network region contains a collection of network sites. It interconnects various parts of a network across multiple geographic areas. For example, if your organization has many sites located in India, you may choose to designate “India” as a network region. Each network site must be associated with a network region.

The same network regions are shared by [Location-Based Routing for Direct Routing](location-based-routing-plan.md) and enhanced emergency services. If you already created network regions for one feature, you don't have to create new network regions for the other feature.

## Network site

A network site represents a location where your organization has a physical venue, such as an office, a set of buildings, or a campus. Network sites are defined as a collection of IP subnets. Each network site must be associated with a network region.

A best practice for Location-Based Routing is to create a separate site for each location that has unique PSTN connectivity. You can create a site that's enabled for Location-Based Routing or a site that's not enabled for Location-Based Routing. For example, you may want to create a site that's not enabled for Location-Based Routing to allow users who are enabled for Location-Based Routing to make PSTN calls when they roam to that site.

You can also use network sites to enable and configure emergency calling.

## Network subnet

Each subnet must be associated with a specific network site. You can associate multiple subnets with the same network site but you can't associate multiple sites with the same subnet. Subnet information is used to determine the network site on which an endpoint is located when a new session is initiated. When the location of each party in a session is known, cloud voice features can apply that information to determine how to handle call setup or routing.

For each network site, work with your network admin to determine which IP subnets are assigned to each network site. For example, the New York site in the North America region can be assigned the following IP subnets: 172.29.80.0/23, 157.57.216.0/25, 172.29.91.0/23, 172.29.81.0/24. If Bob, who usually works in Detroit, travels to the New York office for training, turns on his computer and connects to the network, his computer will get an IP address in one of the four ranges that are allocated for New York, for example, 172.29.80.103.

For Location-Based Routing for Direct Routing, IP subnets at the location where Teams endpoints can connect to the network must be defined and associated to a defined network to enforce toll bypass. This association of subnets enables Location-Based Routing to locate the endpoints geographically to determine whether a given PSTN call should be allowed. Both IPv6 and IPv4 subnets are supported. When determining whether a Teams endpoint is located at a site, Location-Based Routing first checks for a matching IPv6 address. If an IPv6 address isn't present, Location-Based Routing checks for an IPv4 address.

## Trusted IP address

External trusted IP addresses are the internet external IP addresses of the enterprise network. They determine whether the user’s endpoint is inside the corporate network before checking for a specific site match. If the user’s external IP address matches an IP address that's defined in the trusted list, Location-Based Routing checks to determine the internal subnet where the user’s endpoint is located. If the user’s external IP address doesn’t match any IP address that's defined in the trusted list, the endpoint is classified as being at an unknown location and any PSTN calls to or from a user who is enabled for Location-Based Routing are blocked.
