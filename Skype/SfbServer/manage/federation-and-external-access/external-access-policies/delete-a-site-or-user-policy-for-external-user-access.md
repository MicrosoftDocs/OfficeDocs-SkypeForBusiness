---
title: 'Delete a site or user policy for external user access'
ms.reviewer: 
ms:assetid: 6d907507-825b-4354-9c03-337a459f72de
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg521013(v=OCS.15)
ms:contentKeyID: 48184455
mtps_version: v=OCS.15
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "You can delete any site or user policy that is listed in the Skype for Business Server Control Panel on the External Access Policy page."
---


# Delete a site or user policy for external user access

If you have created or configured external user access policies that you no longer want to use, you can do the following:

  - Delete any site or user policy that you created.

  - Reset the global policy to the default settings. The default global policy settings deny any external user access. The global policy cannot be deleted.


You can delete any site or user policy that is listed in the Skype for Business Server Control Panel on the **External Access Policy** page. Deleting the global policy does not actually delete it, but only resets it to the default settings, which do not include support for any external user access options. For details about resetting the global policy, see [Reset the global policy for external user access](reset-the-global-policy-for-external-user-access.md).


## To delete a site or user policy for external user access

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 

3.  Click **External User Access**, click **External Access Policy**.

4.  On the **External Access Policy** tab, click the site or user policy you want to delete, click **Edit**, and then click **Delete**.

5.  When prompted to confirm the deletion, click **OK**.


## Removing PIN Policies by Using Windows PowerShell Cmdlets

External access policies can be deleted by using Windows PowerShell and the Remove-CsExternalAccessPolicy cmdlet. This cmdlet can be run either from the Skype for Business Server Management Shell or from a remote session of Windows PowerShell. 


## To remove a specific external access policy

  - This command removes the external access policy applied to the Redmond site:
    
        Remove-CsExternalAccessPolicy -Identity "site:Redmond"


## To remove all the external access policies applied to the per-user scope

  - This command removes all the external access policies configured at the per-user scope:
    
        Get-CsExternalAccessPolicy -Filter "tag:*" | Remove-CsExternalAccessPolicy


## To remove all the external access policies where outside user access is disabled

  - This command deletes all the external access policies where outside user access has been disabled:
    
        Get-CsExternalAccessPolicy | Where-Object {$_.EnableOutsideAccess -eq $False} | Remove-CsExternalAccessPolicy


For more information, see the help topic for the [Remove-CsExternalAccessPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsExternalAccessPolicy) cmdlet.
