---
title: "Change an existing archiving policy in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 4cf600be-ba3d-4bce-aa22-e158b9ccf8a9
description: "Summary: Learn how to change user archiving policies for Skype for Business Server."
---

# Change an existing archiving policy in Skype for Business Server
 
**Summary:** Learn how to change user archiving policies for Skype for Business Server.
  
When you first deploy Skype for Business Server, you set up initial archiving policies that determine how archiving is implemented for the users in your deployment. This topic describes how to manage and amend policies. 
  
## Change archiving policies by using the Control Panel

1. From a user account that is assigned to the CsArchivingAdministrator or CsAdministrator role, log on to any computer in your internal deployment. 
    
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 
    
3. In the left navigation bar, click **Monitoring and Archiving**, and then click **Archiving Policy**.
    
4. In the list of policies, do one of the following: 
    
   - To change the policy for your entire deployment, click **Global** in the list of policies, click **Edit**, and then click **Show details**.
    
   - To change the policy for a single site, click the site name in the list of policies, click **Edit**, and then click **Show details**.
    
   - To change the policy for a single user or user group, click the user or user group name in the list of policies, click **Edit**, and then click **Show details**.
    
5. On the **Edit Archiving Policy** page, do the following:
    
   - To enable or disable internal archiving for the policy, select or clear the **Archive internal communications** check box.
    
   - To enable or disable external archiving for the policy, select or clear the **Archive external communications** check box.
    
6. Click **Commit**.
    
    > [!IMPORTANT]
    > The settings of a user policy only apply to the specific users and user groups to which you apply the policy. For details, see [Apply an archiving policy to users in Skype for Business Server](apply-a-policy-to-users.md). 
  
## Change archiving policies by using Windows PowerShell

You can also change archiving policies by using the Windows PowerShell **Set-CsArchivingPolicy** cmdlet.
  
### Enable archiving policies

To enable the archiving of internal communication sessions, set the value of the ArchiveInternal parameter to True ($True): 
  
```
Set-CsArchivingPolicy -Identity "global" -ArchiveInternal $True
```

To enable the archiving of external communication sessions, set the value of the ArchiveExternal parameter to True ($True): 
  
```
Set-CsArchivingPolicy -Identity "global" -ArchiveExternal $True
```

To enable the archiving of both internal and external communication sessions, set the value of both the ArchiveInternal and ArchiveExternal parameters to True: 
  
```
Set-CsArchivingPolicy -Identity "global" -ArchiveInternal $True -ArchiveExternal $True
```

### Disable archiving policies

To disable archiving altogether, set the value of both the ArchiveInternal and ArchiveExternal parameters to False ($False): 
  
```
Set-CsArchivingPolicy -Identity "global" -ArchiveInternal $False -ArchiveExternal $False
```
