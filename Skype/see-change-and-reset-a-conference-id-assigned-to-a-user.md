---
title: See, change and reset a conference ID assigned to a user
ms.prod: OFFICE365
ms.assetid: 77d36233-2aab-4802-ba9c-e9a8885ea643
---


# See, change and reset a conference ID assigned to a user

A conference ID is automatically assigned to a user when they are set up for dial-in conferencing using Microsoft as the dial-in conferencing provider. The conference ID assigned can be either a static or dynamic and is sent in the meeting invite when the meeting is scheduled.
  
    
    

Static IDs are used when people in your organization like it when they don't want to remember a random number, they can select a certain number, or they have one that's easy to remember. When dynamic conference IDs are used, each meeting that a user schedules will get assigned a unique conference ID. If you want to assign dynamic and not static conference IDs,  [Using dial-in conferencing dynamic IDs in your organization](using-dial-in-conferencing-dynamic-ids-in-your-organization.md).
Although a static conference ID will be automatically created and assigned to a user, there may be times when a user doesn't want to use this one and you want to set it to a certain number or if your users can't remember or have lost their conference ID, you can use the Skype for Business admin center and Windows PowerShell to view, change, and reset their conference ID.
  
    
    

An email will be sent to the user with the conference ID and the default dial-in conferencing phone numbers, or if you reset the conference ID a different email will be sent that will include the conference ID but won't include a PIN.
## 


### To view the conference ID

You can view their conference ID and send it to them.
  
    
    

1. Sign in to Office 365 with your work or school account.
    
  
2. Go to the **Office 365 admin center** > **Skype for Business**.
    
  
3. In the **Skype for Business admin center**> **Dial-in conferencing**, in the user list, select the user who needs the conference ID.
    
  
4. In the Action page, look under **Conference ID**.
    
    > [!TIP]
      > You can send all of the conferencing information to the user in an email that includes the conference ID and dial-in phone numbers by clicking the **Send conference info via email** link after you select the user on the **Dial-in users** page.

    You can use Windows PowerShell to view the conference ID for a user, run:
    


  ```
  
Get-CsOnlineDialInConferencingUser -Identity "Amos Marble"  
  ```


    See  [Get-CsOnlineDialInConferencingUser](https://go.microsoft.com/fwlink/?LinkId=617693 ) to learn more about the cmdlet.
    
  

### To assign or change the conference ID

You can assign or change a conference ID for a user if, for example, someone wants a conference ID that's easy to remember.
  
    
    

> [!NOTE]
> The Skype for Business admin center can't be used to edit a conference ID that has been automatically created, but you can use Windows PowerShell to edit or change a conference ID that you have set. 
  
    
    


1. To edit or change the conference ID for a user, run:
    
    > [!TIP]
      > A conference ID must contain 7 digits and you can't change it in the Skype for Business admin center or using Windows PowerShell. 

  ```
  
Set-CsOnlineDialInConferencingUser -Identity "Amos Marble"  -ConferenceId 8271964
  ```


### To reset the conference ID

You can reset a conference ID for a user if, for example, if they forget it.
  
    
    

1. Sign in to Office 365 with your work or school account.
    
  
2. Go to the **Office 365 admin center** > **Skype for Business**.
    
  
3. In the **Skype for Business admin center**> **Dial-in conferencing**, in the Action page under **Conference ID** click **Reset**.
    
  
4. In the ** Reset conference ID?** window, click **Yes**. A conference ID will be automatically created and an email sent to the user with the new conference ID.
    
    You can reset the conference ID for a user by using the Windows PowerShell. To do this, run:
    


  ```
  
Set-CsOnlineDialInConferencingUser -Identity "Amos Marble"  -ResetLeaderPIN 8271964
  ```


## What else should you know?


-     > [!IMPORTANT]
      >  After a new conference ID is created or one is reset, the old conference ID can't be used by callers. You should notify users to reschedule their existing meeting invites to make sure the new conference ID is added to the invitations. The users can use the Skype for Business Meeting Migration Tool to update their existing meetings. To see how to download, install, and run the tool, see:>  [Meeting Update Tool for Skype for Business and Lync](http://technet.microsoft.com/library/2b525fe6-ed0f-4331-b533-c31546fcf4d4%28Office.14%29.aspx)>  [Skype for Business Online, Meeting Migration Tool (64-bit)](http://go.microsoft.com/fwlink/?LinkID=626047)>  [Skype for Business Online, Meeting Migration Tool (32-bit)](https://go.microsoft.com/fwlink/?LinkID=626046)
- See  [Set-CsOnlineDialInConferencingUser](https://go.microsoft.com/fwlink/?LinkId=617688 ) to learn more about the cmdlet.
    
  
- The conference ID must meet the length in digits set on the dial-in conferencing bridge. You can't use alphabetic and special characters in conference IDs only numbers can be used.
    
  
- The conference ID for all of your dial-in conferencing users will be 7 digits by default. And the number of digits can't be changed.
    
  
- If the user is moved from Microsoft as the dial-in conferencing provider to a third-party audio conferencing provider or the dial-in conferencing provider is set to **None**, the conference ID will no longer work. See  [Assign a third-party as the dial-in conferencing provider](assign-a-third-party-as-the-dial-in-conferencing-provider.md) or [Change the dial-in conferencing provider for users](http://technet.microsoft.com/library/9b74f053-4d23-485f-9232-3d30370a8c6e%28Office.14%29.aspx).
    
  

## Want to know how to manage with Windows PowerShell?


- When it comes to Windows PowerShell is all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Office 365 and Skype for Business Online using a single point of administration that can simplify your daily work, when you have multiple tasks to do. To get started with Windows PowerShell, see these topics:
    
  -  [An introduction to Windows PowerShell and Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525039)
    
  
  -  [Six Reasons Why You Might Want to Use Windows PowerShell to Manage Office 365 ](https://go.microsoft.com/fwlink/?LinkId=525041)
    
  
- Windows PowerShell has many advantages in speed, simplicity, and productivity over only using the Office 365 admin center such as when you are making setting changes for many users at one time. Learn about these advantages in the following topics:
    
  -  [Best ways to manage Office 365 with Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=525142)
    
  
  -  [Using Windows PowerShell to manage Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525453)
    
  
  -  [Using Windows PowerShell to do common Skype for Business Online management tasks](https://go.microsoft.com/fwlink/?LinkId=525038)
    
  

## Related Topics

 [Set up dial-in or PSTN conferencing for Skype for Business](set-up-dial-in-or-pstn-conferencing-for-skype-for-business.md)
  
    
    

