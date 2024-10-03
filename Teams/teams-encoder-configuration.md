---
title: Encoder configuration for streaming in Microsoft Teams
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
description: This article discusses encoder-based RTMP configuration for Microsoft Teams streaming events.
ms.localizationpriority: medium
appliesto: 
  - Microsoft Teams
ms.custom:
---

# Configuring encoders for live event streaming in Microsoft Teams

> [!NOTE]
> We're currently still supporting live events. While we still recommend you to upgrade to [Teams town halls](plan-town-halls.md) to take advantage of new features and experiences, your users can continue to schedule events. For more information, see [Updates for Town Hall in Microsoft Teams and Teams Live Events](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/extension-for-teams-live-events-retirement/ba-p/4148352).

Teams accepts live feeds from various different encoders that output RTMP or RTMPS. Each encoder is different, so make sure to follow the guidelines for the encoder configurations when sending to Teams.

To learn how to set up a live event in Teams, see [Set up for live events in Microsoft Teams](/MicrosoftTeams/teams-live-events/set-up-for-teams-live-events). If you're already using an encoder integrated with Teams, see [configuring encoders for live streaming](teams-encoder-setup.md).

## Configuration Steps

After you schedule the live event using Teams or Viva Engage, and select the **Teams Encoder** option, you can retrieve the RTMP URL and key from the meeting invite and use them to send the feed into the Teams producer UI.

### Gather the RTMP information

#### Scheduled in Teams

1. Open the Teams client and navigate to the **Calendar**.
1. Select the scheduled live event and select the double arrow button to see the invite details.
1. Go down to the **RTMP in details** section.
1. Select the **Get RTMP** link to copy the RTMP ingest URL to the clipboard.
1. Select the **Get RTMP key** to copy the RTMP key to the clipboard.

#### Scheduled in Viva Engage

1. Navigate to the Viva Engage community where the event was scheduled.
1. Select the **Events** tab to see upcoming scheduled events.
1. Select the desired event to bring up the details page.
1. On the right side, under **Produce**, Select the **RTMP information** link to expose the RTMP URL and key.

## Encoder Setup

1. Once you collect the RTMP information, ensure your encoder is configured with the correct settings in the recommended encoder settings section.
1. Enter the RTMP URL and Key into your encoder's streaming settings (refer to the manufacturer's documentation for specifics).
1. Configure your encoder with the desired audio and video sources.
1. Open the Teams client and join the live vent as a Producer.
1. Start streaming from the encoder to the Teams RTMP ingest URL.
1. In the Teams Producer window, after a few seconds, the encoder's RTMP feed appears in the presenter area.
1. Select on the RTMP feed in the presenter area to place it into the queue on the left side.
1. When you're satisfied with the feed, select **Send Live** - the feed then also appears on right side of the Producer window.
1. Select **Start** to begin the stream.

## Recommended encoder settings

### Ingest protocols

- Single bitrate RTMPS or RTMP

### Video format

- Aspect Ratio: 16:9
- Codec: H.264
- Profile: High (Level 4.0)
- Bitrate: Up to 5 Mbps (5,000 kbps)
- Strict Constant Bitrate (CBR)
- Keyframe/GOP: 2 seconds
  - There must be an IDR frame at the beginning of each GOP
  - Frame Rate: 29.97 fps or 30 fps
  - Resolution: 1280 x 720 (720 P)
  - Interlace Mode: Progressive

### Audio format

- Codec: AAC (LC)
- Bitrate: 192 kbps
- Sample Rate: 48 kHz or 44.1 kHz (recommend 48 kHz)

### Playback requirements

- Both an audio and video stream must be present in order to play back content in Teams.

### Configuration tips

- Whenever possible, use a hardwired internet connection.
- When determining bandwidth requirements, it's advisable to double the streaming bitrates. While doubling the streaming bitrates isn't a mandatory requirement, it helps mitigate network congestion.

- When using software-based encoders, close any unnecessary programs.
- Don't change your encoder configuration after it starts pushing. It has negative effects on the event and can cause the event to be unstable. If you want to change encoder configurations before the event starts, you must disconnect using the producer controls in Teams and start setup again.
- If the encoder is disconnected during the live event, reconnect it keeping the same timestamps of continuing process. Any discontinuity might cause audio or video issues on certain browsers and devices.
- Give yourself ample time to set up your event. For high scale events, it's recommended to start the setup an hour before your event.
- If you're using the vMix encoder for RTMP-In, make sure to select the FFMPEG6 option from the **Application** drop-down menu in the vMix encoder settings.

## Related topics

- [What is Teams live events?](/MicrosoftTeams/teams-live-events/configure-teams-live-events)
- [Plan for Teams live events](/MicrosoftTeams/teams-live-events/configure-teams-live-events)
- [Configure live events settings in Teams](/MicrosoftTeams/teams-live-events/configure-teams-live-events)