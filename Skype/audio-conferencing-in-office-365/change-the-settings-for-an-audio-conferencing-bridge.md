---
title: "Change the settings for an Audio Conferencing bridge"
ms.author: tonysmit
author: tonysmit
manager: scotv
ms.date: 11/10/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Adm_Skype4B_Online
ms.custom:
- Adm_O365_FullSet
- Strat_SB_PSTN
ms.assetid: 783fad3f-b77c-422b-b91f-7c8b0af324fb
description: "Get the steps you need to change settings for a Microsoft dial-in conferencing bridge that's used to prompt callers and gather names and pins for meeting organizers when they're not using Skype for Business clients. "
---

# Change the settings for an Audio Conferencing bridge

When you are setting up Audio Conferencing in Office 365, you will receive phone numbers for your users from what is called an audio conferencing bridge. A conferencing bridge can contain one or more phone numbers. These phone numbers are used when callers dial in to a meeting. The phone number is included at the bottom of the Skype for Business or Microsoft Teams meeting invite.
  
The conferencing bridge answers a call and prompts the caller with voice prompts using a meeting auto attendant, and then, depending on your settings, it can play notifications, ask callers to record their name, and control the PIN settings. PINs are given to meeting organizers to allow them to start a meeting when they are aren't using a Skype for Business or Microsoft Teams app.
  
> [!IMPORTANT]
> A PIN is only required for the meeting organizer when a Skype for Business or Microsoft Teams app user hasn't already started the meeting. If everyone is dialing in to the meeting, the PIN is required for the meeting organizer to start the meeting. 
  
## Change the settings for an audio conferencing bridge

 **Set up the meeting experience when callers join a meeting**
  
1. Sign in to Office 365 with your work or school account.
    
2. Go to the **Office 365 admin center** > **Skype for Business**.
    
3. In the **Skype for Business admin center**, in the left navigation go to **Audio conferencing** > **Microsoft bridge settings**.
    
4. On the **Microsoft bridge settings** page, under **Meeting join experience**, select:
    
  - **Enable meeting entry and exit notifications to be turned on** This is selected by default. If you clear the check box, users who have already joined the meeting won't be notified when someone enters or leaves the meeting.
    
    When you select **Enable meeting entry and exit notifications to be turned on**, you can select these options from the **Entry/exit announcement type** list:
    
  - **Names or phone numbers** When users dial in to a meeting, their phone number will be played when they join it.
    
  - **Tones** When users dial in to a meeting, an audio tone will be played when they join it.
    
    > [!NOTE]
    > Using **Tone** as the announcement type is currently available to all customers as a preview feature.
  
  - **Ask callers to record their name before joining the meeting** This is selected by default. If you clear the check box, callers won't be asked to record their name before they join a meeting.
    
5. After you make your changes, click **Save**.
    
**Set the PIN length for meetings**
  
1. Sign in to Office 365 with your work or school account.
    
2. Go to the **Office 365 admin center** > **Skype for Business**.
    
3. In the **Skype for Business admin center**, in the left navigation, go to **Audio conferencing** > **Microsoft bridge settings**.
    
4. On the **Microsoft bridge settings** page, under **Security**, enter the number of digits you want for the PIN in the **PIN length** list, and then click **Save**.
    
    > [!IMPORTANT]
    > The PIN must be between 4 and 12 digits. 
  
**Select whether to send email to your users**
  
1. Sign in to Office 365 with your work or school account.
    
2. Go to the **Office 365 admin center** > **Skype for Business**.
    
3. In the **Skype for Business admin center**, in the left navigation, go to **Audio conferencing** > **Microsoft bridge settings**.
    
4. On the **Microsoft bridge settings** page, select or clear **Automatically send emails to users if their audio conferencing configuration changes**, and then click **Save**.
    
    See [Emails that are automatically sent to users when their Audio Conferencing settings change](emails-that-are-automatically-sent-to-users-when-their-audio-conferencing-settin.md) for more information.
    
## Want to know how to manage with Windows PowerShell?

- To save time or automate this process, you can use the [Set-CsDialinConferencingBridge](https://go.microsoft.com/fwlink/?LinkId=617686 ) cmdlet.
    
- Windows PowerShell is all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Office 365 using a single point of administration that can simplify your daily work when you have multiple tasks to do. To get started with Windows PowerShell, see these topics:
    
  - [Why you need to use Office 365 PowerShell](https://go.microsoft.com/fwlink/?LinkId=525041)
    
  - [Best ways to manage Office 365 with Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=525142)
    
- Windows PowerShell has many advantages in speed, simplicity, and productivity over only using the Office 365 admin center, such as when you are making setting changes for many users at one time. Learn about these advantages in the following topics: 
    
  - [An introduction to Windows PowerShell and Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525039)
    
  - [Using Windows PowerShell to manage Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525453)
    
  - [Using Windows PowerShell to do common Skype for Business Online management tasks](https://go.microsoft.com/fwlink/?LinkId=525038)
    
    > [!NOTE]
    > The Windows PowerShell module for Skype for Business Online enables you to create a remote Windows PowerShell session that connects to Skype for Business Online. This module, which is supported only on 64-bit computers, can be downloaded from the Microsoft Download Center at [Windows PowerShell Module for Skype for Business Online.](https://go.microsoft.com/fwlink/?LinkId=294688)
  
## See also

#### Other Resources

[Dial-in conferencing in Office 365](../misctopics/dial-in-conferencing-in-office-365.md)

