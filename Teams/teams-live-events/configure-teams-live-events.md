---
title: Configure live event settings in Microsoft Teams
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.date: 8/14/2024
ms.topic: article
ms.service: msteams
ms.reviewer: chbalaki
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
> Teams live events are no longer going away on September 30, 2024. While we still recommend you to upgrade to [Teams town hall](../plan-town-halls.md) when ready to take advantage of new features and experiences, your users can continue to schedule events beyond September 2024. For more information, see [Updates for Town Hall in Microsoft Teams and Teams Live Events](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/extension-for-teams-live-events-retirement/ba-p/4148352).

Teams live events settings  allow you, as an admin, to manage settings for live events in your organization. You can set up a support URL and configure a third-party video distribution provider. These settings apply to all live events that are created in your organization.

![Screen shot of Teams live events settings.](../media/teams-live-events-settings-new.png "Screen shot of Teams live events settings that you can configure in the Microsoft Teams admin center")

## Add event support URL

The support URL for the event is shown to live event attendees. Add your organization's support URL so attendees can contact support during live events.

### Use the Microsoft Teams admin center to add an event support URL

1. Open the Teams admin center.
2. Expand **Meetings** from the navigation pane.
3. Under **Meetings**, select **Live event settings***.
4. Under **Support URL**, enter your organization's support URL.
5. Select **Save**

### Use PowerShell to add an event support URL

In PowerShell, the **`-SupportURL`** parameter in the **CsTeamsMeetingBroadcastConfiguration** cmdlet allows you to add a support URL for live events.

To add a support URL, use the following script:

```PowerShell
Set-CsTeamsMeetingBroadcastConfiguration -SupportURL “{your URL}”
```

## Configure a third-party video distribution provider

For information about setting up a software defined network (SDN) solution or enterprise content delivery network (eCDN) solution, see [Enterprise content delivery networks for streaming Microsoft Teams events](/microsoftteams/streaming-ecdn-enterprise-content-delivery-network).

## Related topics

- [Set-CsTeamsMeetingBroadcastConfiguration](/powershell/module/teams/set-csteamsmeetingbroadcastconfiguration)
- [What are Teams live events?](what-are-teams-live-events.md)
- [Plan for Teams live events](plan-for-teams-live-events.md)
- [Set up for Teams live events](set-up-for-teams-live-events.md)
