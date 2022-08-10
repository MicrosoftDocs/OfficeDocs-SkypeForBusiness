---
title: Manage Audio Conferencing settings
ms.author: heidip
author: MicrosoftHeidi
manager: serdars
ms.reviewer: oscarr
ms.topic: article
ms.assetid: bc9bd328-c5b2-44e5-af15-e02bf00e1c81
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - M365-collaboration
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords: 
  - CSH
ms.custom: 
  - Audio Conferencing
  - seo-marvel-mar2020
description: See Microsoft Teams steps to assign a dial-in conferencing license and conference ID to a user and many other dial-in conferencing settings.
---

# Manage the Audio Conferencing settings for your organization in Microsoft Teams

It might be easier for you to see all of the audio conferencing settings for Microsoft Teams in one place.

> [!NOTE]
> [!INCLUDE [updating-admin-interfaces](includes/updating-admin-interfaces.md)]

## Assign an Audio Conferencing license

> [!NOTE]
> You can't assign licenses using Teams. You must use the Microsoft 365 admin center. See [Assign Microsoft Teams add-on licenses](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md).

### To assign a license for a user

1. Sign in to Microsoft 365 with your work or school account.

2. In the left navigation of the **Microsoft 365 admin center**, go to **Users** > **Active users**, and then select the user or users from the list of available users.

    > [!NOTE]
    > If you are assigning licenses to up to 20 users at the same time, you can use the **Select a view** drop-down then choose one of the options or create your own view. Then click **Edit**, **Next** twice then select the license and click **Submit**.  
  
3. In the Action pane under **Product licenses**, click **Edit**.

4. On the **Product Licenses** page, turn on **Audio Conferencing** and then click **Save**. For more on licensing, see [Microsoft Teams add-on licensing](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md).

   > [!NOTE]
   > After you assign the license, Microsoft might not appear initially in the list as an audio conferencing provider. If this happens, either log out of the admin center or press CTRL+F5 to refresh the browser window.
  
## Enable or disable emails sent to audio conferencing users

### Enable or disable using the Microsoft Teams admin center

1. In the left navigation, go to **Meetings** > **Conference Bridges**.

2. At the top of the **Conference Bridges** page, click **Bridge settings**.

3. In the **Bridge settings** pane, enable or disable **Automatically send emails to users if their dial-in settings change**.

4. Click **Save**.

### Enable or disable using Windows PowerShell

See the [Microsoft Teams PowerShell reference](/powershell/module/teams/?view=teams-ps) for more information.
  
## Reset the meeting conference ID

### Reset the meeting conference ID using the Microsoft Teams admin center

1. In the left navigation, click **Users**, and then select the user from the list of available users.

2. Under **Audio Conferencing**, click **Reset conference ID**.  

3. In the **Reset conference ID?** window, click **Reset**. A conference ID will be automatically created and an email sent to the user with the new conference ID if sending email to your users is enabled. It's enabled by default.

See [Reset a conference ID for a user](reset-a-conference-id-for-a-user-in-teams.md).

## Reset a conference organizer's PIN

Each meeting that a user schedules will get assigned a unique conference ID. Although a conference ID will be automatically created and assigned to a user, there may be times when a user doesn't want to use this one and you want to set it to a certain number, or your users can't remember or have lost their conference ID.

### Reset a conference organizer's PIN using the Microsoft Teams admin center

1. In the left navigation, click **Users**, and then select the user from the list of available users.

2. Under **Audio Conferencing**, click **Reset PIN**, and then click **Reset**.
  
Users will receive an email with their PIN when they're enabled for audio conferencing or when the PIN is reset. But if you have disabled automatically sending emails, a PIN reset email won't be sent and you will have to manually send the PIN to the user. The PIN will only be shown once after it has been reset. After it's displayed just after being reset, the PIN won't be shown anymore on the user properties; instead, ***** will be shown.
  
See [Reset the Audio Conferencing PIN](reset-the-audio-conferencing-pin-in-teams.md).
  
## Send an email with Audio Conferencing information to a user

### Send an email using the Microsoft Teams admin center

1. In the left navigation, click **Users**, and then select the user from the list of available users.

2. Under **Audio Conferencing**, click **Send conference info in email**.

    > [!NOTE]
    > When you do this, the audio conferencing PIN isn't sent to the user.

See [Send an email to a user with their Audio Conferencing information](send-an-email-to-a-user-with-their-dial-in-information-in-teams.md).
  
## Set the phone numbers included on invites

### Set invite phone numbers using the Microsoft Teams admin center

Refer to [Set the phone numbers included on invites in Microsoft Teams](set-the-phone-numbers-included-on-invites-in-teams.md).

