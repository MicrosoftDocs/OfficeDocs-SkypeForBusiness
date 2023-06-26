---
title: Set up alerts for in-progress meeting audio quality issues
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.reviewer: vapati
ms.date: 07/15/2023
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
  - ms.teamsadmincenter.meetingsettings.invitationurls
  - ms.teamsadmincenter.meetingsettings.network.ports
  - ms.teamsadmincenter.meetingsettings.overview
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
  - Tier2
description: Learn how to set up alerts for audio quality issues detected in in-progress meetings.
---

# Set up alerts for in-progress meeting audio quality issues







## Configure device state rule

1. In the left navigation of the Microsoft Teams admin center, select **Notifications & alerts** > **Rules**.

1. In the **Rules** Page, select **Device state rule**.

1. Select the options as described in the following table, and then select **Save**.



|Field |Description  |
|:-----|:------------|
|**Audio conditions**|Choose the audio issues that you want to monitor for.|
|**Monitoring settings**|Choose the **Notification threshold** and **Monitoring window** to specify how long the condition should exist before an alert is sent.<br>Choose the **Notification waiting period** to specify how often an alert is sent.|
|**Scope**|Choose the users or groups whose meeting audio quality you want to monitor.|
|**Actions**|Choose if you want to send alerts to a specific channel or to a web hook URL.|
|**Status**|Choose if the rule is active and alerts should be sent.|



