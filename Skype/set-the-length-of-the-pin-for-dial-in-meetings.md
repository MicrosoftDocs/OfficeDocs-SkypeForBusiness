---
title: Set the length of the PIN for dial-in meetings
ms.prod: OFFICE365
ms.assetid: b86d31c6-1543-478f-b8c6-4b71e708403a
---


# Set the length of the PIN for dial-in meetings

When you are setting up dial-in conferencing in Skype for Business Online, you will receive phone numbers and what is called a dial-in or audio conferencing bridge. A conferencing bridge can contain one or more phone numbers. The phone number you set will be included on the meeting invite.
  
    
    

The dial-in conferencing or audio conferencing bridge answers a call for a user that is dialing into a meeting using a phone. It answers the caller with voice prompts from a system auto attendant and then depending on your settings can play notifications and ask callers to record their name. Skype for Business Online Microsoft bridge settings allows you to change the settings for meeting notifications and the meeting join experience, and set the length of the PINs that are used by meeting organizers. Meeting organizers use PINs to start meetings.
## Setting the PIN length

 **Set the PIN length for meeting organizers**
  
    
    

1. Sign in to Office 365 with your work or school account.
    
  
2. Go to the **Office 365 admin center** > **Skype for Business**.
    
  
3. In the **Skype for Business admin center**, in the left navigation go to **Dial-in conferencing** > **Microsoft bridge settings**.
    
  
4. Under **Security** > **PIN length** > enter the number of digits you want for the PIN and then click **Save**.
    
  

> [!NOTE]
> A PIN is different from a conference ID. Conference IDs are used by callers when they join the meeting. They are used to identify the meeting. The PIN is used to authenticate a caller as the meeting organizer. 
  
    
    


## Want to know more about PIN settings?


- PINs can be from 4 to 12 digits - the default is 5. Numbers are only used when creating PINs. Letters and special characters aren't used.
    
  
- A PIN is only required for the meeting organizer when a Skype for Business client user hasn't already started the meeting. If everyone is dialing in to the meeting, then the PIN is required for the meeting organizer to start the meeting.
    
  
- PIN security settings are applied to all of the phone numbers that are associated with a Microsoft bridge. They will be applied to all meetings that use the phone numbers associated with a given bridge. 
    
  

## Want to know how to manage with Windows PowerShell?


- To save time or automate this, you can use the  [Set-CsOnlineDialInConferencingTenantSettings](https://go.microsoft.com/fwlink/?LinkId=715757) cmdlet.
    
  
- To set the number of digits in the PIN to 8:  `Set-CsOnlineDialInConferencingTenantSettings -PinLength 8`
    
  
- Windows PowerShell is all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Office 365 using a single point of administration that can simplify your daily work when you have multiple tasks to do. To get started with Windows PowerShell, see these topics:
    
  -  [Six Reasons Why You Might Want to Use Windows PowerShell to Manage Office 365 ](https://go.microsoft.com/fwlink/?LinkId=525041)
    
  
  -  [Best ways to manage Office 365 with Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=525142)
    
  
- Windows PowerShell has many advantages in speed, simplicity, and productivity over only using the Office 365 admin center such as when you are making setting changes for many users at one time. Learn about these advantages in the following topics: 
    
  -  [An introduction to Windows PowerShell and Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525039)
    
  
  -  [Using Windows PowerShell to manage Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525453)
    
     [Using Windows PowerShell to manage Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525453)
    
  
  -  [Using Windows PowerShell to do common Skype for Business Online management tasks](https://go.microsoft.com/fwlink/?LinkId=525038)
    
  

    > [!NOTE]
      > The Windows PowerShell module for Skype for Business Online enables you to create a remote Windows PowerShell session that connects to Skype for Business Online. This module, which is supported only on 64-bit computers, can be downloaded from the Microsoft Download Center at  [Windows PowerShell Module for Skype for Business Online.](https://go.microsoft.com/fwlink/?LinkId=294688)

## See also


#### Other Resources


  
    
    
 [Dial-in conferencing in Office 365](http://technet.microsoft.com/library/90d51188-0ba9-4dc4-bd6c-ae11dd1f8551%28Office.14%29.aspx)
