---
title: Microsoft Teams Monitoring and Alerting 
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: conceptual
ms.service: msteams
ms.reviewer: vapati
ms.date: 07/30/2023
f1.keywords:
ms.localizationpriority: medium
search.appverid:
ms.collection: 
  - M365-collaboration
description: Learn about the Teams alerts and notifications capabilities available in the Microsoft Teams admin center.
appliesto: 
  - Microsoft Teams
ms.custom: 
---

# Microsoft Teams monitoring and alerting

Monitoring and alerting capabilities for Microsoft Teams are available in the Teams admin center. Use different sets of rules available under the **Notifications & alerts** section in the Teams admin center to monitor Teams capabilities and receive alerts. For example, you can actively monitor the health of Teams devices such as IP Phones, Teams Rooms on Android, and others if they unexpectedly go offline.  

You can use Teams monitoring and alerting to do the following items:

- Automatically manage Teams capabilities
- Be alerted if they show something unexpected.
- Take corrective actions to get things back on-track.

> [!NOTE]
> The some of the alert functionalities within the Teams admin center is not available in GCC/GCC-High/DoD environments.

## How to manage monitoring and alerting

You must be a global admin in Microsoft 365 or a Teams service admin to configure alerting rules. See [Use Teams administrator roles to manage Teams](../using-admin-roles.md) to learn more about Teams admin roles and which reports each admin role can access.

1. Sign in to the Teams admin center.
2. From the left navigation, select **Notifications & alerts**.
3. Choose the rule you want to configure from **Rules**.

## How alerts are delivered
Alerts are delivered either as a Teams channel message or via webhooks depending on what options admin configures in rule.

Teams Channel alerts are delivered through bot app named **Teams Admin Center**. This bot app is auto-instlled into Team that is choosen by admin while rule configuration to recieve notifications.   


## Teams monitoring rules reference

The following is a list of the Teams monitoring rules available in the Teams admin center.

|Rule  |Monitoring capability|What's monitored? |Public|GCC|GCCH|DoD|
|---------|---------|---------|---------|---------|---------|---------|
|[App submissions](../submit-approve-custom-apps.md) |Teams Apps | Proactively monitor Teams apps if they are submitted for approval.|Yes|Yes|No|No|
|[Device state rule](device-health-status.md)  |Teams Devices | Proactively monitor Teams devices if they go offline.|Yes|Yes|No|No|
|[Audio quality for in-progress meetings](alerts-in-progress-meeting-audio.md)|Teams meetings|Specified users' audio quality for in-progress meetings|Yes|No|No|No|
|[Video quality for in-progress meetings](alerts-in-progress-meeting-video.md)|Teams meetings|Specified users' video quality for in-progress meetings|Yes|No|No|No|
|[Screen sharing quality for in-progress meetings](alerts-in-progress-meeting-screen-sharing.md)|Teams meetings|Specified users' app sharing quality for in-progress meetings|Yes|No|No|No|

## Related topics

[Real-time telemetry limitations](/microsoftteams/use-real-time-telemetry-to-troubleshoot-poor-meeting-quality#limitations)
