---
title: Cloud voice terminology
author: LanaChin
ms.author: v-lanac
manager: serdars
ms.topic: conceptual
ms.reviewer: roykuntz
ms.service: msteams
audience: admin
search.appverid: MET150
description: Learn terminology and concepts associated with cloud voice features including Location-Based Routing for Direct Routing and enhanced emergency services.
localization_priority: Normal
ms.collection: 
  - M365-voice
appliesto: 
  - Microsoft Teams
---

# Cloud voice terminology

> [!INCLUDE [Preview customer token](includes/preview-feature.md)]

Learn about network regions, network sites, network subnets, and trusted IP addresses. These terms and concepts are used throughout our cloud voice documentation for [Location-Based Routing for Direct Routing](../Lync/LyncServer/administering-servers-after-migration.md) and enhanced emergency services. If you're deploying any of these cloud voice features in your organization, you must configure network settings for use with these features in Microsoft Teams.

These cloud voice features have common configuration requirements for which you must create network regions, network sites, and subnets. For example, you must associate each network site in your topology with a network region and associate each subnet with a network site.

This article gives you an overview of the configuration requirements that are common to Location-Based Routing for Direct Routing and enhanced emergency services.

## Network region

A network region contains a collection of network sites. For example, if your organization has many sites located in India, you may choose to designate “India” as a network region.

## Network site

A network site represents a location where your organization has a physical venue, such as an office, a set of buildings, or a campus. Network sites are defined as a collection of IP subnets. A best practice for Location-Based Routing is to create a separate site for each location that has unique PSTN connectivity.  Each network site must be associated with a network region. You can create a site that's enabled for Location-Based Routing or a site that's not enabled for Location-Based Routing. For example, you may want to create a site that's not enabled for Location-Based Routing to allow users who are enabled for Location-Based Routing to make PSTN calls when they roam to that site. Note that network sites may also be used to enable and configure emergency calling.

## Network subnet

IP subnets at the location where Teams endpoints can connect to the network must be defined and associated to a defined network to enforce toll bypass. Multiple subnets may be associated with the same network site, but multiple sites may not be associated with a same subnet. This association of subnets enables Location-Based Routing to locate the endpoints geographically to determine whether a given PSTN call should be allowed. Both IPv6 and IPv4 subnets are supported. When determining whether a Teams endpoint is located at a site, Location-Based Routing first checks for a matching IPv6 address. If an IPv6 address isn't present, Location-Based Routing checks for an IPv4 address.

## Trusted external IP address

Trusted external IP addresses are the Internet external IP addresses of the enterprise network. They determine whether the user’s endpoint is inside the corporate network before checking for a specific site match. If the user’s external IP matches an IP address that's defined in the trusted list, Location-Based Routing checks to determine the internal subnet where the user’s endpoint is located. If the user’s external IP address doesn’t match any IP address that's defined in the trusted list, the endpoint is classified as being at an unknown location and any PSTN calls to or from a user who is enabled for Location-Based Routing are blocked. 

### Related topics
- [Plan Location-Based Routing for Direct Routing](location-based-routing-plan.md)
- [Configure network settings for Location-Based Routing](location-based-routing-configure-network-settings.md)
- [Enable Location-Based Routing for Direct Routing](location-based-routing-enable.md)
