---
title: "Reset the global policy for external user access in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8207e1b1-de9e-461f-975f-fcc5c526849a
description: "You cannot completely delete a global policy. Using the Delete option on the global policy only resets the global policy to the default settings, which do not include support for any external user access options."
---

# Reset the global policy for external user access in Lync Server 2013
[]
You cannot completely delete a global policy. Using the **Delete** option on the global policy only resets the global policy to the default settings, which do not include support for any external user access options. 
  
### To reset the global policy to the default settings

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment. 
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **External User Access**, click **External Access Policy**.
    
4. On the **External Access Policy** tab, click the global policy, click **Edit**, and then click **Delete**.
    
5. When prompted to confirm the deletion, click **OK**. A message appears at the top of the page informing you that the global policy has been reset.
    
## Resetting the Global External Access Policy by Using Windows PowerShell Cmdlets

The global external access policy can be reset by using Windows PowerShell and the Remove-CsExternalAccessPolicy cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876).
  
### To reset the global external access policy

- This command resets the global external access policy:
    
  ```
  Remove-CsExternalAccessPolicy -Identity "global"
  ```

For more information, see the help topic for the [Remove-CsExternalAccessPolicy](remove-csexternalaccesspolicy.md) cmdlet. 
  

