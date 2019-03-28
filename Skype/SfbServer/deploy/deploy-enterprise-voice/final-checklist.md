---
title: "Call admission control deployment final checklist for Skype for Business Server"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom: 
ms.assetid: d56a525f-3da5-4ac0-a311-0c5efd98c9df
description: "Final checklist for deploying Call Admission Control (CAC) in Skype for Business Server Enterprise Voice."
---

# Call admission control deployment: final checklist for Skype for Business Server
 
Final checklist for deploying Call Admission Control (CAC) in Skype for Business Server Enterprise Voice. 
  
Use the following checklist to verify that you have completed all the necessary configuration tasks to deploy Call Admission Control (CAC).
  
- If one or more Edge Servers are deployed, each external interface IP address must be added to the subnet list in the network configuration settings, with a bit mask of 32. You should also associate this subnet (IP address) with the network site ID for the geographic location where the A/V Edge service is deployed.
    
    > [!NOTE]
    > Edge Servers are not required to implement CAC. 
  
- Make sure that CAC is enabled, as specified in [Enable call admission control in Skype for Business Server](enable-call-admission-control.md).
    
- Make sure that CAC is enabled in all central sites. This can be done through the Topology Builder. If a warning is generated when you publish,  *do not*  ignore it.
    
- Make sure that all the subnets that are managed in the enterprise network are configured in the network configuration settings. It is also essential that every subnet be associated to a network site, as explained in [Deploy network regions, sites and subnets in Skype for Business](deploy-network.md).
    
- Make sure that the subnet or IP addresses of all Front End Servers, Survivable Branch Appliances (SBAs), Audio/Video Conferencing Servers (if in a separate pool), and Mediation Servers are configured in the network configuration settings.
    

