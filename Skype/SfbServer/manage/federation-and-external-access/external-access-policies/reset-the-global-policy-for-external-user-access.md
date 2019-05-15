---
title: 'Reset the global policy for external user access'
ms.reviewer: 
ms:assetid: 8207e1b1-de9e-461f-975f-fcc5c526849a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg182545(v=OCS.15)
ms:contentKeyID: 48184675
mtps_version: v=OCS.15
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "You cannot completely delete a global policy. Using the **Delete** option on the global policy only resets the global policy to the default settings, which do not include support for any external user access options."
---


# Reset the global policy for external user access in Skype for Business Server 

If you have created or configured external user access policies that you no longer want to use, you can do the following:

  - Delete any site or user policy that you created.

  - Reset the global policy to the default settings. The default global policy settings deny any external user access. The global policy cannot be deleted.

You cannot completely delete a global policy. Using the **Delete** option on the global policy only resets the global policy to the default settings, which do not include support for any external user access options.

## To reset the global policy to the default settings

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel.

3.  In the left navigation bar, click **External User Access**, click **External Access Policy**.

4.  On the **External Access Policy** tab, click the global policy, click **Edit**, and then click **Delete**.

5.  When prompted to confirm the deletion, click **OK**. A message appears at the top of the page informing you that the global policy has been reset.


## Resetting the Global External Access Policy by Using Windows PowerShell Cmdlets

The global external access policy can be reset by using Windows PowerShell and the Remove-CsExternalAccessPolicy cmdlet. This cmdlet can be run either from the Skype for Business Server Management Shell or from a remote session Windows PowerShell. 

## To reset the global external access policy

  - This command resets the global external access policy:
    
        Remove-CsExternalAccessPolicy -Identity "global"

For more information, see the help topic for the [Remove-CsExternalAccessPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsExternalAccessPolicy) cmdlet.


