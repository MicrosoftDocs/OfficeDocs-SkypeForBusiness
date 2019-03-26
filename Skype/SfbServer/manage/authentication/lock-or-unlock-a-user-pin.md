---
title: "Lock or unlock a user PIN in Skype for Business Server"
ms.reviewer: 
ms.author: heidip
author: microsoftheidi
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: 3d293a8a-e182-4547-8b06-2603c3c77329
description: "Summary: Lock or unlock a user's dial-in conferencing PIN for Skype for Business Server."
---

# Lock or unlock a user PIN in Skype for Business Server
 
**Summary:** Lock or unlock a user's dial-in conferencing PIN for Skype for Business Server.
  
You can lock or unlock a user's PIN from the **Users** section of Skype for Business Server Control Panel.
  
### To lock a user's PIN in Skype for Business Server Control Panel

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel.  
    
3. In the left navigation bar, click **Users**.
    
4. Use one of the following methods to locate a user:
    
    - In the **Search users** box, type all or the first portion of the display name, first name, last name, Security Accounts Manager (SAM) account name, SIP address, or line Uniform Resource Identifier (URI) of the user account, and then click **Find**.
    
    - If you have a saved query, click the **Open query** icon, use the **Open** dialog box to retrieve the query (a .usf file), and then click **Find**.
    
5. (Optional) Specify additional search criteria to narrow the results:
    
   a. Click **Add Filter**.
    
   b. Enter the user property by typing it or by clicking the arrow in the drop-down list to select the property.
    
   c. In the **Equal to** drop-down list, click the operator (for example, **Equal to** or **Not equal to**).
    
   d. Depending on the user property you selected, enter the criteria that you want to use to filter the search results by typing it or by clicking the arrow in the drop-down list.
    
    > [!TIP]
    > To add additional search clauses to your query, click **Add Filter**. 
  
   e. Click **Find**.
    
   f. Click the user, click **Action**, and then click **Lock PIN**.
    
### To unlock a user's PIN in Skype for Business Server Control Panel

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel.  
    
3. In the left navigation bar, click **Users**.
    
4. Use one of the following methods to locate a user:
    
   - In the **Search users** box, type all or the first portion of the display name, first name, last name, Security Accounts Manager (SAM) account name, SIP address, or line Uniform Resource Identifier (URI) of the user account, and then click **Find**.
    
   - If you have a saved query, click the **Open query** icon, use the **Open** dialog box to retrieve the query (a .usf file), and then click **Find**.
    
5. (Optional) Specify additional search criteria to narrow the results:
    
   a. Click **Add Filter**.
    
   b. Enter the user property by typing it or by clicking the arrow in the drop-down list to select the property.
    
   c. In the **Equal to** drop-down list, click the operator (for example, **Equal to** or **Not equal to**).
    
   d. Depending on the user property you selected, enter the criteria that you want to use to filter the search results by typing it or by clicking the arrow in the drop-down list.
    
    > [!TIP]
    > To add additional search clauses to your query, click **Add Filter**. 
  
   e. Click **Find**.
    
   f. Click the user, click **Action**, and then click **Unlock PIN**.
    
## Locking and Unlocking User PINs by Using Windows PowerShell Cmdlets

You can lock and unlock user PINs by using Windows PowerShell and the Lock-CsClientPin and Unlock-CsClientPin cmdlets. You can run these cmdlets either from the Skype for Business Server Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Skype for Business Server, see the blog article ["Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell"](https://go.microsoft.com/fwlink/p/?linkId=255876). The process is the same in Skype for Business Server.
  
### To lock a user PIN

- To lock a user's PIN, use the Lock-CsClientPin cmdlet. For example:
    
  ```
  Lock-CsClientPin -Identity "Ken Myer"
  ```

### To unlock a user PIN

- To unlock a user's PIN, use the Unlock-CsClientPin cmdlet. For example:
    
  ```
  Unlock-CsClientPin -Identity "Ken Myer"
  ```

For more information, see the help topic for the [Lock-CsClientPin](https://docs.microsoft.com/powershell/module/skype/lock-csclientpin?view=skype-ps) and [Unlock-CsClientPin](https://docs.microsoft.com/powershell/module/skype/unlock-csclientpin?view=skype-ps) cmdlets.
