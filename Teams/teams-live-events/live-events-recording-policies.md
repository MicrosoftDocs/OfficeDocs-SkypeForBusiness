---
title: Live events recording policies
author: cichur
ms.author: v-cichur
manager: serdars
ms.date: 06/09/20
ms.topic: article
ms.service: msteams
ms.reviewer: ashwin
audience: admin
search.appverid: MET150
f1.keywords:
- CSH
localization_priority: Normal
ms.collection: 
  - M365-collaboration
description: Learn about live event recording policies.
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-mar2020
---

# Live event recording policies in Microsoft Teams

You have several options for recording a Microsoft Teams live event. The recording options are set using recording policies. This article describes the various settings.

## Scheduling & option behavior

There are two organizer options while scheduling a live event recording:

- Recording available for producers and presenters

  - Recording file: Provides a recording file that producers/presenters can download after the event is over

- Recording available for attendees

  - DVR: Allows attendees to rewind and pause during the event

  - VOD: Allows attendees to watch after the event is over

## Broadcast recording policy setting

As part of the broadcast policy, there is a setting that you can toggle to turn on/off recording for a live event.

|                                 | Recording available for producers and presenters | Recording available for attendees |
| ------------------------------- | ---------------------------------------------------- | ------------------------------------- |
| Always record               | Disabled and selected                                | Enabled and selected by default       |
| Organizer can record or not | Enabled and not selected by default                  | Enabled and not selected by default   |
| Never record               | Disabled and not selected                            | Disabled and not selected      |

When the policy is set to **Always record**, the policy page has the following selected options:

![Screen shot of live events policy settings](../media/live-event-policies.png "Screen shot of live events policy settings in the Microsoft Teams admin center")

## Storage & persistence behavior

| Option                                       | State   | DVR                                                   | VOD                                                     | Recording                |
| ------------------------------------------------ | ------------ | --------------------------------------------------------- | ----------------------------------------------------------- | ---------------------------- |
| Recording available to producers and presenters | Selected     | DVR is available and the AMS asset is stored for 180 days | Attendee can access and watch the event                     |                              |
|                                                  | Not Selected | DVR is available and the AMS asset is stored for 180 days | Attendee will not get access into the event after it's over |                              |
| Recording available to producers and presenters | Selected     |                                                           |                                                             | An MP4 is created and stored |
|                                                  | Not Selected |                                                           |                                                             | No file is created           |

### Related topics

- [What are Teams live events?](what-are-teams-live-events.md)
- [Plan for Teams live events](plan-for-teams-live-events.md)
- [Configure live events settings in Teams](configure-teams-live-events.md)
- [Teams cloud meeting recording](../cloud-recording.md)
