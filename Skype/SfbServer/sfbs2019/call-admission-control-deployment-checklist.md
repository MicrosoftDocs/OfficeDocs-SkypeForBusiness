---
title: "Call admission control deployment checklist for Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d56a525f-3da5-4ac0-a311-0c5efd98c9df
description: "Use the following checklist to verify that you have completed all the necessary configuration tasks to deploy call admission control (CAC)."
---

# Call admission control deployment checklist for Lync Server 2013
[]
Use the following checklist to verify that you have completed all the necessary configuration tasks to deploy call admission control (CAC).
  
- If one or more Edge Servers are deployed, each external interface IP address must be added to the subnet list in the network configuration settings, with a bit mask of 32. You should also associate this subnet (IP address) with the network site ID for the geographic location where the A/V Edge service is deployed.
    
    > [!NOTE]
    > Edge servers are not required to implement CAC. 
  
- Make sure that CAC is enabled, either through Lync Server Control Panel or by running the cmdlet as specified in [Enable call admission control in Lync Server 2013](enable-call-admission-control.md).
    
- Make sure that CAC is enabled in all central sites. This can be done through the Topology Builder. If a warning is generated when you publish,  *do not*  ignore it. 
    
- Make sure that all the subnets that are managed in the enterprise network are configured in the network configuration settings. It is also essential that every subnet be associated to a network site, as explained in [Associate a subnet with a network site in Lync Server 2013](associate-a-subnet-with-a-network-site.md).
    
- Make sure that the subnet or IP addresses of all Front End Servers, Survivable Branch Appliances (SBAs), Audio/Video Conferencing Servers (if in a separate pool), and Mediation Servers are configured in the network configuration settings.
    

