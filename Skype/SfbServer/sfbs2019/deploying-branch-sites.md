---
title: "Deploying branch sites in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 1475dee0-66ae-4ee5-b6f1-7409b4bbff45
description: "Branch site users get most of their Lync Server 2013 functionality from the server at the central site that the branch site is associated with. Each branch site is associated with exactly one central site. To provide calls to and from the public switched telephone network (PSTN), a branch site might contain any of the following:"
---

# Deploying branch sites in Lync Server 2013
[]
Branch site users get most of their Lync Server 2013 functionality from the server at the central site that the branch site is associated with. Each branch site is associated with exactly one central site. To provide calls to and from the public switched telephone network (PSTN), a branch site might contain any of the following:
  
- A PSTN gateway and possibly a Meditation Server
    
- A SIP trunk 
    
- An existing voice infrastructure with a private branch exchange (PBX)
    
- A Survivable Branch Appliance
    
- A Survivable Branch Server
    
Branch sites with a Survivable Branch Appliance or a Survivable Branch Server are more resilient in times of wide-area network or central site failures than branch sites without one of these solutions. For example, in a site with a Survivable Branch Appliance or a Survivable Branch Server deployed, users can still make and receive PSTN calls if the network connecting the branch site to the central site is down. Another way to achieve branch-site resiliency is by using a PSTN gateway or a SIP trunk with a full-scale Lync Server deployment at the branch site. 
  
For details about which branch site deployment is right for your organization, including prerequisites and other planning considerations, see [Planning for PSTN connectivity in Lync Server 2013](planning-for-pstn-connectivity.md) and [Planning for branch-site voice resiliency in Lync Server 2013](planning-for-branch-site-voice-resiliency.md) in the Planning documentation. 
  
## In this section

- [Providing PSTN connectivity at a branch site in Lync Server 2013](providing-pstn-connectivity-at-a-branch-site.md)
    
- [Deploying a Survivable Branch Appliance or Server with Lync Server 2013](deploying-a-survivable-branch-appliance-or-server.md)
    

