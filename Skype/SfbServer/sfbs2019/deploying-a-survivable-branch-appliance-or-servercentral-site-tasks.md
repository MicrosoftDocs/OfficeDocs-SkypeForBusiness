---
title: "Deploying a Survivable Branch Appliance or Server with Lync Server 2013 - central site tasks"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 0f631a36-fc2e-41cd-8a0d-f27e84f4a89e
description: "Complete the tasks in this section at the central site. If you're deploying a Survivable Branch Server, skip the first task."
---

# Deploying a Survivable Branch Appliance or Server with Lync Server 2013 - central site tasks
[]
Complete the tasks in this section at the central site. If you're deploying a Survivable Branch Server, skip the first task.
  
> [!IMPORTANT]
>  Before you perform the tasks in this section, the following conditions must be in place: >  Lync Server must be set up at the central site. >  An installation technician at the branch site must be added to the RTCUniversalSBATechnicians group. >  In addition, we recommend that you do the following: >  Deploy a DHCP server at each branch site to enable clients to obtain IP addresses. >  As an alternative to deploying a DHCP server at each branch site, enable Lync Server DHCP on the Survivable Branch Appliance or Survivable Branch Server by using the Lync Server Management Shell cmdlet **Set-CsRegistrarConfiguration -EnableDHCPServer $true**. For details, see the "Hardware and Software Requirements" section of [Branch-site resiliency requirements for Lync Server 2013](branch-site-resiliency-requirements.md) in the Planning documentation. 
  
## In this section

- [Add a Survivable Branch Appliance to Active Directory in Lync Server 2013](add-a-survivable-branch-appliance-to-active-directory.md)
    
- [Add branch sites to your topology in Lync Server 2013](add-branch-sites-to-your-topology.md)
    
- [Define a Survivable Branch Appliance or Server in Lync Server 2013](define-a-survivable-branch-appliance-or-server.md)
    

