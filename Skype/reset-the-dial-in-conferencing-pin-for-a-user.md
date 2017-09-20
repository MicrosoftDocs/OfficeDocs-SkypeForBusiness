---
title: Reset the dial-in conferencing PIN for a user
ms.prod: OFFICE365
ms.assetid: 67866a47-89c1-4593-8766-3a68777e2be6
---


# Reset the dial-in conferencing PIN for a user

A PIN is a code made up of numbers that is created for each user who is enabled for dial-in conferencing. Dial-in conferencing PINs are used by meeting organizers to identify that they are the meeting organizer and allow them to start a meeting over the phone. If they use the Skype for Business client to start the meeting, a PIN isn't required. If users forget their PIN and they can't find it in the email that was sent to them when they were enabled for dial-in conferencing, an administrator will need to reset their PIN. A user can't reset their own PIN.
  
    
    

Meetings can be started when an authenticated user joins using a Skype for Business client or when the organizer joins with his or her PIN over the phone. When a meeting requires a PIN to start, users who join over the phone will be placed in the lobby and will listen to music on hold until the meeting starts. If the organizer of a meeting doesn't require a PIN to start the meeting over the phone, then callers won't be asked to provide a PIN when they join the meeting.
## 


  
    
    
 **Reset a conference organizer's PIN**
  
    
    

1. Sign in to Office 365 with your work or school account.
    
  
2. Go to the **Office 365 admin center** > **Skype for Business** and in the left navigation click **Dial-in conferencing**
    
  
3. Click on **Dial-in users**, select the user that you want to reset the PIN for.
    
  
4. In the Action pane, click **Reset PIN**.
    
  

## What else should you know about PINs?


- For security purposes, the PIN is only shown to an administrator on one time, when the PIN is reset. After the PIN is reset by an administrator, the PIN will be listed as *********** in the Skype for Business admin center and in the results when they use **Get-CsCsOnlineDialInConfencingUser** in the Windows PowerShell.
    
  
- Automatically sending emails to users is enabled by default and users will receive an email with their PIN when they're enabled for dial-in conferencing or when the PIN is reset. But if you have disabled automatically sending emails, then a PIN reset email won't be sent to a user and you will have to manually send the PIN information to the user. 
    
  
- When a meeting starts, all of the users in the lobby will automatically join it. For example, if two participants try to join a meeting before it has been started, they will be put in the lobby and will listen to music on hold, and when the meeting organizer joins using his PIN via phone, the meeting will start and the participants in the lobby will join the meeting.
    
  
- The default setting isn't to allow a meeting to be started by anonymous callers.
    
  
- When you enable a user for dial-in conferencing, by default they are sent emails that includes conferencing information and their PIN. The user must have an Office 365 mailbox because when a PIN is reset, a new PIN will be sent to the user in email to their primary SMTP address (alias) that is set for the user.
    
  
- When you set up dial-in conferencing, you set the digits that are required for the PINs in your organization. PINs can be from 4 to 12 digits - the default is 5. If you change the PIN length setting, the setting is only applied on newly generated PINs and isn't applied to the PIN setting for existing users that are enabled for dial-in conferencing. See  [Set the length of the PIN for dial-in meetings](set-the-length-of-the-pin-for-dial-in-meetings.md)
    
  
- The email by default will be set to the Office 365 primary SMTP address of the user you can send an email to a non-Office 365 address such as a Hotmail or MSN email address. Using Windows PowerShell you can override the default email address. This is useful if the users don't have an Exchange mailbox in Office 365.
    
  
- To override the default user address where the email is sent to, the tenant admin can use the following cmdlet:  `Set-CsOnlineDialInConferencingUser -amos.marble -ResetLeaderPIN -SendEmail -SendEmailToAddress "u@hotmail.com"`. The  _SendEmail_ parameter is required to override the email address of the user.
    
  

## Want to know how to manage with Windows PowerShell?


- To save time or automate this, you can use the  [Set-CsOnlineDialInConferencingUser](https://go.microsoft.com/fwlink/?LinkId=617688 ) cmdlet.
    
  
- You can set the PIN for Amos Marble by running:
    
  ```
  
Set-CsOnlineDialInConferencingUser -id amos.marble@contoso.com -ResetLeaderPIN
  ```


-  Windows PowerShell is all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Office 365 using a single point of administration that can simplify your daily work when you have multiple tasks to do. To get started with Windows PowerShell, see these topics:
    
  -  [Six Reasons Why You Might Want to Use Windows PowerShell to Manage Office 365 ](https://go.microsoft.com/fwlink/?LinkId=525041)
    
  
  -  [Best ways to manage Office 365 with Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=525142)
    
  
- Windows PowerShell has many advantages in speed, simplicity, and productivity over only using the Office 365 admin center such as when you are making setting changes for many users at one time. Learn about these advantages in the following topics: 
    
  -  [An introduction to Windows PowerShell and Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525039)
    
     [Using Windows PowerShell to manage Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525453)
    
  
  -  [Using Windows PowerShell to do common Skype for Business Online management tasks](https://go.microsoft.com/fwlink/?LinkId=525038)
    
  

    > [!NOTE]
      > The Windows PowerShell module for Skype for Business Online enables you to create a remote Windows PowerShell session that connects to Skype for Business Online. This module, which is supported only on 64-bit computers, can be downloaded from the Microsoft Download Center at  [Windows PowerShell Module for Skype for Business Online.](https://go.microsoft.com/fwlink/?LinkId=294688)

