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

Learn about network regions, network sites, network subnets, and trusted IP addresses. These terms and concepts are used throughout our cloud voice documentation for [Location-Based Routing for Direct Routing](location-based-routing-plan.md) and [dynamic emergency calling](configure-dynamic-emergency-calling.md). If you're deploying these cloud features in your organization, you must configure network settings for use with these features in Microsoft Teams.

This article gives you an overview of the network settings that are common to Location-Based Routing and enhanced emergency services. Depending on the cloud voice feature and capability that you're deploying, you configure some or all these settings. For steps on how to configure these settings, see [Manage your network topology for cloud features in Teams](manage-your-network-topology.md).

> [!NOTE]
> Any feature-specific requirements for network settings are documented in the configuration topics for that feature.

## Network region

A network region contains a collection of network sites. It interconnects various parts of a network across multiple geographic areas. For example, if your organization has many sites located in India, you may choose to designate “India” as a network region. Each network site must be associated with a network region.

The same network regions are shared by Location-Based Routing for Direct Routing and enhanced emergency services. If you already created network regions for one feature, you don't have to create new network regions for the other feature.

## Network site

A network site represents a location where your organization has a physical venue, such as an office, a set of buildings, or a campus. Network sites are defined as a collection of IP subnets. Each network site must be associated with a network region.

You can also use network sites to enable and configure emergency calling.

## Network subnet

Each subnet must be associated with a specific network site. A client's location is determined based on the network subnet and the associated network site. You can associate multiple subnets with the same network site but you can't associate multiple sites with the same subnet.

Subnet information is used to determine the network site on which an endpoint is located when a new session is initiated. When the location of each party in a session is known, the cloud voice feature can apply that information to determine how to handle call setup or routing.

For each network site, work with your network admin to determine which IP subnets are assigned to each network site. For example, the New York site in the North America region can be assigned the following IP subnets: 172.29.80.0/23, 157.57.216.0/25, 172.29.91.0/23, 172.29.81.0/24. If Bob, who usually works in Detroit, travels to the New York office for training, turns on his computer and connects to the network, his computer will get an IP address in one of the four ranges that are allocated for New York, for example, 172.29.80.103.

## Trusted IP address

Trusted IP addresses are the internet external IP addresses of the enterprise network. They determine whether the user’s endpoint is inside the corporate network before checking for a specific site match.

If the user’s external IP address matches an IP address that's in the trusted IP address list, the cloud voice feature checks to determine the internal subnet where the user’s endpoint is located. A match can be made against either IPv4 or IPv6 IP addresses and is dependent upon the format of the IP packet sent to the network settings. (If a public IP address has both IPv4 and IPv6, you must add both as trusted IP addresses.)

If the user’s external IP address doesn’t match an IP address that's in the trusted IP address list, the endpoint is classified as being at an unknown location.
