---
title: "Delete a site or user policy for external user access in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6d907507-825b-4354-9c03-337a459f72de
description: "You can delete any site or user policy that is listed in Lync Server Control Panel on the External Access Policy page. Deleting the global policy does not actually delete it, but only resets it to the default settings, which do not include support for any external user access options. For details about resetting the global policy, see Reset the global policy for external user access in Lync Server 2013."
---

# Delete a site or user policy for external user access in Lync Server 2013
[]
You can delete any site or user policy that is listed in Lync Server Control Panel on the **External Access Policy** page. Deleting the global policy does not actually delete it, but only resets it to the default settings, which do not include support for any external user access options. For details about resetting the global policy, see [Reset the global policy for external user access in Lync Server 2013](reset-the-global-policy-for-external-user-access.md).
  
### To delete a site or user policy for external user access

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment. 
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. Click **External User Access**, click **External Access Policy**.
    
4. On the **External Access Policy** tab, click the site or user policy you want to delete, click **Edit**, and then click **Delete**.
    
5. When prompted to confirm the deletion, click **OK**.
    
## Removing PIN Policies by Using Windows PowerShell Cmdlets

External access policies can be deleted by using Windows PowerShell and the Remove-CsExternalAccessPolicy cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876).
  
### To remove a specific external access policy

- This command removes the external access policy applied to the Redmond site:
    
  ```
  Remove-CsExternalAccessPolicy -Identity "site:Redmond"
  ```

### To remove all the external access policies applied to the per-user scope

- This command removes all the external access policies configured at the per-user scope:
    
  ```
  Get-CsExternalAccessPolicy -Filter "tag:*" | Remove-CsExternalAccessPolicy
  ```

### To remove all the external access policies where outside user access is disabled

- This command deletes all the external access policies where outside user access has been disabled:
    
  ```
  Get-CsExternalAccessPolicy | Where-Object {$_.EnableOutsideAccess -eq $False} | Remove-CsExternalAccessPolicy
  ```

For more information, see the help topic for the [Remove-CsExternalAccessPolicy](remove-csexternalaccesspolicy.md) cmdlet. 
  

