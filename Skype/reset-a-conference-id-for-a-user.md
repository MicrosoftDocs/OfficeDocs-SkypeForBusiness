---
title: Reset a conference ID for a user
ms.prod: OFFICE365
ms.assetid: 6e12242c-55f7-4bf4-90d7-0f36c0326b8e
---


# Reset a conference ID for a user

When your organizations hasn't been enabled for dynamic conference IDs a static conference ID is automatically created when a user is enabled for dial-in conferencing using Microsoft as the provider. This conference ID is included at the bottom of Skype for Business Online meeting invitations along with the dial-in phone numbers that can be used by callers to call into a meeting. When the user dials the phone number, the auto attendant for the meeting will ask the caller to input this conference ID so they can attend the meeting.
  
    
    


> [!NOTE]
> If your conferencing provider is Microsoft, your users' conference ID is set to Dynamic Only by default. Unfortunately, you won't be able to change it in the Skype for Business Admin Center or using Windows Powershell. You will have to contact Microsoft support. 
  
    
    


Note: 
  
    
    

Static IDs are used when people in your organization like it when they don't want to remember a random number, they can select a certain number, or they have one that's easy to remember. When dynamic conference IDs are used, each meeting that a user schedules will get assigned a unique conference ID. If you want to assign dynamic and not static conference IDs,  [Using dial-in conferencing dynamic IDs in your organization](using-dial-in-conferencing-dynamic-ids-in-your-organization.md).Conference IDs are only automatically set by Skype for Business only for users s enabled for dial-in conferencing using Microsoft as their dial-in conferencing provider. If you need to reset a conference ID for a user that is using a third-party audio conferencing provider (ACP), you will need to manually enter a conference ID on the user's properties page for the user.
## Resetting the meeting conference ID for a user

 **To reset the meeting conference ID**
  
    
    

1. Sign in to Office 365 with your work or school account.
    
  
2. Go to the **Office 365 admin center** > **Skype for Business**.
    
  
3. In the **Skype for Business admin center**> **Dial-in conferencing**, in the Action page under **Conference ID** click **Reset**.
    
  
4. In the ** Reset conference ID?** window, click **Yes**. A conference ID will be automatically created and an email sent to the user with the new conference ID. By default, emails are sent to users, but it can be turned off.
    
    > [!NOTE]
      > After you reset the conference ID, an email with the new conference ID will be sent to the user. This email will be sent to the primary email address, in many cases, their Office 365 mailbox. The email contains the new conference ID, default dial-in phone number(s) and instructions to use the Skype for Business Meeting Update Tool to update existing meetings. 

## What else should I know?


- You can send all of the conferencing information to the user in an email that includes the conference ID and dial-in phone numbers by clicking the **Send conference info via email**. It doesn't send the PIN.
    
  
- A conference ID will contain 7 digits and you can't change it's length in either the Skype for Business admin center or using Windows PowerShell.
    
  
- After it has been reset, you can see the new conference ID listed under **Conference ID**.
    
  
- The conference ID for a user for dial-in conferencing can be viewed at the bottom of the Action pane under **Dial-in conferencing** when you select the user on the **Users** page.
    
  
- After a new conference ID is created, the old conference ID can't be used by callers. You should notify users to reschedule their existing meeting invites to make sure the new conference ID is added to the invitations. The users can use Skype for Business Meeting Tool to update their existing meetings. To see how to download, install and run the Skype for Business Meeting Update Tool, see:
    
  -  [Meeting Update Tool for Skype for Business and Lync](http://technet.microsoft.com/library/2b525fe6-ed0f-4331-b533-c31546fcf4d4%28Office.14%29.aspx)
    
  
  -  [Skype for Business Online, Meeting Migration Tool (64-bit)](https://go.microsoft.com/fwlink/?LinkID=626047)
    
  
  -  [Skype for Business Online, Meeting Migration Tool (32-bit)](https://go.microsoft.com/fwlink/?LinkID=626046)
    
  

## Want to know how to manage with Windows PowerShell?


- When it comes to Windows PowerShell is all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Office 365 and Skype for Business Online using a single point of administration that can simplify your daily work, when you have multiple tasks to do. To get started with Windows PowerShell, see these topics:
    
  -  [An introduction to Windows PowerShell and Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525039)
    
  
  -  [Six Reasons Why You Might Want to Use Windows PowerShell to Manage Office 365 ](https://go.microsoft.com/fwlink/?LinkId=525041)
    
  
- Windows PowerShell has many advantages in speed, simplicity, and productivity over only using the Office 365 admin center such as when you are making setting changes for many users at one time. Learn about these advantages in the following topics:
    
  -  [Best ways to manage Office 365 with Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=525142)
    
  
  -  [Using Windows PowerShell to manage Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525453)
    
  
  -  [Using Windows PowerShell to do common Skype for Business Online management tasks](https://go.microsoft.com/fwlink/?LinkId=525038)
    
  