> [!NOTE]
> You can also set phone numbers by adding them to the *TeamsAudioconferencingpolicy* and assigning the policy to your users. Toll and toll-free phone numbers added to the policy take precedence over the phone numbers set individually for users via the audio conferencing settings pane. If no phone numbers are added to the *Teamsaudioconferencingpolicy*, then the phone number set individually for users via the audio conferencing settings pane will be displayed in Microsoft Teams meeting requests. [Audio Conferencing policy settings for toll and toll-free numbers](audio-conferencing-toll-free-numbers-policy.md) has more information.

## Choose audio conferencing bridge settings

### Set the meeting experience when callers join a meeting using the Microsoft Teams admin center

1. In the left navigation, go to **Meetings** > **Conference Bridges**.

2. At the top of the **Conference Bridges** page, click **Bridge settings**.

3. In the **Bridge settings** pane, enable or disable **Meeting entry and exit notifications**.

    This is enabled by default. If you disable this option, users who have already joined the meeting by default won't be notified when someone enters or leaves the meeting.

4. Under **Entry/exit announcement type**, choose either **Tones** or **Names or phone numbers**.

    If you choose **Names or phone numbers**, you can also choose to enable or disable **Ask callers to record their name before joining the meeting**.
    > [!NOTE]
    > By default, external participants can't see the phone numbers of dialed-in participants. If you want to maintain the privacy of these phone numbers, select **Tones** for **Entry/exit announcement type** (this prevents the numbers from being read out by Teams).
5. Click **Save**.

See [Change the settings for an Audio Conferencing bridge](change-the-settings-for-an-audio-conferencing-bridge.md).
  
### Set the PIN length for meetings

1. In the left navigation, go to **Meetings** > **Conference Bridges**.

2. At the top of the **Conference Bridges** page, click **Bridge settings**.

3. In the **Bridge settings** pane, enter the number of digits you want for the PIN in the **PIN length** list, and then click **Save**.

    The PIN must be between 4 and 12 digits. The default is 5.

See [Change the settings for an Audio Conferencing bridge](change-the-settings-for-an-audio-conferencing-bridge.md).

### Enable or disable email from being sent to audio users

1. In the left navigation, go to **Meetings** > **Conference Bridges**.

2. At the top of the **Conference Bridges** page, click **Bridge settings**.

3. In the **Bridge settings** pane, enable or disable **Automatically send emails to users if their audio conferencing settings change**.

4. Click **Save**.

    You can also send email to the user with the audio conferencing settings, by going to the user's audio conferencing properties and clicking **Send conference info in email**.

    If you do this, an email will be sent that only includes conference ID and conference phone number, but the PIN won't be included.

See [Send an email to a user with their Audio Conferencing information](send-an-email-to-a-user-with-their-dial-in-information-in-teams.md).

## See and set the primary (default) and secondary (alternate) languages on an audio conferencing bridge

### See primary and secondary languages using the Microsoft Teams admin center

1. In the left navigation, go to **Meetings** > **Conference Bridges**.

2. Select a phone number from the list and click **Edit**.

3. Choose the languages you want under **Default language** and **Alternate languages (optional)**.

4. Click **Save**.

See [Set auto attendant languages for Audio Conferencing](set-auto-attendant-languages-for-audio-conferencing-in-teams.md).
  
## See audio conferencing dial-in numbers using the Microsoft Teams admin center

1. In the left navigation, go to **Meetings** > **Conference Bridges**.

2. Select a phone number from the list and click **Edit**. Here you can:

   - View the phone numbers that are to be used for Audio Conferencing.

   - View the location, and the primary language, that will be used by the Audio Conferencing auto attendant.

See [See a list of Audio Conferencing numbers](see-a-list-of-audio-conferencing-numbers-in-teams.md).

## Want to know more about Windows PowerShell?

Windows PowerShell is all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Microsoft 365 or Office 365 using a single point of administration that can simplify your daily work when you have multiple tasks to do. To get started with Windows PowerShell, see these topics:

- [Why you need to use Microsoft 365 or Office 365 PowerShell](/microsoft-365/enterprise/why-you-need-to-use-microsoft-365-powershell)

- [Best ways to manage Microsoft 365 or Office 365 with Windows PowerShell](/previous-versions//dn568025(v=technet.10))

For more information about Windows PowerShell, see the [Microsoft Teams PowerShell reference](/powershell/module/teams/?view=teams-ps) for more information.

## Related topics

[Manage the Audio Conferencing settings for a user](manage-the-audio-conferencing-settings-for-a-user-in-teams.md)
