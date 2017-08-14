---
title: Configure media bypass in Skype for Business Server 2015 to always bypass the Mediation Server
ms.prod: SKYPEFORBUSINESS
ms.assetid: 370c4f54-e520-4d77-96a3-84c5e84a9996
---


# Configure media bypass in Skype for Business Server 2015 to always bypass the Mediation Server
[]Enable media bypass to always bypass the Mediation Server in Skype for Business Server Enterprise Voice. 
 If you use the steps in this topic to configure global settings for media bypass, the assumption is that you have good connectivity between Skype for Business endpoints and any peer for which you configured media bypass on the trunk connection.
  
    
    

If you do not have good connectivity between Skype for Business endpoints and all peers to the Mediation Server whose respective trunk connections have been enabled for media bypass, you must configure global media bypass settings to use site and region information when employing media bypass. This allows for more control in determining when media bypasses the Mediation Server. To do this, use the steps in  [Configure media bypass global settings in Skype for Business Server 2015 to use site and region information](configure-media-bypass-global-settings-in-skype-for-business-server-2015-to-use.md) and [Associate a subnet with a network site](deploy-network-regions-sites-and-subnets-in-skype-for-business-2015.md#BKMK_AssociateSubnets) instead.
### To Enable Media Bypass Globally to Always Bypass the Mediation Server


1. Open Skype for Business Server Control Panel.
    
  
2. In the left navigation bar, click **Network Configuration**.
    
  
3. Double-click the **Global** configuration in the list.
    
  
4. On the **Edit Global Setting** page, select the **Enable media bypass** check box.
    
  
5. Click **Always bypass**.
    
  
6. Click **Commit**.
    
  

## See also


#### 


  
    
    
 [Plan for media bypass in Skype for Business 2015](plan-for-media-bypass-in-skype-for-business-2015.md)
  
    
    
 [Deploy media bypass in Skype for Business Server 2015](deploy-media-bypass-in-skype-for-business-server-2015.md)
