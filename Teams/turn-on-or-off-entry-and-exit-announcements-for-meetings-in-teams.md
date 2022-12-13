---
title: "Turn on or off entry and exit announcements for meetings in Teams"
ms.author: heidip
author: MicrosoftHeidi
manager: serdars
ms.reviewer: oscarr
ms.topic: article
ms.assetid: f2c7b5ea-07b6-4b77-8023-bec9596fcc32
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-collaboration
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom: 
  - Audio Conferencing
  - seo-marvel-apr2020
description: Admin can learn about how to turn entry and exit announcements on or off in a Microsoft Teams meeting.
---

# Turn on or off entry and exit announcements for meetings in Microsoft Teams

When you are setting up Audio Conferencing in Microsoft 365 or Office 365, you will get an audio conferencing bridge. A conferencing bridge can contain one or more phone numbers that people will use to call in to a Microsoft Teams meeting.
  
The conferencing bridge answers a call for a user who is dialing in to a meeting using a phone. The conferencing bridge answers the caller with voice prompts from a conferencing auto attendant, and then, depending on your settings, can play notifications, ask callers to record their name, and set up the PIN security. A PIN is given to a Microsoft Teams meeting organizer, and it allows them to start a meeting if they can't start the meeting using the Microsoft Teams app. You can, however, set it so that a PIN isn't required to start a meeting.

> [!NOTE]
> [!INCLUDE [updating-admin-interfaces](includes/updating-admin-interfaces.md)]
  
## Setting meeting join options using the Microsoft Teams admin center

You must be a Teams service admin to make these changes. See [Use Teams administrator roles to manage Teams](./using-admin-roles.md) to read about getting admin roles and permissions.

1. Log in to the admin center.

2. In the left navigation, go to **Meetings** > **Conference Bridges**.

3. At the top of the **Conference Bridges** page, click **Bridge Settings**.

4. In the **Bridge settings** pane, enable or disable **Meeting entry and exit notifications**. This is selected by default. If you clear it, users who have already joined the meeting won't be notified when someone enters or leaves the meeting.

5. Under **Entry/exit announcement type**, select **Names or phone numbers** or **Tones**.

   > [!NOTE]
   > By default, external participants can't see the phone numbers of dialed-in participants. If you want to maintain the privacy of these phone numbers, select **Tones** for **Entry/exit announcement type** (this prevents the numbers from being read out by Teams).

6. If you chose **Names or phone numbers**, enable or disable **Ask callers to record their name before joining the meeting**.

7. Click **Save**.

## Want to know more about Windows PowerShell

Windows PowerShell is all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Microsoft 365 or Office 365 using a single point of administration that can simplify your daily work when you have multiple tasks to do. To get started with Windows PowerShell, see these topics:

- [Why you need to use Microsoft 365 or Office 365 PowerShell](/microsoft-365/enterprise/why-you-need-to-use-microsoft-365-powershell)

- [Best ways to manage Microsoft 365 or Office 365 with Windows PowerShell](/previous-versions//dn568025(v=technet.10))

For more information about Windows PowerShell, see the [Microsoft Teams PowerShell reference](/powershell/module/teams/?view=teams-ps) for more information.
  
## Related topics

[Audio Conferencing common questions](audio-conferencing-common-questions.md)
