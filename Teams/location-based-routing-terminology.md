---
title: Location-Based Routing terminology 
author: LanaChin
ms.author: v-lanac
manager: serdars
ms.date: 2/1/2019
ms.topic: conceptual
ms.reviewer: roykuntz
ms.service: msteams
search.appverid: MET150
description: Learn terminology and concepts associated with Location-Based Routing for Direct Routing.
localization_priority: Normal
ms.collection:  
- Teams_ITAdmin_Help
- M365-collaboration
- M365-voice
appliesto: 
- Microsoft Teams
---

# Location-Based Routing terminology

> [!INCLUDE [Preview customer token](includes/preview-feature.md)] 

Here are some terms and concepts that are used throughout the Location-Based Routing documentation. It's a good idea to be familiar with these terms and concepts before you get deeper into the documentation.

|Term  |Description  |
|---------|---------|
|Network regions     | A network region contains a collection of network sites. For example, if your organization has many sites located in India, you may choose to designate “India” as a network region.        |
|Network sites    | A network site represents a location where your organization has a physical venue, such as an office, a set of buildings, or a campus. Network sites are defined as a collection of IP subnets. A best practice for Location-Based Routing is to create a separate site for each location that has unique PSTN connectivity.  Each network site must be associated with a network region. You can create a site that's enabled for Location-Based Routing or a site that's not enabled for Location-Based Routing. For example, you may want to create a site that's not enabled for Location-Based Routing to allow users who are enabled for Location-Based Routing to make PSTN calls when they roam to that site. Note that network sites may also be used to enable and configure emergency calling.        |
|Network subnets     |IP subnets at the location where Teams endpoints can connect to the network must be defined and associated to a defined network to enforce toll bypass. Multiple subnets may be associated with the same network site, but multiple sites may not be associated with a same subnet. This association of subnets enables Location-Based Routing to locate the endpoints geographically to determine whether a given PSTN call should be allowed. Both IPv6 and IPv4 subnets are supported. When determining whether a Teams endpoint is located at a site, Location-Based Routing first checks for a matching IPv6 address. If an IPv6 address isn't present, Location-Based Routing checks for an IPv4 address. <br><br>Support for IPv6 is in progress and will be available by General Availability (GA) of Location-Based Routing.          |
|Trusted external IP addresses    |Trusted external IP addresses are the Internet external IP addresses of the enterprise network. They determine whether the user’s endpoint is inside the corporate network before checking for a specific site match. If the user’s external IP matches an IP address that's defined in the trusted list, Location-Based Routing checks to determine the internal subnet where the user’s endpoint is located. If the user’s external IP address doesn’t match any IP address that's defined in the trusted list, the endpoint is classified as being at an unknown location and any PSTN calls to or from a user who is enabled for Location-Based Routing are blocked.          |

### Related topics
- [Plan Location-Based Routing for Direct Routing](location-based-routing-plan.md)
- [Configure network settings for Location-Based Routing](location-based-routing-configure-network-settings.md)
- [Enable Location-Based Routing for Direct Routing](location-based-routing-enable.md)
