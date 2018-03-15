---
title: "About network regions, sites, and subnets in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6662123a-d011-408c-a290-92b2a8589943
description: "The advanced Enterprise Voice features described in this section share certain configuration requirements for network regions, network sites, and subnets. For example, all three advanced features require that each subnet in your topology be associated with a specific network site, and each network site must be associated with a network region."
---

# About network regions, sites, and subnets in Lync Server 2013
[]
The advanced Enterprise Voice features described in this section share certain configuration requirements for network regions, network sites, and subnets. For example, all three advanced features require that each subnet in your topology be associated with a specific network site, and each network site must be associated with a network region.
  
> [!IMPORTANT]
> Before you begin network configuration for call admission control, E9-1-1, or media bypass, make sure that you reviewed additional information about network settings in the [Network settings for the advanced Enterprise Voice features in Lync Server 2013](network-settings-for-the-advanced-enterprise-voice-features.md) topic in the Planning documentation. For details about network configuration primarily about call admission control, also see [Defining your requirements for call admission control in Lync Server 2013](defining-your-organization-s-requirements-for-call-admission-control.md) in the Planning documentation. 
  
Call admission control and E9-1-1 have additional configuration requirements for network sites:
  
- Call admission control requires that a bandwidth policy profile be specified for each site that is constrained by WAN bandwidth limitations. If you plan to deploy call admission control, you must [Create bandwidth policy profiles in Lync Server 2013](create-bandwidth-policy-profiles.md) before you configure your network sites. 
    
- E9-1-1 requires that a location policy be specified for each site. If you plan to deploy E9-1-1, you must [Create location policies in Lync Server 2013](create-location-policies.md) before you configure your network sites. 
    
## Create or Modify Network Regions, Network Sites, and Subnets

The following topics provide steps to create or modify network regions and network sites, and to associate subnets with network sites. These topics are not specific to any particular advanced Enterprise Voice feature.
  
- [Create or modify a network region in Lync Server 2013](create-or-modify-a-network-region.md)
    
- [Create or modify a network site in Lync Server 2013](create-or-modify-a-network-site.md)
    
- [Associate a subnet with a network site in Lync Server 2013](associate-a-subnet-with-a-network-site.md)
    

