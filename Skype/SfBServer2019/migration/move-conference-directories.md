---
title: "Move Conference Directories"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "Before decommissioning a pool you must perform the following procedure for each conference directory in your legacy pool."
---

# Move Conference Directories

Before decommissioning a pool, you must perform the following procedure for each conference directory in your legacy pool.
  
### To Move a Conference Directory to Skype for Business Server 2019

1. Open the Skype for Business Server Management Shell.
    
2. To obtain the identity of the conference directories in your organization, run the following command:
    
   ```
   Get-CsConferenceDirectory
   ```

    The preceding command returns all the conference directories in your organization. Because of that, you might want to limit the results to the pool being decommissioned. For example, if you are decommissioning the pool with the fully qualified domain name (FQDN) pool01.contoso.net, use this command to limit the returned data to conference directories from that pool:
    
   ```
   Get-CsConferenceDirectory | Where-Object {$_.ServiceID -match "pool01.contoso.net"}
   ```

    That command returns only the conference directories where the ServiceID property contains the FQDN pool01.contoso.net.
    
3. To move conference directories, run the following command for each conference directory in the pool:
    
   ```
   Move-CsConferenceDirectory -Identity <Numeric identity of conference directory> -TargetPool <FQDN of pool where ownership is to be transitioned>
   ```

    For example, to move conference directory 3, use this command, specifying a Skype for Business Server 2019 pool as the TargetPool:
    
   ```
   Move-CsConferenceDirectory -Identity 3 -TargetPool "pool02.contoso.net"
   ```

    If you want to move all the conference directories on a pool, use a command similar to the following:
    
   ```
   Get-CsConferenceDirectory | Where-Object {$_.ServiceID -match "pool01.contoso.net"} | Move-CsConferenceDirectory -TargetPool "pool02.contoso.net"
   ```

Download [Uninstalling Microsoft legacy and Removing Server Roles](https://go.microsoft.com/fwlink/p/?linkId=246227) for comprehensive, step-by-step instructions on decommissioning legacy pools.
  
When moving conference directories, you might encounter the following error:
  
```
WARNING: Move operation failed for conference directory with ID "5". Cannot perform a rollback because data migration might have already started. Retry the operation.
WARNING: Before using the -Force parameter, ensure that you have exported the conference directory data using DBImpExp.exe and imported the data on the target pool. Refer to the DBImpExp-Readme.htm file for more information.
Move-CsConferenceDirectory : Unable to cast COM object of type 'System._ComObject' to interface type 'Microsoft.Rtc.Interop.User.IRtcConfDirManagement'. 
This operation failed because the QueryInterface call on the COM component for the interface with SID '{4262B886-503F-4BEA-868C-04E8DF562CEB}' failed due to the following error: The specified module could not be found.
```

This error typically occurs when the Skype for Business Server Management Shell requires an updated set of Active Directory permissions in order to complete a task. To resolve the problem, close the current instance of the Management Shell, then open a new instance of the shell and re-run the command to move the conference directory.
  

