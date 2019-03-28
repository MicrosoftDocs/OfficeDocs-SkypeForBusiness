---
title: "Delete an existing archiving policy in Skype for Business Server"
ms.reviewer: 
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 8b88bed9-2b37-4caf-b119-48688076e06a
description: "Summary: Learn how to delete an archiving policy for Skype for Business Server."
---

# Delete an existing archiving policy in Skype for Business Server

**Summary:** Learn how to delete an archiving policy for Skype for Business Server.
  
You can delete a user policy or site policy, but not the global policy. If you delete the global policy, Skype for Business Server automatically resets the policy to the default values.
  
## Delete a policy by using the Control Panel

1. From a user account that is assigned to the CsArchivingAdministrator or CsAdministrator role, log on to any computer in your internal deployment. 
    
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 
    
3. In the left navigation bar, click **Monitoring and Archiving**, and then click **Archiving Policy**.
    
4. In the list of archiving policies, click the user or site policy that you want to delete, click **Edit**, and then click **Delete**.
    
5. Click **Commit**.
    
## Delete a policy by using Windows PowerShell

You can also delete archiving policies by using the **Remove-CsArchivingPolicy** cmdlet.
  
For example, the following command deletes the policy with the Identity site:Redmond. When a policy configured at the site level is deleted, users previously managed by the site policy will automatically be governed by the global archiving policy instead:
  
```
Remove-CsArchivingPolicy -Identity site:Redmond
```

This command removes all the archiving policies applied to the per-user level:
  
```
Get-CsArchivingPolicy -Filter "tag:*" | Remove-CsArchivingPolicy
```

This command removes all the archiving policies where internal archiving has been disabled:
  
```
Get-CsArchivingPolicy | Where-Object {$_.ArchiveInternal -eq $False} | Remove-CsArchivingPolicy
```

For more information, see the help topic for the [Remove-CsArchivingPolicy](https://docs.microsoft.com/powershell/module/skype/remove-csarchivingpolicy?view=skype-ps) cmdlet.
