---
title: Enable users to record their name when they join a meeting
ms.prod: OFFICE365
ms.assetid: 1d649328-ada7-422d-a074-d6da4da36970
---


# Enable users to record their name when they join a meeting

When you are setting up dial-in conferencing in Skype for Business Online, you will receive phone numbers and what is called a dial-in or audio conferencing bridge. A conferencing bridge can contain one or more phone numbers that can be a dedicated or shared phone number.
  
    
    

The conferencing bridge answers a call for a user who is dialing in to a meeting using a phone. The conferencing bridge answers the caller with voice prompts from an auto attendant and then, depending on their settings, can play notifications, ask callers to record their name, and sets up the PIN security for meeting organizers. PINs are given to a meeting organizer that allows them to start a meeting. However, you can set it up so a PIN isn't required to start a meeting.
## Set whether callers should record their name


1. Sign in to Office 365 with your work or school account.
    
  
2. Go to the **Office 365 admin center** > **Skype for Business**.
    
  
3. In the **Skype for Business admin center**, in the left navigation, go to **Dial-in conferencing** > **Microsoft bridge settings**.
    
  
4. Under **Meeting join experience** > **Enable meeting entry and exit notifications to be turned on**
    
  - **Checked** Callers will be asked to record their name before they enter the meeting. This is selected by default.
    
  
  - **Unchecked** Callers won't be asked to record their name before they enter the meeting.
    
  
5. After you make your changes, click **Save**.
    
  

## Want to know how to manage with Windows PowerShell?


- To save time or automate this, you can use the  [Set-CsOnlineDialInConferencingTenantSettings ](https://go.microsoft.com/fwlink/?LinkId=715757) cmdlet.
    
  
-  Windows PowerShell is all about managing users and what users are allowed to do. With Windows PowerShell, you can manage Office 365 using a single point of administration that can simplify your daily work when you have multiple tasks to do. To get started with Windows PowerShell, see these topics:
    
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
