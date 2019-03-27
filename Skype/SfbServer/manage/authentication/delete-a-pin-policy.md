---
title: "Delete a PIN policy in Skype for Business Server"
ms.reviewer: 
ms.author: heidip
author: microsoftheidi
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: 7c378927-2e41-418e-9721-327021bd2e45
description: "Summary: Delete a user's dial-in conferencing PIN for Skype for Business Server."
---

# Delete a PIN policy in Skype for Business Server
 
**Summary:** Delete a user's dial-in conferencing PIN for Skype for Business Server.
  
Follow these steps to delete a personal identification number (PIN) policy.
  
> [!NOTE]
> You cannot delete the global PIN policy. 
  
### To delete a PIN policy in Skype for Business Server Control Panel

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Skype for Business Server.
    
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel.  
    
3. In the left navigation bar, click **Security** and then click **PIN Policy**.
    
4. On the **PIN Policy** page, and in the search field, type all or part of the name of the policy you want to delete.
    
5. In the list of policies, click the policy that you want, click **Edit**, and then click **Delete**.
    
6. Click **OK**.
    
## Removing PIN Policies by Using Windows PowerShell Cmdlets

You can delete PIN policies by using Windows PowerShell and the Remove-CsPinPolicy cmdlet. You can run this cmdlet either from the Skype for Business Server Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Skype for Business Server, see the blog article ["Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell"](https://go.microsoft.com/fwlink/p/?linkId=255876). The process is the same in Skype for Business Server.
  
### To remove a specific PIN policy

- This command removes the PIN policy with the Identity RedmondPinPolicy:
    
  ```
  Remove-CsPinPolicy -Identity "RedmondPinPolicy"
  ```

### To remove all the PIN policies applied to the site scope

- This command removes all the PIN policies configured at the site scope:
    
  ```
  Get-CsPinPolicy -Filter "site:*" | Remove-CsPinPolicy
  ```

### To remove all the PIN policies that allow the use of common patterns

- And this one removes all the PIN policies that allow the use of common patterns:G
    
  ```
  et-CsPinPolicy | Where-Object {$_.AllowCommonPatterns -eq $True} | Remove-CsPinPolicy
  ```

For more information, see the help topic for the [Remove-CsPinPolicy](https://docs.microsoft.com/powershell/module/skype/remove-cspinpolicy?view=skype-ps) cmdlet.
  

