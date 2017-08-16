---
title: Start an audio conference over the phone without a PIN
ms.prod: OFFICE365
ms.assetid: d5b1f775-d7ed-4d30-853a-1d49f81e8fde
---


# Start an audio conference over the phone without a PIN

It might be frustrating for users who dial in to a meeting to be held in the meeting's lobby listening to music because an organizer hasn't started the meeting. 
  
    
    

If a meeting organizer calls into their meeting, by default, a PIN is required to start a meeting. You can set it up so that anyone can dial in to the meeting and not be prompted for a PIN to start the meeting. You can set it up so when a single user or when all of your dial-in users in your organization can start meetings without a PIN. You can use the Skype for Business admin center to enable or disable this setting for a single user. 
A PIN isn't required for the meeting organizer if someone has started the meeting from a Skype for Business client. A PIN is only required when a meeting organizer joins their meeting over a phone. The PIN for meetings is sent to the dial-in user when they are assigned the **Skype for Business PSTN Conferencing** license or are enabled for dial-in conferencing. See, [Send an email to a user with their dial-in conferencing information](send-an-email-to-a-user-with-their-dial-in-conferencing-information.md) and [Emails that are automatically sent to users when their dial-in conferencing settings change](emails-that-are-automatically-sent-to-users-when-their-dial-in-conferencing-sett.md).
  
    
    


## Enable or disable anonymous callers from joining a meeting


1. Sign in to Office 365 with your work or school account.
    
  
2. Go to the **Office 365 admin center** > **Skype for Business**.
    
  
3. In the **Skype for Business admin center**, in the left navigation go to **Dial-in conferencing** > **Dial-in users**. 
    
  
4. In the list select the user and on the Action pane click **Edit**. 
    
  
5. On the user's properties page, under **Meeting options**, check or uncheck **Allow unauthenticated callers to be the first people in a meeting. If not, then they will wait in the lobby until an authenticated user joins**.
    
  
6. Click **Save**. 
    
  
 **To enable or disable anonymous callers to all of your user's meetings using Windows Powershell**
  
    
    

- Run the following: 
    
  ```
  
Set-CsOnlineDialInConferencingTenantSetting -AllowPSTNOnlyMeetingsByDefault $true | $false
  ```


## What else should you know?


- If you want to reset the PIN, see  [Reset the dial-in conferencing PIN for a user](reset-the-dial-in-conferencing-pin-for-a-user.md).
    
  
- If anonymous access or not requiring a PIN to start a meeting is enabled:
    
  - If the meeting hasn't started (there's no one in the meeting yet):
    
    A caller will be prompted if he's the organizer, if he says yes, he'll be prompted for his PIN after he inputs the PIN, the meeting will start and the user will join the meeting.
    
  
  - If the meeting already started (someone else is already in the meeting):
    
    A caller won't be prompted if he's the organizer and he'll never be prompted for the PIN, the meeting is already started, the caller will join it.
    
  
- If anonymous access or not requiring a PIN to start a meeting is disabled: 
    
  - If the meeting hasn't started (there's no one in the meeting yet):
    
    A caller won't be prompted if he's the organizer and he'll never be prompted for the PIN. Because the setting of the organizer is set to off, the meeting will start and the anonymouscallers will join the meeting.
    
  
  - If the meeting already started (someone else is already in the meeting):
    
    A caller won't be prompted if he's the organizer and he'll never be prompted for the PIN, the meeting is already started, the caller will join it.
    
  

## Want to know how to manage with Windows PowerShell?


- To save time or automate this for more than one user, you can use the  [Set-CsOnlineDialInConferencingUser](https://go.microsoft.com/fwlink/?LinkId=617688 ) cmdlet.
    
  

-  When it comes to Windows PowerShell, Skype for Business Online is all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Office UNRESOLVED_TOKEN_VAL(365) using a single point of administration that can simplify your daily work when you have multiple tasks to do. To get started with Windows PowerShell, see these topics:
    
  -  [Six Reasons Why You Might Want to Use Windows PowerShell to Manage Office 365 ](https://go.microsoft.com/fwlink/?LinkId=525041)
    
  
  -  [Best ways to manage Office 365 with Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=525142)
    
  
- Windows PowerShell has many advantages in speed, simplicity, and productivity over only using the Office 365 admin center such as when you are making setting changes for many users at one time. Learn about these advantages in the following topics: 
    
  -  [An introduction to Windows PowerShell and Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525039)
    
     [Using Windows PowerShell to manage Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525453)
    
  
  -  [Using Windows PowerShell to do common Skype for Business Online management tasks](https://go.microsoft.com/fwlink/?LinkId=525038)
    
  

    > [!NOTE]
      > The Windows PowerShell module for Skype for Business Online enables you to create a remote Windows PowerShell session that connects to Skype for Business Online. This module, which is supported only on 64-bit computers, can be downloaded from the Microsoft Download Center at  [Windows PowerShell Module for Skype for Business Online.](https://go.microsoft.com/fwlink/?LinkId=294688)

