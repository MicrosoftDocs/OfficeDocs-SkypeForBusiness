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

- Recording Available for Producers and Presenters

  - Recording File: Provides a recording file that Producers/Presenters can download after the event is over

- Recording Available for Attendees

  - DVR: Allows attendees to rewind and pause during the event

  - VOD: Allows attendees to watch after the event is over

## Broadcast recording policy setting

As part of the broadcast policy, there is a setting that you can toggle to turn on/off recording for a live event.

|                                 | **Recording available for producers and presenters** | **Recording available for attendees** |
| ------------------------------- | ---------------------------------------------------- | ------------------------------------- |
| **Always Record**               | Disabled and Selected                                | Enabled and Selected by Default       |
| **Organizer can record or not** | Enabled and Not Selected by Default                  | Enabled and Not Selected by Default   |
| **Never Record**                | Disabled and Not Selected                            | Enabled and Selected by Default       |

## Flags set on Client

| **Can be set by User**                                         | **Flag/Capability set by client?** | **Flag**                 | **Implications**                                                                                               |
| -------------------------------------------------------------- | ---------------------------------- | ------------------------ | -------------------------------------------------------------------------------------------------------------- |
| Organizer Option: Recording available for Attendee             | Yes                                | Capabilities.VOD         | If True, Attendee Service admits user after event is over                                                      |
| Organizer Option: Recording available for Producer & Presenter | Yes                                | Capabilities.Recording   | If True, generates mp4                                                                                         |
| Admin Setting: Never Record Admin Policy Setting               | No                                 | Capabilities.DoNotRecord | If DoNotRecord is set, then by definition, MP4, VOD AND DVR must all be disabled – no assets should be stored. |

## Storage & Persistence Behavior

| **Option**                                       | **State**    | **DVR**                                                   | **VOD**                                                     | **Recording**                |
| ------------------------------------------------ | ------------ | --------------------------------------------------------- | ----------------------------------------------------------- | ---------------------------- |
| **Recording Available for Producers/Presenters** | Selected     | DVR is available and the AMS asset is stored for 180 days | Attendee can access and watch the event                     |                              |
|                                                  | Not Selected | DVR is available and the AMS asset is stored for 180 days | Attendee will not get access into the event after it's over |                              |
| **Recording Available for Producers/Presenters** | Selected     |                                                           |                                                             | An MP4 is created and stored |
|                                                  | Not Selected |                                                           |                                                             | No file is created           |

## Mitigation

### End User Changes & Fixes

<table>
<thead>
<tr class="header">
<th><strong>End User Scenario</strong></th>
<th><strong>Requirement/Fix</strong></th>
<th><strong>Notes</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>When the Live Event Recording Policy setting is set to “Never Record” don’t allow organizers to select any recording options</td>
<td><ul>
<li><p>Disable and grey out the “Recording for Attendees”</p></li>
</ul></td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td><ul>
<li><p>Set the following:</p></li>
</ul>
<p>Capabilities.DoNotRecord = true</p></td>
<td></td>
</tr>
<tr class="odd">
<td>When the policy is set to “Never Record” the system does not store any recording assets</td>
<td><ul>
<li><p>If the DoNotRecord flag is set to true then:</p>
<ul>
<li><p>Delete the AMS asset used for DVR after the event is over</p></li>
<li><p>Never create a recording MP4</p></li>
</ul></li>
</ul></td>
<td>Users who paused during the event and resumed after it’s over would get a playback error since the AMS asset has been deleted</td>
</tr>
</tbody>
</table>

### New State

|                                 | **Recording Available for Producers and Presenters** | **Recording Available for Attendees** |
| ------------------------------- | ---------------------------------------------------- | ------------------------------------- |
| **Always Record**               | Enabled and Selected by Default                      | Enabled and Selected by Default       |
| **Organizer can record or not** | Enabled and Not Selected by Default                  | Enabled and Not Selected by Default   |
| **Never Record**                | Disabled                                             | Disabled                              |

### New State with options

| **Option**                                       | **State**    | **DVR**                                                       |**VOD**                                                     | **Recording**                |
| ------------------------------------------------ | ------------ | ------------------------------------------------------------- | ----------------------------------------------------------- | ---------------------------- |
| **Recording Available for Producers/Presenters** | Selected     | DVR is available and the AMS asset is stored for 180 days     | Attendee can access and watch the event                     |                              |
|                                                  | Not Selected | DVR is available and the AMS asset is deleted after the event | Attendee will not get access into the event after it's over |                              |
| **Recording Available for Producers/Presenters** | Selected     |                                                               |                                                             | An MP4 is created and stored |
|                                                  | Not Selected |                                                               |                                                             | No file is created           |

### Phases

**Phase 1** – Put the new changes behind an ECS flag and enable for a
handful of tenants

**Phase 2** –

- Make changes to the DVR:
    
  - .DoNotRecord is set = no VOD
    
  - Separate DVR option for end user so that AMS asset doesn’t get
        created in the first place.

- Get feedback from users on the policy change before releasing to all
    users.


### Related topics

- [What are Teams live events?](what-are-teams-live-events.md)
- [Plan for Teams live events](plan-for-teams-live-events.md)
- [Configure live events settings in Teams](configure-teams-live-events.md)
