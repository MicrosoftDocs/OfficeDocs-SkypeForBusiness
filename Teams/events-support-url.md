---
title: Set up event support URL for town halls
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.date: 07/01/2023
ms.topic: article
ms.service: msteams
ms.reviewer: sonua
audience: admin
search.appverid: MET150
ms.localizationpriority: medium
ms.collection: 
- M365-collaboration
- m365initiative-meetings
- m365initiative-meetings-enabler
- enabler-strategic
- highpri
description: Learn how to set up an event support URL for town halls in Microsoft Teams.
f1.keywords:
- CSH
ms.custom:
- ms.teamsadmincenter.liveevents.settings
appliesto: 
  - Microsoft Teams
---

# Set up event support URL for town halls

Use Teams live events settings to configure settings for live events that are held in your organization. You can set up a support URL and configure a third-party video distribution provider. These settings apply to all live events that are created in your organization.

You can easily manage these settings in the Microsoft Teams admin center. In the left navigation, go to **Meetings** > **Live events settings**.

## Set up event support URL

This URL is shown to live event attendees. Add the support URL for your organization to give attendees a way to contact support during a live event.

### Using the Microsoft Teams admin center

1. In the left navigation, go to **Meetings** > **Live event settings**.
2. Under **Support URL**, enter your organization's support URL.

### Using Windows PowerShell

Run the following:

```PowerShell
Set-CsTeamsMeetingBroadcastConfiguration -SupportURL “{your URL}”
```

For more information, see [Set-CsTeamsMeetingBroadcastConfiguration](/powershell/module/skype/set-csteamsmeetingbroadcastconfiguration?view=skype-ps&preserve-view=true).

