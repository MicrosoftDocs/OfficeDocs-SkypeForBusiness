---
title: "Delete an existing conferencing policy in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 709ed771-790f-4bf1-a4de-b37ca5168688
description: "Follow these steps to delete a user-level or a site-level conferencing policy."
---

# Delete an existing conferencing policy in Lync Server 2013
[]
Follow these steps to delete a user-level or a site-level conferencing policy.
  
> [!NOTE]
> You cannot delete the global conferencing policy. 
  
### To delete a site or user conferencing policy

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Conferencing** and then click **Conferencing Policy**.
    
4. In the list of conferencing policies, click the site or user policy that you want to delete, click **Edit**, and then click **Delete**.
    
## Removing Conferencing Policies by Using Windows PowerShell Cmdlets

You can delete conferencing policies by using Lync Server Management Shell and the **Remove-CsConferencingPolicy** cmdlet. You can run this cmdlet from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876).
  
### To remove a specified conferencing policy

- The following command removes the conferencing policy with the Identity RedmondConferencingPolicy:
    
  ```
  Remove-CsConferencingPolicy -Identity "RedmondConferencingPolicy"
  ```

### To remove all of the conferencing policies applied to the per-user scope

- The following command removes all the conferencing policies configured at the per-user scope:
    
  ```
  Get-CsConferencingPolicy -Filter "tag:*" | Remove-CsConferencingPolicy
  ```

### To remove all of the conferencing polices that allow recording by external users

- The following command deletes any conferencing policies that allow external users to record the conference:
    
  ```
  Get-CsConferencingPolicy | Where-Object {$_.AllowExternalUsersToRecordMeetings -eq $True} | Remove-CsConferencingPolicy
  ```

For details, see [Remove-CsConferencingPolicy](remove-csconferencingpolicy.md).
  

