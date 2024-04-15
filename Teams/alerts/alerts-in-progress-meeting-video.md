---
title: Alerts for in-progress meeting video quality issues
ms.author: jtremper
author: jacktremper
manager: pamgreen
ms.reviewer: vapati
ms.date: 01/30/2024
ms.topic: article
ms.service: msteams
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
f1.keywords:
- NOCSH
ms.custom: 
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
  - Tier2
description: Learn how to set up alerts for video quality issues detected in in-progress meetings.
---

# Alerts for in-progress meeting video quality issues

[!INCLUDE[Teams Premium ECM](../includes/teams-premium-ecm.md)]

You can set up alerts for in-progress meeting video issues and be informed immediately when the users you specify experience issues.

Notifications are available for source freeze count, loss recovery attempt rate, and video encoder hardware failure. You can set the threshold for each of these as well as the frequency of notification.

Notifications can  be sent to a Teams channel or a web hook URL.

To be monitored, meeting attendees must have a Teams Premium or Teams Rooms Pro license.

## Set up alerts for video quality issues

1. In the left navigation of the Microsoft Teams admin center, select **Notifications & alerts** > **Rules**.

1. In the **Rules** Page, select **Audio quality for in-progress meetings**.

1. Select the options as described in the following table, and then select **Save**.

|Field |Description  |
|:-----|:------------|
|**Video conditions**|Choose the video issues that you want to monitor for.|
|**Monitoring settings**|Choose the **Notification threshold** and **Monitoring window** to specify how long the condition should exist before an alert is sent.<br>Choose the **Notification waiting period** to specify how often an alert is sent.|
|**Scope**|Choose the users whose meeting audio quality you want to monitor.|
|**Network subnet selection for notifications**|Select which networks you want to get alerts for.|
|**Actions**|Choose if you want to send alerts to a specific channel or to a web hook URL.|
|**Status**|Choose if the rule is active and alerts should be sent.|

## Related topics

[Alerts for audio quality issues](alerts-in-progress-meeting-audio.md)

[Alerts for screen sharing issues](alerts-in-progress-meeting-screen-sharing.md)

[Real-time telemetry limitations](/microsoftteams/use-real-time-telemetry-to-troubleshoot-poor-meeting-quality#limitations)
