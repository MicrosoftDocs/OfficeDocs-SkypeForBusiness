---
title: "Configure media bypass in Skype for Business Server to always bypass the Mediation Server"
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
ms.assetid: 370c4f54-e520-4d77-96a3-84c5e84a9996
description: "Enable media bypass to always bypass the Mediation Server in Skype for Business Server Enterprise Voice."
---

# Configure media bypass in Skype for Business Server to always bypass the Mediation Server
 
Enable media bypass to always bypass the Mediation Server in Skype for Business Server Enterprise Voice. 
  
 If you use the steps in this topic to configure global settings for media bypass, the assumption is that you have good connectivity between Skype for Business endpoints and any peer for which you configured media bypass on the trunk connection.
  
If you do not have good connectivity between Skype for Business endpoints and all peers to the Mediation Server whose respective trunk connections have been enabled for media bypass, you must configure global media bypass settings to use site and region information when employing media bypass. This allows for more control in determining when media bypasses the Mediation Server. To do this, use the steps in [Configure media bypass global settings in Skype for Business Server to use site and region information](use-site-and-region-information.md) and [Associate a subnet with a network site](deploy-network.md#BKMK_AssociateSubnets) instead.
  
### To Enable Media Bypass Globally to Always Bypass the Mediation Server

1. Open Skype for Business Server Control Panel.
    
2. In the left navigation bar, click **Network Configuration**.
    
3. Double-click the **Global** configuration in the list.
    
4. On the **Edit Global Setting** page, select the **Enable media bypass** check box.
    
5. Click **Always bypass**.
    
6. Click **Commit**.
    
## See also

[Plan for media bypass in Skype for Business](../../plan-your-deployment/enterprise-voice-solution/media-bypass.md)
  
[Deploy media bypass in Skype for Business Server](deploy-media-bypass.md)

