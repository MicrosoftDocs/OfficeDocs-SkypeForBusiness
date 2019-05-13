---
title: "Enable or disable archiving in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: d5aed328-e89d-4a7b-b603-15ae5c33c5dd
description: "Summary: Learn how to enable or disable archiving in Skype for Business Server."
---

# Enable or disable archiving in Skype for Business Server

**Summary:** Learn how to enable or disable archiving in Skype for Business Server.
  
## Enable or disable archiving by using the Control Panel

1. From a user account that is assigned to the CsArchivingAdministrator or CsAdministrator role, log on to any computer in your internal deployment. 
    
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 
    
3. In the left navigation bar, click **Monitoring and Archiving**, and then click **Archiving Configuration**.
    
4. Select the appropriate global, site, or pool configuration from the list of archiving configurations, click **Edit**, click **Show details**, and then do the following:
    
   - To enable archiving only for instant messaging (IM) sessions, click **Archive IM sessions**.
    
   - To enable archiving for both IM sessions and conferences, click **Archive IM and conferencing sessions**.
    
   - To disable archiving for the configuration, click **Disable archiving**.
    
5. Click **Commit**.
    
## Enable or disable archiving by using Windows PowerShell

You can also enable or disable archiving by using the **Set-CsArchivingConfiguration** cmdlet. For example, the following command modifies the all of the archiving configuration settings so that only IM sessions are archived. The command calls the **Get-CsArchivingConfiguration** cmdlet without any parameters in order to return all the archiving configuration settings currently in use in the organization. This collection is then piped to the **Where-Object** cmdlet, which selects only those settings where the EnableArchiving property is equal to (-eq) "ImAndWebConf". The filtered collection is then piped to the **Set-CsArchivingConfiguration** cmdlet, which takes each item in the collection and changes the value of EnableArchiving to "ImOnly":
  
```
Get-CsArchivingConfiguration | Where-Object {$_.EnableArchiving -eq "ImAndWebConf"} | Set-CsArchivingConfiguration -EnableArchiving "ImOnly"
```
