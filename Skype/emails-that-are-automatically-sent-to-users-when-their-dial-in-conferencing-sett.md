---
title: Emails that are automatically sent to users when their dial-in conferencing settings change
ms.prod: OFFICE365
ms.assetid: 1b46da6d-f93a-4cc0-9ae8-af765935b007
---


# Emails that are automatically sent to users when their dial-in conferencing settings change

Emails will be automatically sent to users who are  [Set up dial-in or PSTN conferencing for Skype for Business](set-up-dial-in-or-pstn-conferencing-for-skype-for-business.md) using Microsoft as the dial-in conferencing provider.
  
    
    

By default, there are four types of email that will be sent to your users who are enabled for dial-in conferencing. However, if you want to limit the number of emails sent to users, you can turn it off. Dial-in conferencing in Skype for Business Online will send email to your users' email when:
- **A **Skype for Business PSTN Conferencing** license is assigned to them or when you are changing the dial-in conferencing provider to Microsoft.**
    
     This email includes the conference ID, the default conference phone number for the meetings, the dial-in conferencing PIN for the user, and the instructions and link to use the Skype for Business Online Meeting Update Tool that is used to update existing meetings for the user. See [Assign Skype for Business licenses](assign-skype-for-business-licenses.md) or [Assign Microsoft as the dial-in conferencing provider](assign-microsoft-as-the-dial-in-conferencing-provider.md).
    
    > [!NOTE]
      > If your organization has been enabled for dynamic conference IDs, all of a user's meetings that they schedule will have unique conference IDs. You can set up  [Using dial-in conferencing dynamic IDs in your organization](using-dial-in-conferencing-dynamic-ids-in-your-organization.md). 

    Here is an example of this email:
    
     ![Skype for Business Verify License](images/17913e03-8b4a-4563-b58d-2f09b65fbcaa.png)
  

    You can find out more about Skype for Business licensing by seeing  [Skype for Business add-on licensing](skype-for-business-add-on-licensing.md).
    
  
- **The conference ID or default conference phone number of a user changes.**
    
    This email contains the conference ID, default conference phone number, and the instructions and link to use the Skype for Business Online Meeting Update Tool that is used to update existing meetings for the user. But this email doesn't include the user's dial-in conferencing PIN. See  [Reset a conference ID for a user](reset-a-conference-id-for-a-user.md).
    
    > [!NOTE]
      > If your organization has been enabled for dynamic conference IDs, all of a user's meetings that they schedule will have unique conference IDs. You can set up  [Using dial-in conferencing dynamic IDs in your organization](using-dial-in-conferencing-dynamic-ids-in-your-organization.md). 

    Here is an example of this email:
    
     ![Dial-in conferencing info has changed.](images/d6d3e028-d9fb-48c4-97c0-a73d6ade5ea3.png)
  

  

  
- **The dial-in conferencing PIN of a user is reset.**
    
    This email contains the organizer's dial-in conferencing PIN, the existing conference ID, and default conference phone number for the user. See  [Reset the dial-in conferencing PIN for a user](reset-the-dial-in-conferencing-pin-for-a-user.md)
    
    > [!NOTE]
      > If your organization has been enabled for dynamic conference IDs, all of a user's meetings that they schedule will have unique conference IDs. You can set up  [Using dial-in conferencing dynamic IDs in your organization](using-dial-in-conferencing-dynamic-ids-in-your-organization.md). 

    Here is an example of this email:
    
     ![Dial-in conferencing PIN changed.](images/df8df4f8-d11f-41b8-9187-99e66a88831b.png)
  

  

  
