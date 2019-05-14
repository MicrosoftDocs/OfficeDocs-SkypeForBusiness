---
title: "Modify an existing PIN policy in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: 517caaee-3349-4fa6-8d86-e4da3258a445
description: "Summary: Modify an existing PIN policy in Skype for Business Server."
---

# Modify an existing PIN policy in Skype for Business Server
 
**Summary:** Modify an existing PIN policy in Skype for Business Server.
  
You can use the **PIN Policy** tab to provide personal identification number (PIN) authentication to users who are connecting to Skype for Business with IP Phones. To use PIN authentication, make sure that **Enable PIN Authentication** is selected in Web Service settings.
  
Follow these steps to modify a user-level or a site-level PIN policy. 
  
### To modify an existing PIN policy

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Skype for Business Server.
    
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 
    
3. In the left navigation bar, click **Security** and then click **PIN Policy**.
    
4. On the **PIN Policy** page, click a policy, click **Edit**, and then click **Show details**.
    
5. In **Edit PIN Policy**, in **Minimum PIN length**, type or select the minimum PIN length that you want to allow. The default minimum length is five digits.
    
6. To be able to specify the maximum number of logon attempts before a user is locked out, select the **Specify maximum logon attempts** check box. If you do not select this option, the maximum number of allowed attempts is automatically determined based on the PIN length. By default, the maximum number of attempts is automatically determined.
    
7. If you selected the **Specify maximum logon attempts** check box, in **Maximum logon attempts**, type or select the maximum number of logon attempts that you want to allow.
    
8. To have PINs expire, select the **Enable PIN expiration** check box. If you do not select this option, PINs will never expire. By default, PINs never expire.
    
9. If you selected the **Enable PIN expiration** check box, in **PIN expires after (days)**, type or select the number of days after which PINs expire.
    
10. In **PIN history count**, type the number of PINs that a user must create before the user can reuse a PIN. By default, users can reuse their PINs.
    
11. To allow common patterns of digits in PINs, such as sequential numbers and repetitive sets of numbers, select the **Allow common patterns** check box. If you do not select this option, only complex patterns of digits are allowed. By default, only complex patterns of digits are allowed.
    
    > [!IMPORTANT]
    > We recommend that you do not allow common patterns. 
  
12. Click **Commit**.
    

