---
title: Modify conferencing policies in Skype for Business Server 2015
ms.prod: SKYPEFORBUSINESS
ms.assetid: b40ba905-e74a-4456-ac94-65471bc2d66d
---


# Modify conferencing policies in Skype for Business Server 2015
[] **Summary:** Learn how to modify conferencing policies in Skype for Business Server 2015.
You can modify conferencing policies by using Skype for Business Server Control Panel or by using Skype for Business Server Management Shell.
  
    
    


## Modify conferencing policies by using Skype for Business Server Control Panel


1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
  
2.  Open Skype for Business Server Control Panel.
    
  
3. In the left navigation bar, click **Conferencing**, and then click **Conferencing Policy**.
    
  
4. In the list of conferencing policies, click the policy that you want to change, click **Edit**, and then click **Show details**.
    
  
5. In **Edit Conferencing Policy**, modify any of the policy settings, except for the policy name, which cannot be modified.
    
  
6. Click **Commit**.
    
  

## Modify conferencing policies by using Skype for Business Server Management Shell

To modify conferencing policies, use the **Set-CsConferencingPolicy** cmdlet.
  
    
    
The following example modifies a property value of the conferencing policy SalesConferencingPolicy. The command sets the value of the AllowConferenceRecording property to False:
  
    
    



```

Set-CsConferencingPolicy -Identity SalesConferencingPolicy -AllowConferenceRecording $False
```

For more information, including complete syntax and a list of parameters, see  [Set-CsConferencingPolicy](set-csconferencingpolicy.md).
  
    
    

