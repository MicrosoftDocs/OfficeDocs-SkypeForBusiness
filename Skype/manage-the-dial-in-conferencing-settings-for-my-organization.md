---
title: Manage the dial-in conferencing settings for my organization
ms.prod: OFFICE365
ms.assetid: bc9bd328-c5b2-44e5-af15-e02bf00e1c81
---


# Manage the dial-in conferencing settings for my organization

It might be easier for you to see all of the dial-in conferencing settings in one place. 
  
    
    


## Assign a dial-in conferencing license


> [!NOTE]
> You can't assign licenses using the **Skype for Business admin center**, you must use the Office 365 admin center. 
  
    
    

 **To assign a license for a user**
  
    
    

1. Sign in to Office 365 with your work or school account.
    
  
2. In the left navigation of the Office 365 admin center, go to **Users** > **Active users** > and then select the user or users from the list of available users.
    
    > [!NOTE]
      > If you are assigning licenses to up to 20 users at the same time, you can use the **Select a view** drop-down then choose one of the options or create your own view. Then click **Edit**, **Next** twice then select the license and click **Submit**. You can also assign licenses to multiple users by using Windows Powershell. For for instructions and sample PowerShell scripts, see  [Assign Skype for Business licenses](assign-skype-for-business-licenses.md). 
3. In the Action pane under **Assigned license**, click **Edit**. 
    
  
4. On the **Assign License** page, check **Skype for Business PSTN Conferencing** and then click **Save**. For more on licensing, see  [Skype for Business add-on licensing](skype-for-business-add-on-licensing.md).
    
  

> [!NOTE]
> After you assign the license, Microsoft might not appear initially in the drop-down as a dial-in conferencing provider. If this happens, either log out of the Office 365 admin center or press CTRL+F5 to refresh the browser window. 
  
    
    

See  [Assign Skype for Business licenses](assign-skype-for-business-licenses.md).
  
    
    

## Assign a conference ID for a user

A conference ID is automatically assigned to a user when they are set up for dial-in conferencing using Microsoft as the dial-in conferencing provider. The conference ID assigned can be either a static or dynamic and is sent in the meeting invite when the meeting is scheduled. 
  
    
    
Static IDs are used when people in your organization like it when they don't want to remember a random number, they can select a certain number, or they have one that's easy to remember. When dynamic conference IDs are used, each meeting that a user schedules will get assigned a unique conference ID. If you want to assign dynamic and not static conference IDs,  [Using dial-in conferencing dynamic IDs in your organization](using-dial-in-conferencing-dynamic-ids-in-your-organization.md).
  
    
    
The Skype for Business admin center can't be used to assign a conference ID to a user, but you can use the Windows PowerShell cmdlet to do this.
  
    
    
To set the conference ID for a user, run:
  
    
    



```

Set-CsOnlineDialInConferencingUser -Identity "Amos Marble"  -ConferenceId 8271964 
```


> [!IMPORTANT]
> A conference ID must contain 7 digits and you can't change it in the Skype for Business admin center or using Windows PowerShell. 
  
    
    

