---
title: Start Audio Conference over the phone without a PIN in Teams
ms.author: jenz
author: jenzamora
manager: pamgreen
ms.reviewer: oscarr
ms.date: 02/22/2024
ms.topic: article
ms.assetid: d5b1f775-d7ed-4d30-853a-1d49f81e8fde
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.subservice: teams-audio-conferencing
search.appverid: MET150
ms.collection: 
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
  - seo-marvel-mar2020
description: "Learn how to enable or disable anonymous callers from joining a meeting from the Teams admin center. "
---

# Start an Audio Conference over the phone without a PIN in Microsoft Teams

Users dialing into a meeting might feel frustrated as they wait in the lobby, listening to music, because the Microsoft Teams meeting organizer hasn't started the meeting.
  
If a meeting organizer calls in to the meeting, by default, a PIN is required to start a meeting. You can set it up so that anyone can dial in to a meeting and not be prompted for a PIN to start the meeting. You can use the admin center to enable or disable this setting for a single user.
  
A PIN isn't required for the meeting organizer if someone starts the meeting from the Microsoft Teams app. A PIN is only required when a meeting organizer joins their meeting over a phone. The PIN for meetings is sent to the audio user when they're assigned the **Audio Conferencing** license and are enabled for Audio Conferencing. See [Send an email to a user with their Audio Conferencing information](send-an-email-to-a-user-with-their-dial-in-information-in-teams.md) and [Emails that are automatically sent to users when their Audio Conferencing settings change](emails-sent-to-users-when-their-settings-change-in-teams.md).

> [!NOTE]
> [!INCLUDE [updating-admin-interfaces](includes/updating-admin-interfaces.md)]
  
## Enable or disable anonymous callers from joining a meeting

### Using the Microsoft Teams admin center

1. In the left navigation, select **Users**.

2. Select a user in the list, and then select **Edit** at the top of the page.

3. Next to **Audio Conferencing**, select **Edit**.

4. In the **Audio Conferencing** pane, enable or disable **Dial-in callers can be the first person in a meeting**.

5. Select **Apply**.

### Using Windows PowerShell

For more information, see [Microsoft Teams PowerShell reference](/powershell/module/teams).

## What else should you know?

- If you want to reset the PIN, see [Reset the Audio Conferencing PIN](reset-the-audio-conferencing-pin-in-teams.md).

- If anonymous access, or the option to start a meeting without requiring a PIN, is disabled:

  - **If the meeting hasn't started (there's no one in the meeting yet):** A caller is prompted if they're the organizer; if they say yes, they're prompted for their PIN. After they enter the PIN, the meeting starts and the user joins the meeting.

  - **If the meeting already started (someone else is already in the meeting):** A caller isn't be prompted if they're the organizer and they're never prompted for the PIN. The meeting is already started, and the caller joins it.

- If anonymous access, or not requiring a PIN to start a meeting, is enabled:

  - **If the meeting hasn't started (there's no one in the meeting yet):** A caller isn't be prompted if they're the organizer, and they're never prompted for the PIN. Because the organizer's setting is off, the meeting starts and the anonymous callers join the meeting.

  - **If the meeting already started (someone else is already in the meeting):** A caller isn't be prompted if they're the organizer, and they're never prompted for the PIN. The meeting is already started, and the caller joins it.

## Want to know more about Windows PowerShell?

Windows PowerShell is all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Microsoft 365 or Office 365 by using a single point of administration that can simplify your daily work when you have multiple tasks to do. To get started with Windows PowerShell, see these articles:

- [Why you need to use Office 365 PowerShell](/microsoft-365/enterprise/why-you-need-to-use-microsoft-365-powershell)

- [Best ways to manage Microsoft 365 or Office 365 with Windows PowerShell](/previous-versions//dn568025(v=technet.10))

For more information about Windows PowerShell, see the [Microsoft Teams PowerShell reference](/powershell/module/teams).
  
## Related articles

- [Try or purchase Audio Conferencing in Microsoft 365 for Microsoft Teams](try-or-purchase-audio-conferencing-in-office-365-for-teams.md)
