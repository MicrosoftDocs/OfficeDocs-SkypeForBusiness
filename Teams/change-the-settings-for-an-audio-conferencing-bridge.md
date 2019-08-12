---
title: "Change the settings for an Audio Conferencing bridge"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: oscarr
ms.topic: article
ms.assetid: 783fad3f-b77c-422b-b91f-7c8b0af324fb
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection:  
- Teams_ITAdmin_Help
- M365-collaboration
- M365-voice
audience: Admin
appliesto:
- Skype for Business 
- Microsoft Teams
localization_priority: Normal
f1keywords: ms.teamsadmincenter.audioconferencing.bridgesettings
ms.custom:
- Audio Conferencing
description: "Get the steps you need to change settings for a conferencing bridge that's used to prompt callers and gather names and pins for meeting organizers when they're not using Skype for Business or Microsoft Teams apps. "
---

# Change the settings for an Audio Conferencing bridge

When you are setting up Audio Conferencing in Office 365, you will receive phone numbers for your users from what is called an audio conferencing bridge. A conferencing bridge can contain one or more phone numbers. These phone numbers are used when callers dial in to a meeting. The phone number is included at the bottom of the Skype for Business or Microsoft Teams meeting invite.
  
The conferencing bridge answers a call and prompts the caller with voice prompts using a meeting auto attendant, and then, depending on your settings, it can play notifications, ask callers to record their name, and control the PIN settings. PINs are given to meeting organizers to allow them to start a meeting when they are aren't using a Skype for Business or Microsoft Teams app.

  > [!IMPORTANT]
  > A PIN is only required for the meeting organizer when a Skype for Business or Microsoft Teams app user hasn't already started the meeting. If everyone is dialing in to the meeting, the PIN is required for the meeting organizer to start the meeting. 

> [!NOTE]
> [!INCLUDE [updating-admin-interfaces](includes/updating-admin-interfaces.md)]

## ![An icon showing the Microsoft Teams logo](media/teams-logo-30x30.png) Using the Microsoft Teams admin center

1. In the left navigation, go to **Meetings** > **Conference bridges**. 

2. At the top of the **Conference bridges** page, click **Bridge settings**. 

3. In the **Bridge settings** pane, select: 
   - **Meeting entry and exit notifications** If you turn this off, users who have already joined the meeting won't be notified when someone enters or leaves the meeting.
    
     When you turn on **Meeting entry and exit notifications**, you can select these options:
    
   - **Names or phone numbers** When users dial in to a meeting, their phone number will be played when they join it.
    
   - **Tones** When users dial in to a meeting, an audio tone will be played when they join it.
      
   - **Ask callers to record their name before joining the meeting** If you turn this off, callers won't be asked to record their name before they join a meeting.

4. To set the PIN length for meetings, select the number of digits you want for the PIN in the **PIN length** list.

5. To specify whether to send email to your users, enable or disable **Automatically send emails to users if their audio conferencing configuration changes**.
    See [Emails automatically sent to users when their Audio Conferencing settings change in Microsoft Teams](emails-sent-to-users-when-their-settings-change-in-teams.md) or [Emails sent to users when their settings change in Skype for Business Online](/SkypeForBusiness/audio-conferencing-in-office-365/emails-sent-to-users-when-their-settings-change) for more information.
 
6. Click **Save**. 


## ![An icon showing the Skype for Business logo](media/sfb-logo-30x30.png)  Using the Skype for Business admin center

 **Set up the meeting experience when callers join a meeting**
    
1. In the **Skype for Business admin center**, in the left navigation go to **Audio conferencing** > **Microsoft bridge settings**.
    
2. On the **Microsoft bridge settings** page, under **Meeting join experience**, select:
    
   - **Enable meeting entry and exit notifications to be turned on** This is selected by default. If you clear the check box, users who have already joined the meeting won't be notified when someone enters or leaves the meeting.
    
   - When you select **Enable meeting entry and exit notifications to be turned on**, you can select these options from the **Entry/exit announcement type** list:
    
   - **Names or phone numbers** When users dial in to a meeting, their phone number will be played when they join it.
    
   - **Tones** When users dial in to a meeting, an audio tone will be played when they join it.
  
   - **Ask callers to record their name before joining the meeting** This is selected by default. If you clear the check box, callers won't be asked to record their name before they join a meeting.
    
3. After you make your changes, click **Save**.
    
**Set the PIN length for meetings**
  
1. Sign in to Office 365 with your work or school account.
    
2. Go to the **Microsoft 365 admin center** > **Skype for Business**.
    
3. In the **Skype for Business admin center**, in the left navigation, go to **Audio conferencing** > **Microsoft bridge settings**.
    
4. On the **Microsoft bridge settings** page, under **Security**, enter the number of digits you want for the PIN in the **PIN length** list, and then click **Save**.
    
    > [!IMPORTANT]
    > The PIN must be between 4 and 12 digits. 
  
**Select whether to send email to your users**
  
1. Sign in to Office 365 with your work or school account.
    
2. Go to the **Microsoft 365 admin center** > **Skype for Business**.
    
3. In the **Skype for Business admin center**, in the left navigation, go to **Audio conferencing** > **Microsoft bridge settings**.
    
4. On the **Microsoft bridge settings** page, select or clear **Automatically send emails to users if their dial-in information changes**, and then click **Save**.
    
    See [Emails automatically sent to users when their Audio Conferencing settings change in Microsoft Teams](emails-sent-to-users-when-their-settings-change-in-teams.md) or [Emails sent to users when their settings change in Skype for Business Online](/SkypeForBusiness/audio-conferencing-in-office-365/emails-sent-to-users-when-their-settings-change) for more information.
    
## Want to know how to manage with Windows PowerShell?

- To save time or automate this process, you can use the [Set-CsDialinConferencingBridge](https://go.microsoft.com/fwlink/?LinkId=617686) cmdlet.
    
- Windows PowerShell is all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Office 365 using a single point of administration that can simplify your daily work when you have multiple tasks to do. To get started with Windows PowerShell, see these topics:
    
  - [Why you need to use Office 365 PowerShell](https://go.microsoft.com/fwlink/?LinkId=525041)
    
  - [Best ways to manage Office 365 with Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=525142)
    
- Windows PowerShell has many advantages in speed, simplicity, and productivity over only using the Microsoft 365 admin center, such as when you are making setting changes for many users at one time. Learn about these advantages in the following topics: 
    
  - [An introduction to Windows PowerShell and Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525039)
    
  - [Using Windows PowerShell to manage Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525453)
    
  - [Using Windows PowerShell to do common Skype for Business Online management tasks](https://go.microsoft.com/fwlink/?LinkId=525038)
    
    > [!NOTE]
    > The Windows PowerShell module for Skype for Business Online enables you to create a remote Windows PowerShell session that connects to Skype for Business Online. This module, which is supported only on 64-bit computers, can be downloaded from the Microsoft Download Center at [Windows PowerShell Module for Skype for Business Online.](https://go.microsoft.com/fwlink/?LinkId=294688)
  
## Related topics

[Set up Audio Conferencing for Microsoft Teams](set-up-audio-conferencing-in-teams.md)

[Set up Audio Conferencing for Skype for Business Online](/skypeforbusiness/audio-conferencing-in-office-365/set-up-audio-conferencing)