- **A user's license is removed or when their dial-in conferencing provider changes from Microsoft to other provider or None**
    
    This happens when the **Skype for Business PSTN Conferencing** license is removed from a user or when changing the dial-in conferencing provider of a user from Microsoft to a third-party audio conferencing provider or when setting the provider to **None**. This email contains the instructions and information for the user to use the Skype for Business Online Meeting Update Tool to remove dial-in conferencing specific information, such as the default conference phone number or conference ID.
    
    See  [Assign or remove licenses for Office 365 for business](http://technet.microsoft.com/library/997596b5-4173-4627-b915-36abac6786dc%28Office.14%29.aspx) or [Assign a third-party as the dial-in conferencing provider](assign-a-third-party-as-the-dial-in-conferencing-provider.md).
    
    Here is an example of this email:
    
     ![Dial-in conferencing is turned off.](images/4ebc8ae6-b516-452e-8d27-6177e145daba.png)
  

  

  

## Make changes to the email messages that are sent to them

You can make changes to the email that is automatically sent to your users including the email address and the display name that is included in the  *From*  contact information. By default, the sender of the emails will be from Office 365 but you can change the email address and display name using Windows PowerShell and the [Set-CsOnlineDialInConferencingTenantSettings](https://go.microsoft.com/fwlink/?LinkId=627285) cmdlet. To make changes to the email address that is sending the email to the users you must:
  
    
    

- Enter the email address in the  _SendEmailFromAddress_ parameter.
    
  
- Enter the email display name in the  _SendEmailFromDisplayName_ parameter.
    
    
    
  
- Set the  _SendEmailOverride_parameter to  _True_.
    
  
You can make changes to the email sent to users, such as the email address that the email is sent from and the display name for the email by running:
  
    
    



```

Set-CsOnlineDialInConferencingTenantSetting -SendEmailOverride $true -SendEmailFromAddress amos.marble -SendEmailFromDisplayName "Amos Marble"
```


> [!NOTE]
>  If you want to change the email address information, you need to make sure that the inbound email policies of your environment allow emails that come from the custom specified from address.> If you decide to override the  *From*  contact information, you should verify that the emails are correctly sent to users. You can do this by testing this with one user in your organization.
  
    
    

You can use the  [Set-CsOnlineDialInConferencingTenantSettings](https://go.microsoft.com/fwlink/?LinkId=627285) cmdlet to manage other settings for your organization including email.
  
    
    

## What if you don't want email to be sent to them?

When you disable sending emails to users, email won't be sent even when a user gets assigned a license. If this is the case, the conference ID, default conferencing phone number and more importantly, their dial-in conferencing PIN won't be sent to the user. When this happens, you must tell the user by sending them a separate email or by calling them.
  
    
    
By default, emails will be sent to your users, but if you want to prevent them from receiving email for dial-in conferencing use can use the Skype for Business admin center or Windows PowerShell. 
  
    
    
 **Using the Skype for Business admin center**
  
    
    

1. Sign in to Office 365 with your work or school account.
    
  
2. Go to the **Office 365 admin center** > **Skype for Business**.
    
  
3. In the **Skype for Business admin center**, in the left navigation go to **Dial-in conferencing** > **Microsoft bridge settings**.
    
  
4. On the **Microsoft bridge settings** page, check or uncheck **Automatically send emails to user if their PSTN dial-in conferencing information changes**. 
    
  
5. Click **Save**. 
    
  
 **Using Windows PowerShell**
  
    
    

1. Run the following to disable sending all of your users email:
    
  ```
  
Set-CsOnlineDialInConferencingTenantSetting -AutomaticallySendEmailsToUsers $false
  ```

You can use the  [Set-CsOnlineDialInConferencingTenantSettings](https://go.microsoft.com/fwlink/?LinkId=627285) to manage other settings for your organization including email.
  
    
    

## What else should you know about this email?


- For more on enabling and disabling automatically sending email to your users, see  [Enable or disable sending emails when dial-in conferencing settings change](enable-or-disable-sending-emails-when-dial-in-conferencing-settings-change.md).
    
  
- Sometimes users lose their dial-in information and you need to be able to send them all of their dial-in information to them. You can do this by using the Skype for Business admin center and clicking **Send conference info via email** under the dial-in properties for a user. See [Send an email to a user with their dial-in conferencing information](send-an-email-to-a-user-with-their-dial-in-conferencing-information.md). However, this information doesn't include the dial-in conferencing PIN.
    
    Here is an example of this email that will be sent to them:
    
     ![Dial-in conferencing email](images/81fe4e09-a346-4469-8cc5-c6d65f739b73.png)
  

  

  

## Want to know how to manage with Windows PowerShell?


- By default, the sender of the emails will be from Office 365 but you can change the email address and display name using Windows PowerShell and the  [Set-CsOnlineDialInConferencingTenantSettings](https://go.microsoft.com/fwlink/?LinkId=627285) cmdlet.
    
  

- Windows PowerShell is all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Office 365 using a single point of administration that can simplify your daily work when you have multiple tasks to do. To get started with Windows PowerShell, see these topics:
    
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


  
    
    
 [Enable or disable sending emails when dial-in conferencing settings change](enable-or-disable-sending-emails-when-dial-in-conferencing-settings-change.md)
  
    
    
 [Send an email to a user with their dial-in conferencing information](send-an-email-to-a-user-with-their-dial-in-conferencing-information.md)
