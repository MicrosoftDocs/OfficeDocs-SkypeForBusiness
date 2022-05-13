---
title: Live events recording policies
author: SerdarSoysal
ms.author: serdars
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: christi.balaki
audience: admin
search.appverid: MET150
f1.keywords:
- CSH
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
description: Learn about live event recording policies.
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-mar2020
---

# Live event recording policies in Microsoft Teams

You have several options for recording a Microsoft Teams live event. The recording options are set using recording policies. This article describes the various settings.

The recording options are set using the PowerShell command [Set-CsTeamsMeetingBroadcastPolicy](/powershell/module/skype/set-csteamsmeetingbroadcastpolicy).

## Scheduling and option behaviors

There are two organizer options while scheduling a live event recording:

- Recording available for producers and presenters

  - Recording file: Provides a recording file that producers and presenters can download after the event is over.

- Recording available for attendees

  - DVR: A digital video recorder (DVR) allows attendees to rewind and pause during the event

  - VOD: A video on demand (VOD) allows attendees to watch after the event is over

## Broadcast recording policy setting

As part of the broadcast policy, there's a setting that you can toggle to turn recording on or off for a live event.

| &nbsp;| Recording available for producers and presenters | Recording available for attendees |
| ------------------------------- | ---------------------------------------------------- | ------------------------------------- |
| Always record               | Disabled and selected                                | Enabled and selected         |
| Organizer can record or not | Enabled and selected by default                  | Enabled and selected by default   |
| Never record               | Disabled and not selected                            | Disabled and not selected      |

## Storage and persistence behavior

| Option                                       | State   | DVR                                                   | VOD                                                     | Recording                |
| ------------------------------------------------ | ------------ | --------------------------------------------------------- | ----------------------------------------------------------- | ---------------------------- |
| Recording available for attendees | Selected     | DVR is available and the Azure Media Services (AMS) asset is stored for 180 days | Attendee can access and watch the event                     |                              |
|                                                  | Not Selected | DVR is available and the AMS asset is stored for 180 days | Attendee won't get access into the event after it's over |                              |
||Disabled (Not selected)|DVR is available and the AMS asset is deleted after the event|Attendee won't get access into the event after it's over||
| Recording available to producers and presenters | Selected     |                                                           |                                                             | An MP4 is created and stored for 180 days |
|                                                  | Not Selected |                                                           |                                                             | No file is created           |

### Related topics

- [What is Teams live events?](what-are-teams-live-events.md)
- [Plan for Teams live events](plan-for-teams-live-events.md)
- [Configure live events settings in Teams](configure-teams-live-events.md)
- [Teams clouds meeting recording](../cloud-recording.md)
