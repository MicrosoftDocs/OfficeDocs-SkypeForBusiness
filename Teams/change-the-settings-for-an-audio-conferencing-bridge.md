---
title: "Change the settings for an Audio Conferencing bridge"
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.reviewer: oscarr
ms.date: 12/7/2023
ms.topic: article
ms.assetid: 783fad3f-b77c-422b-b91f-7c8b0af324fb
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - m365initiative-meetings
  - M365-collaboration
  - m365initiative-meetings
  - Tier1
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

When you set up Audio Conferencing in Microsoft 365 or Office 365, you get phone numbers for your users from an audio conferencing bridge. A conferencing bridge can have one or more phone numbers that are included at the bottom of the meeting invite. These phone numbers allow users to join Microsoft Teams meetings by dialing in.

When a user dials in to a meeting using a phone, the conferencing bridge answers with voice prompts from the meeting auto attendant. Depending on your settings, the conferencing bridge can also play notifications, ask callers to record their name, and control the PIN settings. A PIN is assigned to meeting organizers to allow them to start their meetings if they can't use the Microsoft Teams app.

  > [!IMPORTANT]
  > A PIN is only required for the meeting organizer when a Teams app user hasn't already started the meeting. If everyone is dialing in to the meeting, the PIN is required for the meeting organizer to start the meeting.

> [!NOTE]
> [!INCLUDE [updating-admin-interfaces](includes/updating-admin-interfaces.md)]

## Using the Microsoft Teams admin center

1. Go to **Meetings** > **Conference bridges**.

2. At the top of the **Conference bridges** page, select **Bridge settings**.

3. In the **Bridge settings** pane, select:
   - **Meeting entry and exit notifications**- If you turn this setting off, users in the meeting aren't notified when someone enters or leaves the meeting.

     When you turn on **Meeting entry and exit notifications**, you can select one of these options:

     - **Names or phone numbers**- When users join a meeting by dialing in, their phone number is played.

     - **Tones**- When users join a meeting by dialing in, an audio tone is played.

4. To set the PIN length for meetings, select the number of digits you want for the PIN in the **PIN length** list.

5. To control whether to send email to your users, toggle **Automatically send emails to users if their audio conferencing configuration changes** **On** or **Off**.
    For more information, see [Emails automatically sent to users when their Audio Conferencing settings change in Microsoft Teams](emails-sent-to-users-when-their-settings-change-in-teams.md).

6. Select **Save**.

## Want to know how to manage with Windows PowerShell?

- To save time or automate this process, you can use the [Set-CsOnlineDialInConferencingBridge](/powershell/module/skype/Set-CsOnlineDialInConferencingBridge) cmdlet.

- Windows PowerShell is all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Microsoft 365 or Office 365 using a single point of administration that can simplify your daily work when you have multiple tasks to do. To get started with Windows PowerShell, see these articles:

  - [Why you need to use Office 365 PowerShell](/microsoft-365/enterprise/why-you-need-to-use-microsoft-365-powershell)

  - [Best ways to manage Microsoft 365 or Office 365 with Windows PowerShell](/previous-versions//dn568025(v=technet.10))

- Windows PowerShell has many advantages in speed, simplicity, and productivity over only using the Microsoft 365 admin center, such as when you're making setting changes for many users at one time. Learn about these advantages in the following articles:

  - [Microsoft Teams PowerShell Overview](teams-powershell-overview.md)

  - [Install Microsoft Teams PowerShell Module](teams-powershell-install.md)
  
## Related articles

[Set up Audio Conferencing for Microsoft Teams](set-up-audio-conferencing-in-teams.md)
