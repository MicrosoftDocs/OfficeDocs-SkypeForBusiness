---
title: Configure live event settings in Microsoft Teams
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.date: 10/01/2023
ms.topic: article
ms.service: msteams
ms.reviewer: 
audience: admin
search.appverid: MET150
ms.localizationpriority: medium
ms.collection: 
- M365-collaboration
- m365initiative-meetings
- m365initiative-meetings-enabler
- enabler-strategic
- highpri
description: Learn how to manage settings for Teams live events that are held in your organization.
f1.keywords:
- CSH
ms.custom:
- ms.teamsadmincenter.liveevents.settings
appliesto: 
  - Microsoft Teams
---

# Configure live event settings in Microsoft Teams

> [!NOTE]
> Teams live events will be deprecated on September 30, 2024. We recommend that you use town halls instead. For details, see [Plan for Teams town halls](/microsoftteams/plan-town-halls).

Use Teams live events settings to configure settings for live events that are held in your organization. You can set up a support URL and configure a third-party video distribution provider. These settings apply to all live events that are created in your organization.

You can easily manage these settings in the Microsoft Teams admin center. In the left navigation, go to **Meetings** > **Live events settings**.

![Screen shot of Teams live events settings.](../media/teams-live-events-settings-new.png "Screen shot of Teams live events settings that you can configure in the Microsoft Teams admin center")

## Set up event support URL

This URL is shown to live event attendees. Add the support URL for your organization to give attendees a way to contact support during a live event.

### Using the Microsoft Teams admin center

1. In the left navigation, go to **Meetings** > **Live event settings**.
2. Under **Support URL**, enter your organization's support URL.

    ![Support URL setting for live events in the admin center.](../media/teams-live-events-settings-supporturl.png "Screen shot of support URL setting for Teams live events")

### Using Windows PowerShell

Run the following:

```PowerShell
Set-CsTeamsMeetingBroadcastConfiguration -SupportURL “{your URL}”
```

For more information, see [Set-CsTeamsMeetingBroadcastConfiguration](/powershell/module/skype/set-csteamsmeetingbroadcastconfiguration?view=skype-ps&preserve-view=true).

## Configure a third-party video distribution provider

For information about setting up a software defined network (SDN) solution or enterprise content delivery network (eCDN) solution, see [Enterprise content delivery networks for streaming Microsoft Teams events](/microsoftteams/streaming-ecdn-enterprise-content-delivery-network).

## Related topics

[What are Teams live events?](what-are-teams-live-events.md)

[Plan for Teams live events](plan-for-teams-live-events.md)

[Set up for Teams live events](set-up-for-teams-live-events.md)
