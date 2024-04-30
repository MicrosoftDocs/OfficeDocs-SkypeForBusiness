---
title: "Turn on or off entry and exit announcements for meetings in Teams"
ms.author: jenz
author: jenzamora
manager: pamgreen
ms.reviewer: oscarr
ms.date: 12/14/2023
ms.topic: article
ms.assetid: f2c7b5ea-07b6-4b77-8023-bec9596fcc32
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.subservice: teams-audio-conferencing
search.appverid: MET150
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
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

When you set up Audio Conferencing in Microsoft 365 or Office 365, you get phone numbers for your users through an audio conferencing bridge. A conferencing bridge can have one or more phone numbers that are included at the bottom of the meeting invite. These phone numbers allow users to join Microsoft Teams meetings by dialing in.

As an admin, you can manage whether an entry and exist announcement is played when participants who dialed into the meeting join or exit.

> [!NOTE]
> [!INCLUDE [updating-admin-interfaces](includes/updating-admin-interfaces.md)]
  
## Setting meeting join options using the Microsoft Teams admin center

You must be a Teams service admin to make these changes. See [Use Teams administrator roles to manage Teams](./using-admin-roles.md) to read about getting admin roles and permissions.

1. Navigate to **Meetings** > **Conference Bridges**.

2. At the top of the **Conference Bridges** page, select **Bridge Settings**.

3. In the **Bridge settings** pane, enable or disable **Meeting entry and exit notifications**. This setting is enabled by default. If you disable it, participants in the meeting aren't notified when someone enters or leaves.

4. Under **Entry/exit announcement type**, select **Names or phone numbers** or **Tones**.

   > [!NOTE]
   > By default, external participants can't see the phone numbers of dialed-in participants. If you want to maintain the privacy of these phone numbers, select **Tones** for **Entry/exit announcement type** (this prevents the numbers from being read out by Teams).

5. If you chose **Names or phone numbers**, enable or disable **Ask callers to record their name before joining the meeting**.

6. Select **Save**.

## Turn on or off entry and exit announcements with PowerShell

To turn entry and exit announcements on or off with PowerShell, use the **`-EnableEntryExitNotifications`** parameter within the PowerShell CsOnlineDialInConferencingTenantSettings cmdlet.

For CsOnlineDialInConferencingBridge script examples, see [Set-CsOnlineDialInConferencingBridge](/powershell/module/teams/Set-csonlinedialinconferencingtenantsettings).

## Related topics

-[Audio Conferencing common questions](audio-conferencing-common-questions.md)
