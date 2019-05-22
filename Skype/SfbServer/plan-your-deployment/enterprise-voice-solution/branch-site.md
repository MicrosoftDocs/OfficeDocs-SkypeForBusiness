---
title: "Branch site SIP trunking in Skype for Business Server"
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
ms.assetid: c4d9dfcd-8baa-41ea-9677-48b0e429429d
description: "Learn about SIP trunking at branch sites in Skype for Business Server Enterprise Voice."
---

# Branch site SIP trunking in Skype for Business Server
 
Learn about SIP trunking at branch sites in Skype for Business Server Enterprise Voice.
  
In some cases, you may need to implement distributed SIP trunking at selected branch sites. To determine whether a SIP trunk is needed for a branch site, and for details about the supported topology options for deploying SIP trunks in branch sites, see [SIP trunking in Skype for Business Server](sip-trunking.md).
  
## Example Branch Site SIP Trunk Requirements Analysis

When you decide to deploy a branch site SIP trunk, you need to perform a site-specific cost analysis. For example, an enterprise that has a central site in Redmond, Washington, and a branch site in New York, should do an analysis to determine whether to implement a SIP trunk from the New York site to a local service provider.
  
To determine whether a distributed SIP trunk in New York is cost-effective, identify which Direct Inward Dialing (DID) numbers will use the SIP trunk, and analyze the number of calls New York makes to areas other than Redmond (425). You can have DID termination for the branch site at the central site. For example, the Redmond central site can host DID numbers for the New York branch site. If the cost of implementing a distributed SIP trunk is less than the cost of those calls, consider implementing a SIP trunk at the New York branch site. 
  
## Other Branch Site SIP Trunk Requirements

The choice between a deploying a SIP trunk instead of a gateway is based on the difference between the public switched telephone network (PSTN) long distance toll charges of each option. If you deploy a branch site SIP trunk, you also need to determine your resiliency and bandwidth requirements. If the link between your branch site and central site is resilient and has sufficient bandwidth, you can deploy a SIP trunk or a gateway. You do not need to deploy a Survivable Branch Appliance at the branch site. If the link between your branch site and central site is not resilient, deploy a Survivable Branch Appliance, or deploy a Survivable Branch Server with either a gateway or SIP trunk at the branch site. 
  

