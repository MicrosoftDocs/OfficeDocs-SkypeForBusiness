---
title: "Plan for Enterprise Voice in Skype for Business Server"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom:
ms.assetid: fd8d5867-0ac9-47f8-94f0-1c3ee5e25575
description: "Enterprise Voice planning basics in Skype for Business Server, including sites, regions, network links between sites, and estimating voice usage traffic."
---

# Plan for Enterprise Voice in Skype for Business Server
 
Enterprise Voice planning basics in Skype for Business Server, including sites, regions, network links between sites, and estimating voice usage traffic.
  
The deployment process for Enterprise Voice depends on your existing topology, infrastructure, and the Enterprise Voice functionality that you want to support. The required procedures will depend on what features you choose, but there are other planning considerations that you must make at a high level.
  
In general, consider the type and number of sites that you want to deploy and their geographical locations, the call volume at each site, the types of network links that connect sites, whether you want to provide redundancy and failover for voice functionality for each site, and whether you want to use existing PBX equipment. There are certain considerations, such as high availability, that you should consider when you plan for Skype for Business Server as a whole. These considerations are discussed in topics throughout this section, as needed.
  
## Sites and regions

First, identify the sites in your topology where you will deploy Enterprise Voice and the network regions to which those sites belong. In particular, consider how you will provide public switched telephone network (PSTN) connectivity to each site. For manageability and logistical reasons, the regions to which these sites belong can be a deciding factor. Decide where gateways will be deployed locally, where Survivable Branch Appliances (SBAs) will be deployed, and where you can configure SIP trunks (either locally or at the central site) to an Internet telephony service provider (ITSP).
  
## Network links between sites

You also need to consider the bandwidth usage that you expect on the network links between your central site and its branch sites. If you have, or plan to deploy, resilient WAN links between sites, we recommend that you deploy a gateway at each branch site to provide local direct inward dial (DID) termination for users at those sites. If you have resilient WAN links, but the bandwidth on a WAN link is likely to be constrained, configure call admission control for that link. If you do not have resilient WAN links, host fewer than 1000 users at your branch site, and do not have local trained Skype for Business Server administrators available, we recommend that you deploy a Survivable Branch Appliance at the branch site. If you host between 1000 and 5000 users at your branch site, lack a resilient WAN connection, and have trained Skype for Business Server administrators available, we recommend that you deploy a Survivable Branch Server with a small gateway at the branch site. Consider also enabling media bypass on constrained links if you have a gateway peer that supports media bypass.
  
## Estimating voice usage and traffic

The Microsoft Lync Server 2013, Planning Tool uses the following metric to estimate user traffic at each site and the number of ports that are required to support that traffic.
  
> For **Light traffic** (one PSTN call per user per hour), figure 15 users per port.
> 
> For **Medium traffic** (2 PSTN calls per user per hour), figure 10 users per port.
> 
> For **Heavy traffic** (3 or more PSTN per user calls per hour), figure 5 users per port.
    
The number of ports in turn determines the number of Mediation Servers and gateways that will be required. The public switched telephone network (PSTN) gateways that most organizations consider deploying range in size from 2 ports to as many as 960 ports. (There are even larger gateways, but these are used mainly by telephony service providers.)
  
For example, an organization with 10,000 users and medium traffic would require 1000 ports. The number of gateways required would equal the total number of ports required as determined by the total capacity of the gateways.
  
## Components, features, and options of Enterprise Voice

See the following sections for more information on planning your Enterprise Voice deployment.
  
- [Components required for Enterprise Voice in Skype for Business Server](components-required-for-enterprise-voice.md)
    
- [Plan for PSTN connectivity in Skype for Business Server](pstn-connectivity-0.md)
    
- [Network settings for the advanced Enterprise Voice features in Skype for Business Server](network-settings-for-advanced-features.md)
    
- [Plan for call admission control in Skype for Business Server](call-admission-control.md)
    
- [Plan for emergency services in Skype for Business Server](emergency-services.md)
    
- [Plan for media bypass in Skype for Business](media-bypass.md)
    
- [Plan for private telephone lines with Skype for Business](private-telephone-lines.md)
    
- [Plan for Location-Based Routing in Skype for Business](location-based-routing.md)
    
- [Plan for call management features in Skype for Business](call-management-features.md)
    
- [Plan for Enterprise Voice resiliency in Skype for Business Server](enterprise-voice-resiliency.md)
    

