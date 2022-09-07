---
title: "Change the settings for an Audio Conferencing bridge"
ms.author: heidip
author: MicrosoftHeidi
manager: serdars
ms.reviewer: oscarr
ms.topic: article
ms.assetid: 783fad3f-b77c-422b-b91f-7c8b0af324fb
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
  - ms.teamsadmincenter.audioconferencing.bridgesettings
  - seo-marvel-mar2020
description: Change audio conferencing bridge settings, including entry and exit notifications, play names or phone numbers, tones, and prompt callers to record their name.
---

# Change the settings for an Audio Conferencing bridge

When you are setting up Audio Conferencing in Microsoft 365 or Office 365, you will receive phone numbers for your users from what is called an audio conferencing bridge. A conferencing bridge can contain one or more phone numbers. These phone numbers are used when callers dial in to a meeting. The phone number is included at the bottom of the Teams meeting invite.
  
The conferencing bridge answers a call and prompts the caller with voice prompts using a meeting auto attendant, and then, depending on your settings, it can play notifications, ask callers to record their name, and control the PIN settings. PINs are given to meeting organizers to allow them to start a meeting when they are aren't using a Microsoft Teams app.

  > [!IMPORTANT]
  > A PIN is only required for the meeting organizer when a Teams app user hasn't already started the meeting. If everyone is dialing in to the meeting, the PIN is required for the meeting organizer to start the meeting.

> [!NOTE]
> [!INCLUDE [updating-admin-interfaces](includes/updating-admin-interfaces.md)]

## Using the Microsoft Teams admin center

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
    See [Emails automatically sent to users when their Audio Conferencing settings change in Microsoft Teams](emails-sent-to-users-when-their-settings-change-in-teams.md) for more information.

6. Click **Save**.

## Want to know how to manage with Windows PowerShell?

- To save time or automate this process, you can use the [Set-CsDialinConferencingBridge](/powershell/module/skype/Set-CsOnlineDialInConferencingBridge) cmdlet.

- Windows PowerShell is all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Microsoft 365 or Office 365 using a single point of administration that can simplify your daily work when you have multiple tasks to do. To get started with Windows PowerShell, see these topics:

  - [Why you need to use Office 365 PowerShell](/microsoft-365/enterprise/why-you-need-to-use-microsoft-365-powershell)

  - [Best ways to manage Microsoft 365 or Office 365 with Windows PowerShell](/previous-versions//dn568025(v=technet.10))

- Windows PowerShell has many advantages in speed, simplicity, and productivity over only using the Microsoft 365 admin center, such as when you are making setting changes for many users at one time. Learn about these advantages in the following topics:

  - [An introduction to Windows PowerShell and Skype for Business Online](/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell)

  - [Using Windows PowerShell to manage Skype for Business Online](/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell)

  - [Using Windows PowerShell to do common Skype for Business Online management tasks](/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell)

    > [!NOTE]
    > The Windows PowerShell module for Skype for Business Online enables you to create a remote Windows PowerShell session that connects to Skype for Business Online. This module, which is supported only on 64-bit computers, can be downloaded from the Microsoft Download Center at [Windows PowerShell Module for Skype for Business Online.](/skypeforbusiness/set-up-your-computer-for-windows-powershell/download-and-install-windows-powershell-5-1)
  
## Related topics

[Set up Audio Conferencing for Microsoft Teams](set-up-audio-conferencing-in-teams.md)

[Set up Audio Conferencing for Skype for Business Online](/skypeforbusiness/audio-conferencing-in-office-365/set-up-audio-conferencing)
