---
title: Change the settings for a Microsoft dial-in conferencing bridge
ms.prod: OFFICE365
ms.assetid: 783fad3f-b77c-422b-b91f-7c8b0af324fb
---


# Change the settings for a Microsoft dial-in conferencing bridge

When you are setting up dial-in conferencing in Skype for Business Online, you will receive phone numbers for your users from what is called a dial-in or audio conferencing bridge. A conferencing bridge can contain one or more phone numbers. These phone numbers are used when callers dial into a meeting. The phone number is included at the bottom of the meeting invite.
  
    
    

The conferencing bridge answers a call and prompts the caller with voice prompts using a meeting auto attendant and then depending on your settings can play notifications, ask callers to record their name and controls the PIN settings. PINs are given to a meeting organizer that allows them to start a meeting when they are aren't using a Skype for Business client.
> [!NOTE]
> A PIN is only required for the meeting organizer when a Skype for Business client user hasn't already started the meeting. If everyone is dialing in to the meeting, then the PIN is required for the meeting organizer to start the meeting. 
  
    
    


## Change the settings for a Microsoft dial-in conferencing bridge

 **Set up the meeting experience when callers join a meeting**
  
    
    

1. Sign in to Office 365 with your work or school account.
    
  
2. Go to the **Office 365 admin center** > **Skype for Business**.
    
  
3. In the **Skype for Business admin center**, in the left navigation go to **Dial-in conferencing** > **Microsoft bridge settings**.
    
  
4. On the **Microsoft bridge settings** page under **Meeting join experience** select:
    
  - **Enable meeting entry and exit notifications to be turned on** This is selected by default. However if you uncheck it, users that have already joined the meeting won't be notified that someone enters or leaves the meeting.
    
    When you select **Enable meeting entry and exit notifications to be turned on** you can select these options from the **Entry-exist announcement type** drop down:
    
  - **Phone numbers** When a user dials in to a meeting their phone number will be played when they join it.
    
  
  - **Tones** When users dial in to a meeting an audio tone will be played when they join it.
    
    > [!NOTE]
      > Using **Tone** as the announcement type is currently available to all customers as a preview feature.
  - **Ask callers to record their name before joining the meeting** This is selected by default. However, if you uncheck it, callers won't be asked to record their name before they join a meeting.
    
  
5. After you make your changes, click **Save**.
    
  
 **Set the PIN length meetings**
  
    
    

1. Sign in to Office 365 with your work or school account.
    
  
2. Go to the **Office 365 admin center** > **Skype for Business**.
    
  
3. In the **Skype for Business admin center**, in the left navigation go to **dial-in conferencing** > **Microsoft bridge settings**.
    
  
4. On the **Microsoft bridge settings** page > **Security** > **PIN length** and enter the number of digits you want for the PIN and then click **Save**.
    
    > [!IMPORTANT]
      > The PIN can only be from 4 to 12 digits. 
 **Select whether to send email to your users**
  
    
    

1. Sign in to Office 365 with your work or school account.
    
  
2. Go to the **Office 365 admin center** > **Skype for Business**.
    
  
3. In the **Skype for Business admin center**, in the left navigation go to **Dial-in conferencing** > **Microsoft bridge settings**.
    
  
4. On the **Microsoft bridge settings** page, check or uncheck **Automatically send emails to users if their PSTN dial-in configuration changes** then click **Save**.
    
    See,  [Emails that are automatically sent to users when their dial-in conferencing settings change](emails-that-are-automatically-sent-to-users-when-their-dial-in-conferencing-sett.md)
    
  

## Want to know how to manage with Windows PowerShell?


- To save time or automate this, you can use the  [Set-CsDialinConferencingBridge](https://go.microsoft.com/fwlink/?LinkId=617686 ) cmdlet.
    
  
- Windows PowerShell is all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Office UNRESOLVED_TOKEN_VAL(365) using a single point of administration that can simplify your daily work when you have multiple tasks to do. To get started with Windows PowerShell, see these topics:
    
  -  [Six Reasons Why You Might Want to Use Windows PowerShell to Manage Office 365 ](https://go.microsoft.com/fwlink/?LinkId=525041)
    
  
  -  [Best ways to manage Office 365 with Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=525142)
    
  
- Windows PowerShell has many advantages in speed, simplicity, and productivity over only using the Office 365 admin center such as when you are making setting changes for many users at one time. Learn about these advantages in the following topics: 
    
  -  [An introduction to Windows PowerShell and Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525039)
    
  
  -  [Using Windows PowerShell to manage Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525453)
    
  
  -  [Using Windows PowerShell to do common Skype for Business Online management tasks](https://go.microsoft.com/fwlink/?LinkId=525038)
    
  

    > [!NOTE]
      > The Windows PowerShell module for Skype for Business Online enables you to create a remote Windows PowerShell session that connects to Skype for Business Online. This module, which is supported only on 64-bit computers, can be downloaded from the Microsoft Download Center at  [Windows PowerShell Module for Skype for Business Online.](https://go.microsoft.com/fwlink/?LinkId=294688)

## See also


#### Other Resources


  
    
    
 [Dial-in conferencing in Office 365](http://technet.microsoft.com/library/90d51188-0ba9-4dc4-bd6c-ae11dd1f8551%28Office.14%29.aspx)
