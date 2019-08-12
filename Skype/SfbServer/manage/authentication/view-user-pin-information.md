---
title: "View user PIN information in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: 59e38117-8112-4851-82ac-a746ffa0f89d
description: "Summary: View user PIN information in Skype for Business Server."
---

# View user PIN information in Skype for Business Server
 
**Summary:** View user PIN information in Skype for Business Server.
  
To join a dial-in conference as an authenticated user, a Skype for Business Server user with Active Directory Domain Services (AD DS) credentials requires a personal identification number (PIN). You can view a user's PIN information from Skype for Business Server Control Panel.
  
> [!NOTE]
> You can view PIN status information such as whether the PIN has been set or when the PIN was last changed, but you cannot see the current PIN by looking at the PIN status. If a user has lost their PIN, you can reset it by following the procedures in [Set a user's dial-in conferencing PIN in Skype for Business Server](set-a-user-s-dial-in-conferencing-pin.md)
  
### To view a user's PIN in Skype for Business Server Control Panel

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
  
6. Click a user in the search results, click **Action**, and then click **View PIN status**.
    
## Viewing User PIN Information by Using Windows PowerShell cmdlets

You can view user PIN information by using the Get-CsClientPinInfo cmdlet. This cmdlet can be run either from the Skype for Business Server Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Skype for Business Server, see the blog article ["Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell"](https://go.microsoft.com/fwlink/p/?linkId=255876). The process is the same in Skype for Business Server.
  
### To view user PIN information

To view PIN information for a user, type a command similar to the following in the Skype for Business Server Management Shell and then press ENTER:
    
  ```
  Get-CsClientPinInfo -Identity "Ken Myer"
  ```

That will return information similar to this:

<pre>
Identity          : sip:kenmyer@litwareinc.com
IsPinSet          : False
IsLockedOut       : False
LastPinChangeTime : 9/25/2012 1:35:03 PM
PinExpirationTime :
</pre>

For more information, see the help topic for the [Get-CsConferenceDisclaimer](https://docs.microsoft.com/powershell/module/skype/get-csconferencedisclaimer?view=skype-ps) cmdlet.
  
## See also

[Set a user's dial-in conferencing PIN in Skype for Business Server](set-a-user-s-dial-in-conferencing-pin.md)
  
[Lock or unlock a user PIN in Skype for Business Server](lock-or-unlock-a-user-pin.md)
