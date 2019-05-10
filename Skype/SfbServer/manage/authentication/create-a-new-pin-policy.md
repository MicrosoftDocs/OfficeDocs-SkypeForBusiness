---
title: "Create a new PIN policy in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: 8bdf0478-fe9f-4371-93ff-db39381a25db
description: "Summary: Create a new PIN policy in Skype for Business Server."
---

# Create a new PIN policy in Skype for Business Server
 
**Summary:** Create a new PIN policy in Skype for Business Server.
  
You can use the **PIN Policy** page to provide personal identification number (PIN) authentication to users who are connecting to Skype for Business with IP Phones. To use PIN authentication, make sure that **Enable PIN Authentication** is selected in Web Service settings.
  
Follow these steps to create a user-level or a site-level PIN policy. 
  
### To create a user or site PIN policy

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Skype for Business Server.
    
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 
    
3. In the left navigation bar, click **Security** and then click **PIN Policy**.
    
4. On the **PIN Policy** page, click **New**, and then do one of the following:
    
   - To create a user-level policy, click **User policy**. In **New PIN Policy**, in **Name**, type a name that describes the policy.
    
   - To create a site-level policy, click **Site policy**. In the **Select a Site** search field, type all or part of the name of the site for which you want to create a policy. In the resulting list of sites, click the site you want, and then click **OK**.
    
5. In the **Description** field, type a description of the PIN policy.
    
6. In the **Minimum PIN length** field, type or select the minimum PIN length that you want to allow. The default minimum length is five digits.
    
7. To be able to specify the maximum number of logon attempts before a user is locked out, select the **Specify maximum logon attempts** check box. If you do not select this option, the maximum number of allowed attempts is automatically determined based on the PIN length. By default, the maximum number of attempts is automatically determined.
    
8. If you selected the **Specify maximum logon attempts** check box, in **Maximum logon attempts**, type or select the maximum number of logon attempts that you want to allow.
    
9. To have PINs expire, select the **Enable PIN expiration** check box. If you do not select this option, PINs will never expire. By default, PINs never expire.
    
10. If you selected the **Enable PIN expiration** check box, in **PIN expires after (days)**, type or select the number of days after which PINs expire.
    
11. In **PIN history count**, type the number of PINs that a user must create before the user can reuse a PIN. By default, users can reuse their PINs.
    
12. To allow common patterns of digits in PINs, such as "1234" and "8888", select the **Allow common patterns** check box. If you do not select this option, only complex patterns of digits are allowed. By default, only complex patterns of digits are allowed.
    
    > [!IMPORTANT]
    > We recommend that you do not allow common patterns. 
  
13. Click **Commit**.
    

