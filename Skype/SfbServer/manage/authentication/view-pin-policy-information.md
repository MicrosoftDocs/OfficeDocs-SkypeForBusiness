---
title: "View PIN policy information in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: 1d48b060-d77f-44ee-b70f-3ce128aedac4
description: "Summary: View a user's PIN policy information for Skype for Business Server."
---

# View PIN policy information in Skype for Business Server
 
**Summary:** View a user's PIN policy information for Skype for Business Server.
  
You can use the **PIN Policy** tab to view personal identification number (PIN) authentication of users who are connecting to Skype for Business with IP Phones. To use PIN authentication, make sure that **Enable PIN Authentication** is selected in Web Service settings.
  
Follow these steps to modify a user-level or a site-level PIN policy. 
  
### To view information about a PIN policy in Skype for Business Server Control Panel

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Skype for Business Server.
    
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel.  
    
3. In the left navigation bar, click **Security** and then click **PIN Policy**.
    
4. On the **PIN Policy** page, click a policy, click **Edit**, and then click **Show details**.
    
## Viewing PIN Policies by Using Windows PowerShell Cmdlets

You can also view PIN policies by using Windows PowerShell and the Get-CsPinPolicy cmdlet. This cmdlet can be run either from the Skype for Business Server Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Skype for Business Server, see the blog article ["Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell"](https://go.microsoft.com/fwlink/p/?linkId=255876). The process is the same in Skype for Business Server.
  
### To view PIN policies

To view information about all your PIN policies, type the following command in the Skype for Business Server Management Shell and then press ENTER:
    
  ```
  Get-CsPinPolicy
  ```

That will return information similar to this:

<pre>
Identity             : Global
Description          :
MinPasswordLength    : 5
PINHistoryCount      : 0
AllowCommonPatterns  : False
PINLifetime          : 0
MaximumLogonAttempts :
</pre>

For more information, see the help topic for the [Get-CsPinPolicy](https://docs.microsoft.com/powershell/module/skype/get-cspinpolicy?view=skype-ps) cmdlet.
  
## See also

[Create a new PIN policy in Skype for Business Server](create-a-new-pin-policy.md)
