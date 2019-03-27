---
title: "Delete conferencing policies in Skype for Business Server"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 497e6ca0-7a49-4f3e-9804-14414cf87b57
description: "Summary: Learn how to delete conferencing policies in Skype for Business Server."
---

# Delete conferencing policies in Skype for Business Server
 
**Summary:** Learn how to delete conferencing policies in Skype for Business Server.
  
You can delete conferencing policies by using Skype for Business Server Control Panel or by using Skype for Business Server Management Shell.
  
## Delete conferencing policies by using Skype for Business Server Control Panel

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2.  Open Skype for Business Server Control Panel.
    
3. In the left navigation bar, click **Conferencing**, and then click **Conferencing Policy**.
    
4. In the list of conferencing policies, click the site or user policy that you want to delete, click **Edit**, and then click **Delete**.
    
## Delete conferencing policies by using Skype for Business Server Management Shell

To delete conferencing policies, use the **Remove-CsConferencingPolicy** cmdlet.
  
The following command removes the conferencing policy with the Identity RedmondConferencingPolicy:
  
```
Remove-CsConferencingPolicy -Identity "RedmondConferencingPolicy"
```

The next command deletes any conferencing policies that allow external users to record the conference:
  
```
Get-CsConferencingPolicy | Where-Object {$_.AllowExternalUsersToRecordMeetings -eq $True} | Remove-CsConferencingPolicy
```

For more information, including complete syntax and a list of parameters, see [Remove-CsConferencingPolicy](https://docs.microsoft.com/powershell/module/skype/remove-csconferencingpolicy?view=skype-ps).
  

