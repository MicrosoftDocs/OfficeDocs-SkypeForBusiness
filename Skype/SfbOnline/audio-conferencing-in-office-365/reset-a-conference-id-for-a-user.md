---
title: "Reset a conference ID for a user"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: oscarr
ms.date: 01/22/2018
ms.topic: article
ms.assetid: 6e12242c-55f7-4bf4-90d7-0f36c0326b8e
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
ms.collection: 
- Adm_Skype4B_Online
- Strat_SB_PSTN
ms.audience: Admin
appliesto:
- Skype for Business 
- Microsoft Teams
localization_priority: Normal
f1keywords: None
ms.custom:
- Strat_SB_PSTN
- Audio Conferencing
description: "Learn the steps to reset a user's meeting conference ID, and get links to meeting update and migration tools. "
---

# Reset a conference ID for a user

When your organizations hasn't been enabled for dynamic conference IDs, a static conference ID is automatically created when a Skype for Business or Microsoft Teams user is enabled for Audio Conferencing using Microsoft as the provider. This conference ID is included at the bottom of meeting invitations along with the dial-in phone numbers that can be used by callers to call in to a meeting. When the user dials the phone number, the auto attendant for the meeting will ask the caller to enter this conference ID so they can attend the meeting.
  
> [!NOTE]
> If your conferencing provider is Microsoft, your users' conference IDs are set to Dynamic Only by default. Unfortunately, you won't be able to change it in the Skype for Business Admin Center or using Windows Powershell. You will have to contact Microsoft support. 
  
Static IDs are used when people in your organization don't want to remember a random number; they can select a certain number or use one that's easy to remember. When dynamic conference IDs are used, each meeting that a user schedules will get assigned a unique conference ID. If you want to assign dynamic rather than static conference IDs, [go here](using-audio-conferencing-dynamic-ids-in-your-organization.md).
  
Conference IDs are only automatically set only for Skype for Business and Microsoft Teams users enabled for Audio Conferencing using Microsoft as their audio conferencing provider. If you need to reset a conference ID for a user who is using a third-party audio conferencing provider (ACP), you will need to manually enter a conference ID on the properties page for the user.
  
## Resetting the conference ID for a user

**Using the Microsoft Teams and Skype for Business Admin Center**

1. In the left navigation, click **Users**, and then select the user from teh list of available users.

2. At the top of the page, click **Edit**.

3. Click the menu next to **Conference Bridges**, and then click **Reset conference id** in the drop-down list.

2. In the **Reset conference id** window, click **Ok**. A conference ID will be automatically created and an email sent to the user with the new conference ID. By default, emails are sent to users, but this can be turned off.   

**Using the Skype for Business admin center**
    
1. In the **Skype for Business admin center**, click **Audio conferencing** > **Users**, select a user, and then in the Action pane under **Conference ID** click **Reset**.
    
2. In the **Reset conference ID?** window, click **Yes**. A conference ID will be automatically created and an email sent to the user with the new conference ID. By default, emails are sent to users, but this can be turned off.
    
> [!NOTE]
> After you reset the conference ID, an email with the new conference ID will be sent to the user. This email will be sent to the primary email address, in many cases, their Office 365 mailbox. The email contains the new conference ID, default dial-in phone number(s) and instructions to use the Skype for Business Meeting Update Tool to update existing meetings. 
  
## What else should I know?

- You can send all of the conferencing information to the user in an email that includes the conference ID and dial-in phone numbers by clicking **Send conference info via email** for the user in the Action pane. It doesn't send the PIN.
    
- A conference ID will contain 7 digits, and you can't change its length in the Skype for Business admin center or by using Windows PowerShell.
    
- After it has been reset, you can see the new conference ID listed under **Conference ID**.
    
- The conference ID for a user for audio conferencing can be viewed at the bottom of the Action pane under **Audio conferencing** when you select the user on the **Users** page.
    
- After a new conference ID is created, the old conference ID can't be used by callers. You should notify users to reschedule their existing meeting invites to make sure the new conference ID is added to the invitations. The users can use Skype for Business Meeting Tool to update their existing meetings. To see how to download, install, and run the Skype for Business Meeting Update Tool, see:
    
  - [Meeting Update Tool for Skype for Business and Lync](https://support.office.com/article/2b525fe6-ed0f-4331-b533-c31546fcf4d4)
    
  - [Skype for Business Online, Meeting Migration Tool (64-bit)](https://go.microsoft.com/fwlink/?LinkID=626047)
    
  - [Skype for Business Online, Meeting Migration Tool (32-bit)](https://www.microsoft.com/en-us/download/details.aspx?id=54079)
    
## Want to know how to manage with Windows PowerShell?

- When it comes to Windows PowerShell is all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Office 365 and Skype for Business Online using a single point of administration that can simplify your daily work, when you have multiple tasks to do. To get started with Windows PowerShell, see these topics:
    
  - [An introduction to Windows PowerShell and Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525039)
    
  - [Why you need to use Office 365 PowerShell](https://go.microsoft.com/fwlink/?LinkId=525041)
    
- Windows PowerShell has many advantages in speed, simplicity, and productivity over only using the Office 365 admin center such as when you are making setting changes for many users at one time. Learn about these advantages in the following topics:
    
  - [Best ways to manage Office 365 with Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=525142)
    
  - [Using Windows PowerShell to manage Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525453)
    
  - [Using Windows PowerShell to do common Skype for Business Online management tasks](https://go.microsoft.com/fwlink/?LinkId=525038)
    
## Related topics

[Reset the Audio Conferencing PIN for a user](reset-the-audio-conferencing-pin-for-a-user.md)

## Feedback?
To provide product feedback or to let us know how we're doing, see [Skype for Business Feedback](https://www.skypefeedback.com).