See  [Set-CsOnlineDialInConferencingUser](https://go.microsoft.com/fwlink/?LinkId=617688 ) to learn more about the cmdlet.
  
    
    

> [!IMPORTANT]
>  After a new conference ID is created, the old conference ID can't be used by callers. You should notify users to reschedule their existing meeting invites to make sure the new conference ID is added to the invitations. The users can use Skype for Business Meeting Migration Tool to update their existing meetings. To see how to download, install and run the Lync Meeting Update Tool, see:>  [Meeting Update Tool for Skype for Business and Lync](http://technet.microsoft.com/library/2b525fe6-ed0f-4331-b533-c31546fcf4d4%28Office.14%29.aspx)>  [Skype for Business Online, Meeting Migration Tool (64-bit)](http://go.microsoft.com/fwlink/?LinkID=626047)>  [Skype for Business Online, Meeting Migration Tool (32-bit)](https://go.microsoft.com/fwlink/?LinkID=626046)
  
    
    

See  [See, change and reset a conference ID assigned to a user](see-change-and-reset-a-conference-id-assigned-to-a-user.md).
  
    
    

## Change the dial-in conferencing provider from Microsoft to a third-party provider


1. Sign in to Office 365 with your work or school account.
    
  
2. Go to the **Office 365 admin center** > **Skype for Business**.
    
  
3. In the **Skype for Business admin center**, in the left navigation go to **Dial-in conferencing** > **Dial-in users** and then and select the user you want to change the dial-in conferencing provider for.
    
  
4. In the Action pane, click **Edit**. 
    
  
5. In the **Skype for Business admin center**, in the left navigation go to Dial-in conferencing > **Provider name** drop-down, and then select the dial-in conferencing provider for the user.
    
    > [!NOTE]
      > You can only select Microsoft as the dial-in conferencing provider or **None** if you have selected multiple users.
6. Click **Save**. 
    
  
See  [Change the dial-in conferencing provider for users](http://technet.microsoft.com/library/9b74f053-4d23-485f-9232-3d30370a8c6e%28Office.14%29.aspx).
  
    
    

## Enable or disable emails from being sent to dial-in users

You can use the Skype for Business admin center or Windows PowerShell to enable or disable email from being sent to users.
  
    
    
 **Use the Skype for Business admin center**
  
    
    

1. Sign in to Office 365 with your work or school account.
    
  
2. Go to the **Office 365 admin center** > **Skype for Business** and in the left navigation click **Dial-in conferencing**
    
  
3. On the **Microsoft bridge settings** page, check or uncheck the **Automatically send emails to users if any of the dial-in configuration changes**
    
  
4. Click **Save**.
    
    You can also send emails to the user with the dial-in conferencing settings, by going to the user's properties > **Dial-in conferencing** > **Send conference info via email**. The conference ID and default dial-in conferencing phone number is included on the meeting invite but not the PIN.
    
    See  [Send an email to a user with their dial-in conferencing information](send-an-email-to-a-user-with-their-dial-in-conferencing-information.md).
    
  
 **Use the Windows PowerShell**
  
    
    

- You can also use the Windows PowerShell and run: 
    
  ```
  
Set-CsOnlineDialInConferencingTenantSetting -AutomaticallySendEmailsToUsers $true|$false
  ```


    You can use the  [Set-CsOnlineDialInConferencingTenantSettings](https://go.microsoft.com/fwlink/?LinkId=627285) to manage other settings for your organization including email.
    
  

## Change the senders contact information of email messages sent to users

You can make changes to the email that is automatically sent to your users including the actual email address and the display name of the sender's contact information. By default, the sender of the emails will be from Office 365 but you can change the email address and display name using Windows PowerShell and the  [Set-CsOnlineDialInConferencingTenantSettings](https://go.microsoft.com/fwlink/?LinkId=627285) cmdlet. To make changes to the email address that is sending the email to the users you must:
  
    
    

- Enter the email address in the  _SendEmailFromAddress_ parameter.
    
  
- Enter the email display name in the  _SendEmailFromDisplayName_ parameter.
    
    
    
  
- Set the  _SendEmailOverride_parameter to  _True_.
    
  
You can make changes to the email sent to users, such as the email address that the email is sent from or the display name for the email by running:
  
    
    



```
Set-CsOnlineDialInConferencingTenantSetting -SendEmailOverride $true -SendEmailFromAddress amos.marble@contoso.com -SendEmailFromDisplayName "Amos Marble"
```

If you want to change the email address information, you need to make sure that the inbound email policies of your organization allow emails that come from the custom email address.
  
    
    
You can use the  [Set-CsOnlineDialInConferencingTenantSettings](https://go.microsoft.com/fwlink/?LinkId=627285) to manage other settings for your organization including email.
  
    
    
See  [Emails that are automatically sent to users when their dial-in conferencing settings change](emails-that-are-automatically-sent-to-users-when-their-dial-in-conferencing-sett.md).
  
    
    

## Reset the meeting conference ID


1. Sign in to Office 365 with your work or school account.
    
  
2. Go to the **Office 365 admin center** > **Skype for Business**.
    
  
3. In the **Skype for Business admin center**> **Dial-in conferencing**, in the Action page under **Conference ID** click **Reset**.
    
  
4. In the ** Reset conference ID?** window, click **Yes**. A conference ID will be automatically created and an email sent to the user with the new conference ID if sending email to your users is enabled. It's enabled by default.
    
    > [!IMPORTANT]
      >  After a new conference ID is created, the old conference ID can't be used by callers. You should notify users to reschedule their existing meeting invites to make sure the new conference ID is added to the invitations. The users can use Skype for Business Meeting Migration Tool to update their existing meetings. To see how to download, install and run the Lync Meeting Update Tool, see:>  [Meeting Update Tool for Skype for Business and Lync](http://technet.microsoft.com/library/2b525fe6-ed0f-4331-b533-c31546fcf4d4%28Office.14%29.aspx)>  [Skype for Business Online, Meeting Migration Tool (64-bit)](http://go.microsoft.com/fwlink/?LinkID=626047)>  [Skype for Business Online, Meeting Migration Tool (32-bit)](https://go.microsoft.com/fwlink/?LinkID=626046)
See  [Reset a conference ID for a user](reset-a-conference-id-for-a-user.md).
  
    
    

## Reset a conference organizer's PIN

Static IDs are used when people in your organization like it when they don't want to remember a random number, they can select a certain number, or they have one that's easy to remember. When dynamic conference IDs are used, each meeting that a user schedules will get assigned a unique conference ID. If you want to assign dynamic and not static conference IDs,  [Using dial-in conferencing dynamic IDs in your organization](using-dial-in-conferencing-dynamic-ids-in-your-organization.md).
  
    
    
Although a static conference ID will be automatically created and assigned to a user, there may be times when a user doesn't want to use this one and you want to set it to a certain number or if your users can't remember or have lost their conference ID, you can use the Skype for Business admin center and Windows PowerShell to view, change, and reset their conference ID.
  
    
    

1. Sign in to Office 365 with your work or school account.
    
  
2. Go to the **Office 365 admin center** > **Skype for Business** and in the left navigation click **Dial-in conferencing**
    
  
3. Click on **Dial-in users**, select the user that you want to reset the PIN for.
    
  
4. In the Action pane, click **Reset PIN**.
    
    Users will receive an email with their PIN when they're enabled for dial-in conferencing or when the PIN is reset. But if you have disabled automatically sending emails, then a PIN reset email won't be sent to a user and you will have to manually send the PIN to the user. The PIN will only be shown once after it has been reset. Once it's displayed just after being reset, the PIN won't be shown anymore on the user properties and instead ***** will be shown.
    
    
    
  
See  [Reset the dial-in conferencing PIN for a user](reset-the-dial-in-conferencing-pin-for-a-user.md).
  
    
    

## Send an email with dial-in conferencing information to a user


1. Sign in to Office 365 with your work or school account.
    
  
2. Go to the **Office 365 admin center** > **Skype for Business** and in the left navigation click **Dial-in conferencing**
    
  
3. Click on **Dial-in users**, select the user that you want to reset the PIN for.
    
  
4. In the Action pane, click **Send conference info via email**.
    
    > [!NOTE]
      > When you do this, the dial-in conferencing PIN isn't sent to the user. 
See  [Send an email to a user with their dial-in conferencing information](send-an-email-to-a-user-with-their-dial-in-conferencing-information.md).
  
    
    

## Setting the default dial-in conferencing phone number for meeting organizers

 **To set the default dial-in conferencing phone number for meeting organizers when you are enabling a user for dial-in conferencing**
  
    
    

1. Sign in to Office 365 with your work or school account.
    
  
2. Go to the **Office 365 admin center** > **Skype for Business**.
    
  
3. In the left navigation go to **Dial-in conferencing** > **Dial-in users**. Select the user that you want to enable for dial-in conferencing.
    
  
4. In the Action pane, in the user's properties click **Edit**.
    
  
5. On the **Properties** page, under **Provider name** use drop-down to select the dial-in conferencing provider.
    
  - If you select Microsoft as the dial-in conferencing provider, you can choose the default dial-in conferencing phone number from the list.  
    
  
  - If you select a third-party ACP as the dial-in conferencing provider, you will need to manually enter the Toll and if required, the Toll-free phone number. These phone numbers will be the default phone number.
    
    The default dial-in conferencing phone number of a user is the number that is shown on the meeting invite when they schedule a meeting.
    
  
6. Click **Save**. 
    
  
See  [Set the dial-in phone numbers for meeting organizers that are included on invites](set-the-dial-in-phone-numbers-for-meeting-organizers-that-are-included-on-invite.md).
  
    
    
 **To set the default dial-in conferencing phone number for meeting organizers after you have enabled a user for dial-in conferencing**
  
    
    

1. Sign in to Office 365 with your work or school account.
    
  
2. Go to the **Office 365 admin center** > **Skype for Business**.
    
  
3. In the **Skype for Business admin center**, in the left navigation go to **Dial-in conferencing** > **Dial-in users**, select the user you want and in the Action page, click **Edit**.
    
  
4. On the **Properties** page, under **Provider name** use drop-down to select the dial-in conferencing provider
    
  - If the user uses Microsoft as the dial-in conferencing provider, you can choose the default dial-in conferencing phone number from the list.  
    
  
  - If the user uses a third-party ACP as the dial-in conferencing provider, you will need to manually enter the Toll and if required, the Toll-free phone number.
    
    The default dial-in conferencing phone number of a user is the number that is shown on the meeting invite when they schedule a meeting.
    
  
5. Click **Save**. 
    
  
See  [Set the dial-in phone numbers for meeting organizers that are included on invites](set-the-dial-in-phone-numbers-for-meeting-organizers-that-are-included-on-invite.md).
  
    
    

## Setting dial-in conferencing bridge settings

 **Set the meeting experience when callers join a meeting**
  
    
    

1. Sign in to Office 365 with your work or school account.
    
  
2. Go to the **Office 365 admin center** > **Skype for Business**.
    
  
3. In the **Skype for Business admin center**, in the left navigation go to **dial-in conferencing** > **Microsoft bridge settings**.
    
  
4. Under **Meeting join experience** select the following actions:
    
  - **Enable meeting entry and exit notifications to be turned on** This is selected by default. However if you uncheck it, users that have already joined the meeting by default won't be notified when someone enters or leaves the meeting.
    
    This can be set on a meeting-by-meeting basis when a user joins a meeting using a Skype for Business client and they modify the **Announce when people enter or leave** setting in the Skype Meeting Options menu of the meeting.
    
  
  - **Ask callers to record their name before joining the meeting** This is selected by default. However, if you uncheck it, callers won't be asked to record their name before they join a meeting.
    
  
5. After you make your changes, click **Save**.
    
  
See  [Change the settings for a Microsoft dial-in conferencing bridge](change-the-settings-for-a-microsoft-dial-in-conferencing-bridge.md).
  
    
    
 **Set the PIN length for meetings**
  
    
    

1. Sign in to Office 365 with your work or school account.
    
  
2. Go to the **Office 365 admin center** > **Skype for Business**.
    
  
3. In the **Skype for Business admin center**, in the left navigation go to **dial-in conferencing** > **Microsoft bridge settings**.
    
  
4. Under **Security** > **PIN length** > enter the number of digits you want for the PIN and then click **Save**.
    
    The PIN can only be from 4 to 12 digits. The default is 5.
    
  
See  [Change the settings for a Microsoft dial-in conferencing bridge](change-the-settings-for-a-microsoft-dial-in-conferencing-bridge.md).
  
    
    
 **Enable or disable email from being sent to dial-in users**
  
    
    

1. Sign in to Office 365 with your work or school account.
    
  
2. Go to the **Office 365 admin center** > **Skype for Business** and in the left navigation click **Dial-in conferencing**.
    
  
3. On the **Microsoft bridge settings** page, check or uncheck the **Automatically send emails to users if any of the dial-in configuration changes**.
    
  
4. Click **Save**.
    
    You can also send email to the user with the dial-in conferencing settings, by going to the user's properties > **Dial-in conferencing** > **Send conference info via email**.
    
    If you do this, an email will be sent that only includes conference ID and conference phone number, but the PIN won't be included.
    
    See  [Send an email to a user with their dial-in conferencing information](send-an-email-to-a-user-with-their-dial-in-conferencing-information.md).
    
  

## See and set the primary and secondary languages on a dial-in conferencing bridge


1. Sign in to Office 365 with your work or school account.
    
  
2. Go to the **Office 365 admin center** > **Skype for Business**.
    
  
3. In the **Skype for Business admin center**, in the left navigation go to **Dial-in conferencing** and then click **Microsoft bridge**.
    
  
4. In the Action pane, select the phone number from the list, click **Set languages** and then on the **Set languages** page, click the drop-down under **Primary language** to view the complete list of supported languages.
    
    You can also set the primary and secondary languages that are supported when you select Microsoft as the dial-in conferencing provider. The order that you select in the drop-downs will be the order of the languages that will be presented to the callers.
    
  
See  [Set auto attendant languages for a dial-in conferencing](set-auto-attendant-languages-for-a-dial-in-conferencing.md).
  
    
    

## See dial-in conferencing dial-in numbers


1. Sign in to Office 365 with your work or school account.
    
  
2. Go to the **Office 365 admin center** > **Skype for Business**.
    
  
3. In the **Skype for Business admin center**, in the left navigation go to **Dial-in conferencing**> **Microsoft bridge**, and then under **Microsoft bridge**:
    
  - You can view the phone numbers that are set by Office 365 to be used for dial-in conferencing. 
    
  
  - You can also view the location, and the primary and secondary languages that will be used by the dial-in conferencing auto attendant.
    
  
  - You can select the dial-in conferencing default phone number that will be given to users when they are enabled for dial-in conferencing. However, if the default phone number of the dial-in conferencing bridge changes, the default phone number for existing users won't change.
    
  
You can go to **Dial-in conferencing** > **Dial-in users** and select the user's properties to change the default number for a user by choosing a new number from the list of numbers that are available in your organization.
  
    
    
See  [See a list of dial-in conferencing dial-in numbers](see-a-list-of-dial-in-conferencing-dial-in-numbers.md).
  
    
    

## See a list of users that are enabled


1. Sign in to Office 365 with your work or school account.
    
  
2. Go to the **Office 365 admin center** > **Skype for Business**.
    
  
3. In the **Skype for Business admin center**, in the left navigation go to **Dial-in conferencing**> and then **Dial-in users**.
    
  
See  [See a list of users that are enabled for dial-in conferencing](see-a-list-of-users-that-are-enabled-for-dial-in-conferencing.md).
  
    
    

## Want to know how to manage with Windows PowerShell?


- There are several settings that you can manage settings at the organization level using Windows PowerShell. This makes it easy to make these settings and have them apply to all of your users. Here are the organization level settings:
    
    To get more help on each cmdlet, see  [Skype for Business Online cmdlets](https://go.microsoft.com/fwlink/?LinkId=627324).
    

  
    
    
> 
  ```
  
Set-CsOnlineDialInConferencingTenantSettings -EnableEntryExitNotifications $true|$false
  ```


     The default is _$true_.
    
  

  
    
    
> 
  ```
  Set-CsOnlineDialInConferencingTenantSettings -EnableNameRecording $true|false
  ```


     The default is _$true_.
    
  

  
    
    
> 
  ```
  Set-CsOnlineDialInConferencingTenantSettings -PinLength 7
  ```


    The default is 5.
    
  

  
    
    
> 
  ```
  Set-CsOnlineDialInConferencingTenantSettings -AllowPSTNOnlyMeetingsByDefault $true|$false
  ```


    The default is  _$false_.
    
  

  
    
    
> 
  ```
  Set-CsOnlineDialInConferencingTenantSettings -AutomaticallySendEmailsToUsers $true|$false
  ```


     The default is _$true_.
    
  

  
    
    
> 
  ```
  Set-CsOnlineDialInConferencingTenantSettings -SendEmailFromOverride $true|$false
  ```


    The default is  _$false_.
    
  

  
    
    
> 
  ```
  Set-CsOnlineDialInConferencingTenantSettings -SendEmailFromAddress
  ```


     The default is _$null_.
    
  

  
    
    
> 
  ```
  Set-CsOnlineDialInConferencingTenantSettings -SendEmailFromDisplayName
  ```


    The default is  _$null_.
    
  
- Windows PowerShell is all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Office UNRESOLVED_TOKEN_VAL(365) using a single point of administration that can simplify your daily work when you have multiple tasks to do. To get started with Windows PowerShell, see these topics:
    
  -  [Six Reasons Why You Might Want to Use Windows PowerShell to Manage Office 365 ](https://go.microsoft.com/fwlink/?LinkId=525041)
    
  
  -  [Best ways to manage Office 365 with Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=525142)
    
  
- Windows PowerShell has many advantages in speed, simplicity, and productivity over only using the Office 365 admin center such as when you are making setting changes for many users at one time. Learn about these advantages in the following topics: 
    
  -  [An introduction to Windows PowerShell and Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525039)
    
  
  -  [Using Windows PowerShell to manage Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525453)
    
  
  -  [Using Windows PowerShell to do common Skype for Business Online management tasks](https://go.microsoft.com/fwlink/?LinkId=525038)
    
  

    The Windows PowerShell module for Skype for Business Online enables you to create a remote Windows PowerShell session that connects to Skype for Business Online. This module, which is supported only on 64-bit computers, can be downloaded from the Microsoft Download Center at  [Windows PowerShell Module for Skype for Business Online.](https://go.microsoft.com/fwlink/?LinkId=294688)
    
  

## See also


#### Other Resources


  
    
    
 [Set up dial-in or PSTN conferencing for Skype for Business](set-up-dial-in-or-pstn-conferencing-for-skype-for-business.md)
