---
title: "What are the special character restrictions in Teams policies?"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: jastark
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.collection: 
- M365-collaboration
- Teams_ITAdmin_Help
search.appverid: MET150
audience: Admin
appliesto:
- Skype for Business 
- Microsoft Teams
localization_priority: Normal
ROBOTS: NOINDEX, NOFOLLOW
f1keywords:
- ms.teamsadmincenter.policies.naming.error
description: "See what issues there are with special characters in the names of policies and what you can do to fix it."
---

# What are the special character restrictions in Teams policies?

**You can't create or edit policies (for messaging, meetings, etc.) that have a special character in the name in the Microsoft Teams admin center**. 

If a policy name contains special characters, you will be limited in managing these policies in the Microsoft Teams admin center. **As such, we strongly recommend that policy names don't include special characters**. 

Policy names that have been created using PowerShell for meetings and messaging in Teams can have special characters such as @,#,$. However, if you are wanting to make changes to the policy in the Microsoft Teams admin center,you won't be able to. 

If you have a policy with special characters, you will need to either edit the policy using Windows PowerShell (forever) or create a new policy in the Microsoft Teams admin center with the same settings as the old policy and assign it to the same group of users.

## To remove special characters

**Step 1 - Make a remote connection with PowerShell.**
[Set up your computer for Windows PowerShell](https://docs.microsoft.com/skypeforbusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell) if you haven't yet.
```
 Import-Module "C:\Program Files\Common Files\Skype for Business Online\Modules\SkypeOnlineConnector\SkypeOnlineConnector.psd1"
 $credential = Get-Credential
 $session = New-CsOnlineSession -Credential $credential
 Import-PSSession $session
```


**Step 2 - Get the settings for the old policy and capture the output.**

> [!NOTE]
> This example is for a [Messaging](https://docs.microsoft.com/powershell/module/skype/get-csteamsmessagingpolicy?view=skype-ps) policy.  The steps would be the same for other policy types but you must use the correct cmdlet. 

  ```
  Get-CsTeamsMessagingPolicy -id <old_policy_name>
  ```


**Step 3 - Create a new policy.**

You can either create the new policy with the same setting by using the Microsoft Teams admin center or PowerShell.

Running this will create a new policy for you but you will need to add the correct settings by seeing [Set-CsTeamsMessagingPolicy](https://docs.microsoft.com/powershell/module/skype/set-csteamsmessagingpolicy?view=skype-ps) and then running it:

  ```
  Set-CsTeamsMessagingPolicy -id <new_policy_name>
 ```
**Step 4 - Assign the policy.**
 ```
Grant-CsTeamsMessagingPolicy -Policy <new_policy_name>
 ```
See, [Grant-CsTeamsMessagingPolicy](https://docs.microsoft.com/powershell/module/skype/grant-csteamsmessagingpolicy?view=skype-ps) for more information on this cmdlet.

**Step 5 - Delete the old policy.**

This will delete the old policy with the special characters.
  ```
  Remove-CsTeamsMessagingPolicy -identity <old_policy_name>
  ```
See, [Remove-CsTeamsMessagingPolicy](https://docs.microsoft.com/powershell/module/skype/remove-csteamsmessagingpolicy?view=skype-ps) for more information on this cmdlet.

If this command succeeds, you're done. If the above command returns an error, it is because the old policy is assigned to users so you need to run to remove all assigned users from the policy:

```
Grant-CsMessagingPolicy -Policy <old_policy_name> $null
```
### Want to know how to manage with Windows PowerShell?

Windows PowerShell is all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Office 365 using a single point of administration that can simplify your daily work when you have multiple tasks to do. To get started with Windows PowerShell, see these topics:
    
  - [Why you need to use Office 365 PowerShell?](https://go.microsoft.com/fwlink/?LinkId=525041)
    
  - [Best ways to manage Office 365 with Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=525142)
    
- Windows PowerShell has many advantages in speed, simplicity, and productivity over only using the Microsoft 365 admin center, such as when you are making settings changes for many users at one time. Learn about these advantages in the following topics:
    
  - [An introduction to Windows PowerShell and Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525039)
    
    [Using Windows PowerShell to manage Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525453)
    
  - [Using Windows PowerShell to do common Skype for Business Online management tasks](https://go.microsoft.com/fwlink/?LinkId=525038)
    
    > [!NOTE]
    > The Windows PowerShell module for Skype for Business Online enables you to create a remote Windows PowerShell session that connects to Skype for Business Online and Microsoft Teams. This module, which is supported only on 64-bit computers, can be downloaded from the Microsoft Download Center at [Windows PowerShell Module for Skype for Business Online.](https://go.microsoft.com/fwlink/?LinkId=294688)
  

