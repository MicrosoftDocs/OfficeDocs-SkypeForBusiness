---
title: Viewing Microsoft Teams Rooms events
ms.author: tonysmit
author: mstonysmith
manager: pamgreen
ms.reviewer: kimmatlock
ms.date: 05/20/2024
ms.topic: article
audience: admin
appliesto:
 - Microsoft Teams
ms.service: msteams
ms.subservice: itpro-rooms
ms.collection:
 - M365-collaboration
 - teams-rooms-consoles
 - Tier1
f1.keywords:
 - NOCSH
search.appverid: MET150
ms.localizationpriority: medium
description: Read this article to learn more about the event feed in the Microsoft Teams Rooms Pro Management portal. 
---

# Events feed in Microsoft Teams Rooms Pro Management Portal

The Event feed in the Teams Rooms Pro Management portal is the way to view and highlight room events that have happened in the past. The event feed is the central place to view historical occurrences, like poor calls, user-reported issues, and other information.

Events are informative and differ from tickets and signals. They don't need to be triaged, but one or more can be used to flag rooms as **unhealthy**. Flagging a room as unhealthy from the events feed then creates a support ticket.

## Event feed

Events represent activity of the past like issues that occurred briefly, changes to the device, or interactions with the device. Events are informative and differ from health signals, which represent the current condition of devices. They don't need to be triaged, but one or more can be used to flag rooms as unhealthy.

**To view events:**

1. In the left navigation of the Microsoft Teams Rooms Pro Management portal, go to  **Events**

**Types of events**

|Event Type|Source|Description|
| -------- | -------- | -------- |
|Poor Call Detected|Call Record |Call analytics detected poor call quality.  |
|Report an Issue|Teams Room|When a user in a Teams Room reports an issue from the Teams Rooms device, an end user report feedback event is created in the Teams Rooms Pro Management portal Events feed. This event gives managers the data they need to address the feedback or open a support case with specific logs generated when the user submitted the feedback. Logs will remain on the device for 30 days.  The feature is enabled through the Skype XML setting \<SendFeedbacktoPMP\>True\</SendFeedbacktoPMP\>|

  ------------------------------------------------------------------------
  **Flag as unhealthy**

While events are meant to be informative, it's possible to elevate one or more events into a support ticket which will in turn mark the Teams Rooms as unhealthy. This feature is useful if a pattern of events is perceived as problematic and requires further troubleshooting.

**To flag a room as unhealthy:**

1. In the left navigation of the Microsoft Teams Rooms Pro Management portal, go to **Events**.
2. Select one or more events in the list and **Flag as unhealthy**.
3. On the **Details** page, in the Description field, describe as best as possible the issue. Select **High Impact** to elevate importance to your support if the incident is causing significant health degradation for a critical room. Choose **Next.**
4. On the **Events** page, select more events to add to this issue if needed. Choose **Next.**
5. On the **Finish** page, review the details of the issue. If you're satisfied with the configuration, choose **Submit**. If you want to edit a section, use the **Previous** button or select the step in the left navigation.
