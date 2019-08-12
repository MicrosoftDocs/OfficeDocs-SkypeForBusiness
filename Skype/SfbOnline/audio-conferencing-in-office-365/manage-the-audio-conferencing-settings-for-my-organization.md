---
title: "Manage the Audio Conferencing settings for my organization in Skype for Business Online"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: oscarr
ms.topic: article
ms.assetid: bc9bd328-c5b2-44e5-af15-e02bf00e1c81
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
search.appverid: MET150
ms.collection:
- Adm_Skype4B_Online
- Strat_SB_PSTN
audience: Admin
appliesto:
- Skype for Business
localization_priority: Normal
f1keywords: None
ms.custom:
- Audio Conferencing
description: "See Skype for Business Online steps to assign a dial-in conferencing license and conference ID to a user and many other dial-in conferencing settings. "
---

# Manage the Audio Conferencing settings for my organization in Skype for Business Online

> [!NOTE]
> If you want to manage these settings in Teams, see [Manage the Audio Conferencing settings for my organization in Microsoft Teams](/MicrosoftTeams/manage-the-audio-conferencing-settings-for-my-organization-in-teams).

It might be easier for you to see all of the audio conferencing settings for Skype for Business in one place.


## Assign an Audio Conferencing license

> [!NOTE]
> You can't assign licenses using the **Skype for Business admin center**. You must use the Microsoft 365 admin center. See [Assign Skype for Business licenses](../skype-for-business-and-microsoft-teams-add-on-licensing/assign-skype-for-business-and-microsoft-teams-licenses.md).

 **To assign a license for a user**

1. Sign in to Office 365 with your work or school account.

2. In the left navigation of the admin center, go to **Users** > **Active users**, and then select the user or users from the list of available users.

    > [!NOTE]
    > If you are assigning licenses to up to 20 users at the same time, you can use the **Select a view** drop-down then choose one of the options or create your own view. Then click **Edit**, **Next** twice then select the license and click **Submit**. You can also assign licenses to multiple users by using Windows Powershell. For instructions and sample PowerShell scripts, see [Assign Skype for Business licenses](../skype-for-business-and-microsoft-teams-add-on-licensing/assign-skype-for-business-and-microsoft-teams-licenses.md).

3. In the Action pane under **Product licenses**, click **Edit**.

4. On the **Product Licenses** page, turn on **Audio Conferencing** and then click **Save**. For more on licensing, see [Skype for Business add-on licensing](../skype-for-business-and-microsoft-teams-add-on-licensing/skype-for-business-and-microsoft-teams-add-on-licensing.md).

> [!NOTE]
> After you assign the license, Microsoft might not appear initially in the list as an audio conferencing provider. If this happens, either log out of the admin center or press CTRL+F5 to refresh the browser window.

## Enable or disable emails sent to audio conferencing users

![An icon showing the Skype for Business logo](../images/sfb-logo-30x30.png) **Using the Skype for Business admin center**

1. Sign in to Office 365 with your work or school account.

2. Go to the admin center > **Skype for Business** and in the left navigation, click **Audio conferencing**.

3. On the **Microsoft bridge settings** page, select or clear the **Automatically send emails to users if their audio conferencing settings change**.

4. Click **Save**.

    You can also send emails to the user with the audio conferencing settings by going to the user's audio conferencing properties and clicking **Send conference info via email**. The conference ID and default audio conferencing phone number is included on the meeting invite but not the PIN.

    See [Send an email to a user with their Audio Conferencing information](send-an-email-to-a-user-with-their-dial-in-information.md).

> [!NOTE]
> [!INCLUDE [updating-admin-interfaces](../includes/updating-admin-interfaces.md)]

**Using Windows PowerShell**

