---
title: Live events in Microsoft Teams overview
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
ms.reviewer: christi.balaki
ms.date: 10/3/2024
search.appverid: MET150
f1.keywords:
- NOCSH
description: This article gives an overview of encoder-based RTMP configuration for Microsoft Teams streaming events.
ms.localizationpriority: Medium
appliesto: 
  - Microsoft Teams
ms.custom:
---
# Live events in Microsoft Teams overview

> [!NOTE]
> We're currently still supporting live events. While we still recommend you to upgrade to [Teams town halls](plan-town-halls.md) to take advantage of new features and experiences, your users can continue to schedule events. For more information, see [Updates for Town Hall in Microsoft Teams and Teams Live Events](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/extension-for-teams-live-events-retirement/ba-p/4148352).

Users in your organization can create live events using Microsoft Teams. Your users can schedule, produce, and deliver live events for various scenarios such as company-wide events, leadership updates, and more. Live streaming events allow producers to curate and control the content that is broadcast to an audience.

Your users can create, schedule, and run live events using a single bitrate RTMP or RTMPS stream from an encoder – we take care of all the transcoding for adaptive bitrate delivery to your viewers.

Just like any other video in Teams, as an admin, you decide who can join live events in your organization. Managing the event access type provides an end-to-end creation and viewing experience inside of Teams.

After the event, the video is available on demand with intelligent features including:

- Speech-to-text and closed captions.
- Transcript search and time codes to quickly find moments that matter in a video.

## Live events in Microsoft 365

Your users can create live events in Teams or Viva Engage, wherever your audience, team, or community resides. Attendees can watch the event in high-definition (HD) video and submit questions through a moderated Q&A experience. Seamless integration across Microsoft 365 means that you can use Teams to deliver highly produced, studio-quality events.

## Get started

Ensure that users you want to create live events have the permissions required to create a live event. By default, everyone in your organization can create a live event, however you can restrict access.

1. In the left navigation of the Teams admin center, go to **Meetings** > **Live events policies** > the **Manage Policies** tab.
1. If you want to:
    1. edit the existing default policy, choose **Global (Org-wide default)**.
    1. create a new custom policy, choose **+Add**.
    1. edit a custom policy, select the policy, and then choose **Edit**.

## Monitor your event

Producers can use the Teams client to see the audience feed (visible on the right side) and the number of attendees currently viewing the event.

## Capabilities

The following are capabilities of live streaming events:

|Operation                                            |Limits                                                               |
|-----------------------------------------------------|---------------------------------------------------------------------|
|Create live events in Teams (with external encoder)  |Enterprise (E1, E3, E5), Education (A3, A5)                          |
|Watch live event                                     |Viewers with permissions to view the event and a valid Teams license (unless the event is public, then a license to view isn't required) |
|Maximum resolution                                   |720p                                                                 |
|Maximum concurrent live events (in prelive or live) |15<sup>1</sup>                                                                   |
|Active concurrent viewers                            |10000<sup>1</sup>                                                                |
|Maximum length of live event                         |4 hours <sup>1</sup>                                                             |
|Partner networks caching support                      |Hive, Kollective, Riverbed, Ramp, Microsoft                          |
|Other network caching support                        |Might work, but isn't supported                                        |
|Attendee DVR controls                                |Pause, playback speed (2x catch up, 1x at live), seek                |
|Real-time captions                                   |708 caption pass-through from encoder                                |
|Automatic speech-to-text and captions                |Processed after the event                                            |
|Interactive discussions                              |Supported via Viva Engage when the event is created from Viva Engage           |
|Teams comments                                       |Available after the event ends                                       |
|On-demand viewing on live event (after event)        |Automatic transition for live to on-demand for immediate viewing and indexing in Teams |
|Downloadable recording                               |Processed and available after the live event by owners               |

<sup>1</sup> The limits that are set might be changed. Check [Limits and specifications for Teams](limits-specifications-teams.md).<br/>

Teams live events is a highly available service and you can expect good performance at scale. In the unlikely scenario that results in failover being required, live events using external encoding don't have redundancy and aren't recoverable.

## Related topics

- [What are Teams live events?](what-are-teams-live-events.md)
- [Plan for Teams live events](/MicrosoftTeams/teams-live-events/plan-for-teams-live-events)
- [Set up for Teams live events](/MicrosoftTeams/teams-live-events/set-up-for-teams-live-events)
