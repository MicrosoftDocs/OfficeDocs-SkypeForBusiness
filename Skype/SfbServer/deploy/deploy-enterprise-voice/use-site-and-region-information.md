---
title: "Configure media bypass global settings in Skype for Business Server to use site and region information"
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
ms.assetid: 0a21cdf1-f350-49da-b346-70806f256bea
description: "Configure media bypass to be used for only certain sites and regions in Skype for Business Server Enterprise Voice."
---

# Configure media bypass global settings in Skype for Business Server to use site and region information
 
Configure media bypass to be used for only certain sites and regions in Skype for Business Server Enterprise Voice. 
  
 If you use the steps in this topic to configure global settings for media bypass, the assumption is that you do not have good connectivity between all Skype for Business endpoints and any peer for which you configured media bypass on the trunk connection.
  
> [!NOTE]
> Network region and network site information is shared between call admission control and media bypass advanced Enterprise Voice features when both are enabled. Therefore, if you have already configured call admission control, you are not required to use the following procedure to edit the site and region information specifically for media bypass. Follow the steps in this procedure if you have not yet configured network regions and sites for call admission control, and you want to change media bypass settings. 
  
For media bypass to work properly there must be consistency between a site as defined in Topology Builder and as it is defined when you configure network regions and network sites. For example, if you have a branch site that you defined in Topology Builder as having only a PSTN gateway deployed, then that branch site must be configured with an Enterprise Voice policy that enables branch site users to have their PSTN calls routed through the PSTN gateway at the branch site.
  
### To Configure Site and Region Information for Media Bypass

1. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel.  
    
2. In the left navigation bar, click **Network Configuration**.
    
3. Double-click the **Global** configuration in the table.
    
4. On the **Edit Global Setting** page, select the **Enable media bypass** check box.
    
5. Click **Use sites and region configuration**.
    
6. If necessary, select the **Enable bypass for non-mapped sites** check box.
    
    > [!NOTE]
    > Select this check box only if you have one or more large sites associated with the same region that do not have bandwidth constraints (for example, a large central site), but you also have some branch sites associated with the same region that do have bandwidth constraints. When you enable bypass for non-mapped sites, configuration is streamlined in that you specify only the subnets associated with the branch sites, rather than needing to specify all subnets associated with all sites. We recommend that you do not select this check box if call admission control is enabled. 
  
7. Click **Commit**.
    
Next, add subnets to the network site, as described in [Associate a subnet with a network site](deploy-network.md#BKMK_AssociateSubnets). After you associate all subnets with network sites, media bypass deployment is complete.
> [!IMPORTANT]
> If you have not already created network regions and network sites, you must first create those before you can proceed with media bypass deployment. For details, see [Deploy network regions, sites and subnets in Skype for Business](deploy-network.md). 
  
## See also

[Associate a subnet with a network site](deploy-network.md#BKMK_AssociateSubnets)

