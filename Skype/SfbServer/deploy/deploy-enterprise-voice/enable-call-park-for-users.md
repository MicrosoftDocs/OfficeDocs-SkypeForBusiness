---
title: "Enable Call Park for users in Skype for Business"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom: 
ms.assetid: 9430763f-3394-467c-9c6d-426bf761604e
description: "Enable users for Call Park in Skype for Business Server Enterprise Voice."
---

# Enable Call Park for users in Skype for Business
 
Enable users for Call Park in Skype for Business Server Enterprise Voice.
  
By default, Call Park is disabled for all users. Users cannot park calls or retrieve parked calls until they are enabled for Call Park in voice policy.
  
You can enable Call Park at the global scope, or at the site scope or user scope. User scope takes precedence over site scope, and site scope takes precedence over global scope. If you have multiple voice policies, review all the policies to enable Call Park, not just the global policy.
  
### To Use Skype for Business Server Control Panel to Enable Call Park for Users

1. Log on to the computer as a member of the **RTCUniversalServerAdmins** group, or as a member of the **CsVoiceAdministrator**, **CsServerAdministrator**, or **CsAdministrator** administrative role.
    
2. Open Skype for Business Server Control Panel.
    
3. In the left navigation bar, click **Voice Routing**.
    
4. Click the **Voice Policy** tab.
    
5. Double-click an existing voice policy to open the **Edit Voice Policy** dialog box.
    
6. Under **Calling features**, select **Enable call park**.
    
7. Click **OK** to save the voice policy
    
### To Use Cmdlets to Enable Call Park for Users

1. Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator administrative role.
    
2. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.
    
3. Run:
    
   ```
   Set-CsVoicePolicy -Identity <VoicePolicy> -EnableCallPark $true
   ```

    For example, to enable Call Park for the default global voice policy:
    
   ```
   Set-CsVoicePolicy -EnableCallPark $true
   ```

## See also



[Create or modify a voice policy and configure PSTN usage records in Skype for Business](voice-policy-and-pstn-usage-records.md)