- You can also use the Windows PowerShell and run:

  ```
  Set-CsOnlineDialInConferencingTenantSettings -AutomaticallySendEmailsToUsers $true|$false
  ```

    You can use the [Set-CsOnlineDialInConferencingTenantSettings](https://docs.microsoft.com/powershell/module/skype/set-csonlinedialinconferencingtenantsettings?view=skype-ps) to manage other settings for your organization, including email.

## Change the sender's contact information in email messages sent to users

You can make changes to the email that is automatically sent to your users, including the actual email address and the display name of the sender's contact information. By default, the sender of the emails is Office 365, but you can change the email address and display name using Windows PowerShell and the [Set-CsOnlineDialInConferencingTenantSettings](https://docs.microsoft.com/powershell/module/skype/set-csonlinedialinconferencingtenantsettings?view=skype-ps) cmdlet. To make changes to the email address that is sending the email to the users, you must:

- Enter the email address in the _SendEmailFromAddress_ parameter.

- Enter the email display name in the  _SendEmailFromDisplayName_ parameter.

- Set the _SendEmailOverride_ parameter to _True_.

You can make changes to the email sent to users, such as the email address that the email is sent from or the display name for the email by running:

```
Set-CsOnlineDialInConferencingTenantSettings -SendEmailOverride $true -SendEmailFromAddress amos.marble@contoso.com -SendEmailFromDisplayName "Amos Marble"
```

If you want to change the email address information, you need to make sure that the inbound email policies of your organization allow emails that come from the custom email address.

You can use the [Set-CsOnlineDialInConferencingTenantSettings](https://docs.microsoft.com/powershell/module/skype/set-csonlinedialinconferencingtenantsettings?view=skype-ps) cmdlet to manage other settings for your organization, including email.

See [Emails that are automatically sent to users when their Audio Conferencing settings change](emails-sent-to-users-when-their-settings-change.md).

## Reset the meeting conference ID

1. Sign in to Office 365 with your work or school account.

2. Go to the admin center > **Skype for Business**.

3. In the **Skype for Business admin center**, in the left navigation, go to **Audio conferencing**, and in the Action pane under **Conference ID**, click **Reset**.

4. In the **Reset conference ID?** window, click **Yes**. A conference ID will be automatically created and an email sent to the user with the new conference ID if sending email to your users is enabled. It's enabled by default.

    > [!IMPORTANT]
    >  After a new conference ID is created, the old conference ID can't be used by callers. You should notify users to reschedule their existing meeting invites to make sure the new conference ID is added to the invitations. The users can use the Skype for Business Meeting Migration Tool to update their existing meetings. To see how to download, install, and run the Skype for Business Meeting Update Tool, see: [Meeting Update Tool for Skype for Business and Lync](https://support.office.com/article/2b525fe6-ed0f-4331-b533-c31546fcf4d4), [Skype for Business Online, Meeting Migration Tool (64-bit)](https://go.microsoft.com/fwlink/?LinkID=626047), and  [Skype for Business Online, Meeting Migration Tool (32-bit)](https://www.microsoft.com/en-us/download/details.aspx?id=54079).

See [Reset a conference ID for a user](reset-a-conference-id-for-a-user.md).

## Reset a conference organizer's PIN

Each meeting that a user schedules will get assigned a unique conference ID. Although a conference ID will be automatically created and assigned to a user, there may be times when a user doesn't want to use this one and you want to set it to a certain number, or your users can't remember or have lost their conference ID. You can use the Skype for Business admin center and Windows PowerShell to view, change, and reset their conference ID.


1. Sign in to Office 365 with your work or school account.

2. Go to the admin center > **Skype for Business** and in the left navigation, click **Audio conferencing**.

3. Click **Users**, and then select the user that you want to reset the PIN for.

4. In the Action pane, under **PIN**, click **Reset**.

Users will receive an email with their PIN when they're enabled for audio conferencing or when the PIN is reset. But if you have disabled automatically sending emails, a PIN reset email won't be sent and you will have to manually send the PIN to the user. The PIN will only be shown once after it has been reset. After it's displayed just after being reset, the PIN won't be shown anymore on the user properties; instead, ***** will be shown.

See [Reset the Audio Conferencing PIN](reset-the-audio-conferencing-pin.md).

## Send an email with Audio Conferencing information to a user

1. Sign in to Office 365 with your work or school account.

2. Go to the admin center > **Skype for Business** and in the left navigation, click **Audio conferencing**.

3. Click **Users**, and then select the user that you want to reset the PIN for.

4. In the Action pane, click **Send conference info via email**.

    > [!NOTE]
    > When you do this, the audio conferencing PIN isn't sent to the user.

See [Send an email to a user with their Audio Conferencing information](send-an-email-to-a-user-with-their-dial-in-information.md).

## Setting the phone numbers included on invites

1. Sign in to Office 365 with your work or school account.

2. Go to the admin center > **Skype for Business**.

3. In the left navigation, go to **Audio conferencing** > **Users**. Select the user that you want to enable for Audio Conferencing.

4. In the Action pane, you can set the **Toll number** and, if allowed, the **Toll-free number**.

5. Click **Save**.

See [Set the phone numbers included on invites](set-the-phone-numbers-included-on-invites.md).


## Choosing audio conferencing bridge settings

**Set the meeting experience when callers join a meeting**


1. Sign in to Office 365 with your work or school account.

2. Go to the admin center > **Skype for Business**.

3. In the **Skype for Business admin center**, in the left navigation, go to **Audio conferencing** > **Microsoft bridge settings**.

4. Under **Meeting join experience**, select the following actions:

   - **Enable meeting entry and exit notifications to be turned on** This is selected by default. If you clear this check box, users who have already joined the meeting by default won't be notified when someone enters or leaves the meeting.

     This can be set on a meeting-by-meeting basis when a user joins a meeting using a Skype for Business app and they modify the **Announce when people enter or leave** setting in the Skype Meeting **Options** menu of the meeting.

   - **Ask callers to record their name before joining the meeting** This is selected by default. If you clear this check box, callers won't be asked to record their name before they join a meeting.

5. After you make your changes, click **Save**.
    
See [Change the settings for an Audio Conferencing bridge](/MicrosoftTeams/change-the-settings-for-an-audio-conferencing-bridge).
  
 **Set the PIN length for meetings**

1. Sign in to Office 365 with your work or school account.

2. Go to the admin center > **Skype for Business**.

3. In the **Skype for Business admin center**, in the left navigation, go to **Audio conferencing** > **Microsoft bridge settings**.

4. Under **Security**, enter the number of digits you want for the PIN in the **PIN length** list, and then click **Save**.

    The PIN must be between 4 and 12 digits. The default is 5.
    
See [Change the settings for an Audio Conferencing bridge](/MicrosoftTeams/change-the-settings-for-an-audio-conferencing-bridge).
  
 **Enable or disable email from being sent to audio users**

1. Sign in to Office 365 with your work or school account.

2. Go to the admin center > **Skype for Business** and in the left navigation, click **Audio conferencing**.

3. On the **Microsoft bridge settings** page, select or clear the **Automatically send emails to users if their audio conferencing settings change**.

4. Click **Save**.

    You can also send email to the user with the audio conferencing settings, by going to the user's audio conferencing properties and clicking **Send conference info via email**.

    If you do this, an email will be sent that only includes conference ID and conference phone number, but the PIN won't be included.

    See [Send an email to a user with their Audio Conferencing information](send-an-email-to-a-user-with-their-dial-in-information.md).

## See and set the primary (default) and secondary (alternate) languages on an audio conferencing bridge


1. Sign in to Office 365 with your work or school account.

2. Go to the admin center > **Skype for Business**.

3. In the **Skype for Business admin center**, in the left navigation, go to **Audio conferencing**, and then click **Microsoft bridge**.

4. Select a phone number from the list, click **Set languages** in the Action pane, and then on the **Set languages** page, click the use the **Primary language** list to view the complete list of supported languages.

    You can also set the primary and secondary languages that are supported when you select Microsoft as the audio conferencing provider. The order that you select in the lists is the same order in which languages will be presented to callers.

See [Set auto attendant languages for Audio Conferencing](set-auto-attendant-languages-for-audio-conferencing.md).

## See audio conferencing dial-in numbers

1. Sign in to Office 365 with your work or school account.

2. Go to the admin center > **Skype for Business**.

3. In the **Skype for Business admin center**, in the left navigation, go to **Audio conferencing** > **Microsoft bridge**. Here you can:

   - View the phone numbers that are set by Office 365 to be used for Audio Conferencing.

   - View the location, and the primary and secondary languages, that will be used by the Audio Conferencing auto attendant.

   - Select the default phone number that will be given to users when they are enabled for Audio Conferencing. However, if the default phone number of the audio conferencing bridge changes, the default phone number for existing users won't change.

You can go to **Audio conferencing** > **Users** and select the user's properties to change the default number for a user by choosing a new number from the list of numbers that are available in your organization.

See [See a list of Audio Conferencing numbers](see-a-list-of-audio-conferencing-numbers.md).

## See a list of users that are enabled

1. Sign in to Office 365 with your work or school account.

2. Go to the admin center > **Skype for Business**.

3. In the **Skype for Business admin center**, in the left navigation, go to **Audio conferencing**> and then **Users**.

See [See a list of users that are enabled for Audio Conferencing](see-a-list-of-users-that-are-enabled-for-audio-conferencing.md).

## Want to know how to manage with Windows PowerShell?

There are several settings that you can manage at the organization level using Windows PowerShell. This makes it easy to apply settings to all of your users.

To get more help on each cmdlet, see [Skype for Business Online cmdlets](https://go.microsoft.com/fwlink/?LinkId=627324).

Here are the organization-level settings:

- **Setting entry/exit notifications** The default is _$true_.
  ```
  Set-CsOnlineDialInConferencingTenantSettings -EnableEntryExitNotifications $true|$false
  ```

- **Setting name recording** The default is _$true_.
  ```
  Set-CsOnlineDialInConferencingTenantSettings -EnableNameRecording $true|false
  ```

- **Setting the PIN length** The default is 5.
  ```
  Set-CsOnlineDialInConferencingTenantSettings -PinLength 7
  ```

- **Setting only dial-in meetings from a phone** The default _$false_.
  ```
  Set-CsOnlineDialInConferencingTenantSettings -AllowPSTNOnlyMeetingsByDefault $true|$false
  ```

- **Setting whether to send email to users** The default is _$true_.
  ```
  Set-CsOnlineDialInConferencingTenantSettings -AutomaticallySendEmailsToUsers $true|$false
  ```

- **Setting whether to send email from a different account** The default is  _$false_.
  ```
  Set-CsOnlineDialInConferencingTenantSettings -SendEmailFromOverride $true|$false
  ```

- **Setting the From address on email that is sent to users** The default is _$null_.
  ```
  Set-CsOnlineDialInConferencingTenantSettings -SendEmailFromAddress
  ```

- **Setting the display name for the email that is sent to users** The default is  _$null_.
  ```
  Set-CsOnlineDialInConferencingTenantSettings -SendEmailFromDisplayName
  ```

  ## Want to know more about Windows PowerShell
- Windows PowerShell is all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Office 365 using a single point of administration that can simplify your daily work when you have multiple tasks to do. To get started with Windows PowerShell, see these topics:

  - [Why you need to use Office 365 PowerShell](https://go.microsoft.com/fwlink/?LinkId=525041)

  - [Best ways to manage Office 365 with Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=525142)

- Windows PowerShell has many advantages in speed, simplicity, and productivity over only using the admin center, such as when you are making settings changes for many users at one time. Learn about these advantages in the following topics:

  - [An introduction to Windows PowerShell and Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525039)

  - [Using Windows PowerShell to manage Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525453)

  - [Using Windows PowerShell to do common Skype for Business Online management tasks](https://go.microsoft.com/fwlink/?LinkId=525038)

    The Windows PowerShell module for Skype for Business Online enables you to create a remote Windows PowerShell session that connects to Skype for Business Online. This module, which is supported only on 64-bit computers, can be downloaded from the Microsoft Download Center at [Windows PowerShell Module for Skype for Business Online.](https://go.microsoft.com/fwlink/?LinkId=294688)

## Related topics

[Manage the Audio Conferencing settings for a user](manage-the-audio-conferencing-settings-for-a-user.md)


