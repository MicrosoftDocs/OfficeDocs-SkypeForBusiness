---
title: "Deleting an Archiving policy in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 4739a691-41cc-4128-8bb8-6d5a4c02107a
description: "You can delete a user policy or site policy. The global policy cannot be removed. If you try to delete the global policy, Lync Server 2013 automatically resets the policy to the default values."
---

# Deleting an Archiving policy in Lync Server 2013
[]
You can delete a user policy or site policy. The global policy cannot be removed. If you try to delete the global policy, Lync Server 2013 automatically resets the policy to the default values.
  
> [!NOTE]
> If you enabled Microsoft Exchange integration for your deployment, Exchange policies control whether archiving is enabled for the users who are homed on Exchange 2013 and have their mailboxes put on In-Place Hold. For details, see [Setting up policies for Archiving in Lync Server 2013 when using Exchange Server integration](setting-up-policies-for-archiving-when-using-exchange-server-integration.md) in the Deployment documentation. 
  
### To delete a user or site policy for archiving

1. From a user account that is assigned to the CsArchivingAdministrator or CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Monitoring and Archiving**, and then click **Archiving Policy**.
    
4. In the list of archiving policies, click the user or site policy that you want to delete, click **Edit**, and then click **Delete**.
    
5. Click **Commit**.
    
## Removing Archiving Policies by Using Windows PowerShell Cmdlets

Archiving policies can be deleted by using Windows PowerShell and the **Remove-CsArchivingPolicy** cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876).
  
### To remove a specified archiving policy

- As an example, **Remove-CsArchivingPolicy** deletes the policy with the Identity site:Redmond. Note that, when a policy configured at the site scope is deleted, users previously managed by the site policy will automatically be governed by the global archiving policy instead. The following command removes the archiving applied to the Redmond site: 
    
  ```
  Remove-CsArchivingPolicy -Identity site:Redmond
  ```

### To remove all the archiving policies applied to the per-user scope

- This command removes all the archiving policies applied to the per-user scope:
    
  ```
  Get-CsArchivingPolicy -Filter "tag:*" | Remove-CsArchivingPolicy
  ```

### To remove all the archiving policies that disable internal archiving

- This command removes all the archiving policies where internal archiving has been disabled:
    
  ```
  Get-CsArchivingPolicy | Where-Object {$_.ArchiveInternal -eq $False} | Remove-CsArchivingPolicy
  ```

For more information, see the help topic for the [Remove-CsArchivingPolicy](remove-csarchivingpolicy.md) cmdlet. 
  
## See also

#### 

[Managing the Archiving of internal and external communications in Lync Server 2013](managing-the-archiving-of-internal-and-external-communications.md)

