---
title: Overview of the encoder for streaming in Microsoft Teams
author: MicrosoftHeidi
ms.author: heidip
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-collaboration
ms.reviewer: asteele
search.appverid: MET150
f1.keywords:
- NOCSH
description: This article will give an overview of encoder-based RTMP configuration for Microsoft Teams streaming events.
localization_priority: Normal
appliesto: 
  - Microsoft Teams
ms.custom:
---
# Live streaming events in Microsoft Teams

You can create live events using Microsoft Teams across your organization. You can schedule, produce, and deliver live events for various scenarios such as company-wide events, leadership updates, and more. Live streaming events enable producers to curate and control the content that's broadcast to an audience.

You can create, schedule, and run live events using a single bitrate RTMP or RTMPS stream from an encoder – we’ll take care of all the transcoding for adaptive bitrate delivery to your viewers.

Just like any other video in Teams, you can make the live event open to your entire company or limit the access to specific groups. This provides an end-to-end creation and viewing experience inside of Teams.

After the event, the video will be available on demand with intelligent features including:

- Speech-to-text and closed captions.
- Transcript search and timecodes let you quickly find moments that matter in a video.

## Live events in Microsoft 365

You can create a live steaming event in Teams or Yammer — wherever your audience, team, or community resides. Attendees can participate in real time, with high-definition (HD) video and interactive discussion, or catch up later with powerful AI features that unlock the content of the event recording. Seamless integration across Microsoft 365 means that you can use Teams to deliver highly produced, studio-quality events.

## Get started

Ensure that users you want to be able to create live events have the granted permissions required to create a live event. By default, everyone in your organization can create a live event, however a Teams admin can restrict access. Learn more about live event administration.

- Go to **Admin settings** > **Live events**.
- Select **Create** > **Live event**. Follow the instructions in **Create a live event** in Teams

## Monitor your event

As an organizer or producer you can monitor the audience engagement in real-time. Quickly toggle between audience and producer views to see different screens and monitor analytics like current viewers, likes, and total views for your event.

## Capabilities

The following are capabilities of live streaming events:

|Operation  |Limits  |
|---------|---------|
|Create live events in Teams (with external encoder)  |Enterprise (E1, E3, E5), Education (A3, A5)                          |
|Watch live event                                     |Viewers with permissions to view the event and a valid Teams license |
|Maximum resolution                                   |720p                                                                 |
|Maximum concurrent live events (in pre-live or live) |15                                                                   |
|Active concurrent viewers                            |10000                                                                |
|Maximum length of live event                         |4 hours                                                              |
|Partner network caching support                      |Hive, Kollective, Ramp                                               |
|Other network caching support                        |May work, but isn't supported                                        |
|Attendee DVR controls                                |Pause, playback speed (2x catch up, 1x at live), seek                |
|Real-time captions                                   |708 caption pass-through from encoder                                |
|Automatic speech-to-text and captions                |Processed after event                                                |
|Interactive discussions                              |Supported via Yammer when event is created from Yammer               |
|Teams comments                                       |Available after the event ends                                       |
|On-demand viewing on live event (after event)        |Automatic transition for live to on-demand for immediate viewing and indexing in Teams |
|Downloadable recording                               |Processed and available after live event by owners                   |

Live events in Teams is a highly available service and you can expect good performance at scale. In the very unlikely scenario that results in failover being required, live events using external encoding will not have redundancy and are not recoverable.
