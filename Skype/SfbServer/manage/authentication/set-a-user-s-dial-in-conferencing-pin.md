---
title: "Set a user's dial-in conferencing PIN in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: 4252b5a5-4267-4513-b18e-0253a8d66f72
description: "Summary: Set a user's dial-in conferencing PIN for Skype for Business Server."
---

# Set a user's dial-in conferencing PIN in Skype for Business Server
 
**Summary:** Set a user's dial-in conferencing PIN for Skype for Business Server.
  
To join a dial-in conference as an authenticated user, a Skype for Business Server user with Active Directory Domain Services (AD DS) credentials requires a personal identification number (PIN). If a user forgets the dial-in conferencing PIN or has not set the PIN by using Skype for Business Server, you can set the user's PIN from Skype for Business Server Control Panel. You can automatically generate the PIN or create one manually.
  
> [!NOTE]
> Specific characteristics of the PIN, such as its minimum length, can be configured as a policy. In addition to the global policy, you can configure a PIN policy for individual sites or users. 
  
### To set a user's PIN

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
    
    > [!NOTE]
    > If the PIN is locked, you must unlock the PIN before you can set it. To unlock the PIN, click the user, click **Action**, and then click **Unlock PIN**. 
  
6. Click a user in the search results, click **Action**, and then click **Set PIN**.
    
7. In the **Set PIN** dialog box, do one of the following:
    
   - To allow Skype for Business Server to generate the user's PIN, select **Automatically generate a valid PIN** (the default).
    
   - To create your own PIN, click **Manually enter a specific PIN**, click the text box, and then type a PIN that meets the PIN requirements specified in your PIN policy settings.
    
8. Click **OK**.
    
9. In **Set PIN**, do one of the following: 
    
   - Select the **Show PIN** check box to see the PIN, and then copy the PIN and communicate it to the user using your organization's preferred method.
    
   - Click **Open my email application to send the new PIN to the user** to send the PIN by email. If Microsoft Office Outlook is your email client, the PIN is automatically copied into a new email message. If you use a different email client, select the **Show PIN** check box to see the PIN and then copy it into your email message.
    
10. Click **Close**.
    
## Assigning a User PIN by Using Windows PowerShell Cmdlets

You can assign PIN numbers can also be assigned by using the Set-CsClientPin cmdlet. You can run this cmdlet either from the Skype for Business Server Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Skype for Business Server, see the blog article ["Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell"](https://go.microsoft.com/fwlink/p/?linkId=255876). The process is the same in Skype for Business Server. 
  
### To auto-assign a PIN number to a user

The following command assigns a PIN number to the user Ken Myer. Because the Pin parameter is not included, Skype for Business Server will automatically generate and assign the PIN number.
    
  ```
  Set-CsClientPin -Identity "Ken Myer" 
  ```

### To assign a specific PIN number to a user

This command uses the Pin parameter to assign the PIN number 121989 to the user Ken Myer.
    
  ```
  Set-CsClientPin -Identity "Ken Myer" -Pin 121989
  ```

For more information, see the help topic for the [Set-CsClientPin](https://docs.microsoft.com/powershell/module/skype/set-csclientpin?view=skype-ps) cmdlet.
  

