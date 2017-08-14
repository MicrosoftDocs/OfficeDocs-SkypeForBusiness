---
title: Enable or disable sending emails when dial-in conferencing settings change
ms.prod: OFFICE365
ms.assetid: 26ea19d3-e420-4fc1-baa3-2692d17e5e1d
---


# Enable or disable sending emails when dial-in conferencing settings change

Skype for Business dial-in conferencing by default will send email to the users when they are enabled for dial-in conferencing. There may be times though when you want to reduce the number of emails that are sent to users, and in that case you can disable this.
  
    
    

If you disable sending emails, all dial-in conferencing emails won't be sent to your users including emails for when users are enabled or disabled for dial-in conferencing, when their PIN is reset, when the conference ID and the default conferencing phone number changes.
Here is an example of the email that is sent to users when they are enabled for dial-in conferencing:
  
    
    


  
    
    
![Dial-in conferencing email](images/81fe4e09-a346-4469-8cc5-c6d65f739b73.png)
  
    
    

  
    
    

  
    
    

## When are emails being sent to your users?


- There are several emails that are sent to users in your organization after they are enabled for dial-in conferencing:
    
  - When a **Skype for Business PSTN Conferencing** license is assigned to them.
    
  
  - When you manually reset the user's dial-in conferencing PIN.
    
  
  - When you manually reset the user's conference ID.
    
  
  - When the **Skype for Business PSTN Conferencing** license is removed from them.
    
  
  - When the dial-in conferencing provider of a user is changed from Microsoft to another provider or **None**.
    
  
  - When the dial-in conferencing provider of a user is changed to Microsoft.
    
  

## Enable or disable email from being sent to dial-in users

You can use the Skype for Business admin center or Windows PowerShell to enable or disable email from being sent to users.
  
    
    
 **Use the Skype for Business admin center**
  
    
    

1. Sign in to Office 365 with your work or school account.
    
  
2. Go to the **Office 365 admin center** > **Skype for Business** and in the left navigation click **Dial-in conferencing**.
    
  
3. On the **Microsoft bridge settings** page, check or uncheck the **Automatically send emails to users if any of the dial-in configuration changes**.
    
  
4. Click **Save**.
    
    > [!TIP]
      > You can also send email to the user with the dial-in conferencing settings, by going to the user's properties > **Dial-in conferencing** > **Send conference info via email**. > If you do this, an email will be sent that only includes conference ID and conference phone number, but the PIN won't be included. > See,  [Send an email to a user with their dial-in conferencing information](send-an-email-to-a-user-with-their-dial-in-conferencing-information.md). 
 **Use the Windows PowerShell**
  
    
    

- Run the following to disable sending emails: 
    
  ```
  
Set-CsOnlineDialInConferencingTenantSetting -AutomaticallySendEmailsToUsers $false
  ```


    To help you with this cmdlet, see  [Set-CsOnlineDialInConferencingTenantSettings](https://go.microsoft.com/fwlink/?LinkId=715757).
    
  

## What else should you know?


- When automatic emails are disabled, you can still manually trigger sending an email with the conference ID and phone number using the Skype for Business admin center. However, if you do this the PIN won't be included. If you want to reset the dial-in conferencing PIN and sending emails is disabled, you will need to send it to the user in another way.
    
  
- By default, the sender of the emails will be from Office 365 but you can change the email address and display name using Windows PowerShell and also use the  [Set-CsOnlineDialInConferencingTenantSettings](https://go.microsoft.com/fwlink/?LinkId=715757) cmdlet.
    
    > [!NOTE]
      >  If you want to change the email address information, you need to make sure that the inbound email policies of your environment allow emails that come from the custom specified from address.

  - Enter the email address in the  _SendEmailFromAddress_ parameter.
    
  
  - Enter the email display name in the  _SendEmailFromDisplayName_ parameter.
    
  
  - Set the  _SendEmailOverride_ parameter to _True_.
    
  
  -  `Set-CsOnlineDialInConferencingTenantSetting -SendEmailOverride $true -SendEmailFromAddress amos.marble@contoso.com -SendEmailFromDisplayName "Amos Marble"`
    
  
- Sending email to your users can be disabled using the Skype for Business admin center or the Windows PowerShell.
    
  

## Want to know how to manage with Windows PowerShell?


- You can use these cmdlets too to save time or automate this.
    
  -  [Get-CsOnlineDialInConferencingTenantSettings](https://go.microsoft.com/fwlink/?LinkId=715760)
    
  
  -  [Remove-CsOnlineDialInConferencingTenantSettings](https://go.microsoft.com/fwlink/?LinkId=715759)
    
  
  -  [Get-CsOnlineDialinConferencingTenantConfiguration](https://go.microsoft.com/fwlink/?LinkId=715758)
    
  
  -  [Get-CsOnlineDialInConferencingTenantSettings](https://go.microsoft.com/fwlink/?LinkId=715760)
    
  
-  Windows PowerShell is all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Office UNRESOLVED_TOKEN_VAL(365) using a single point of administration that can simplify your daily work when you have multiple tasks to do. To get started with Windows PowerShell, see these topics:
    
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
