---
title: Encoder configuration for streaming in Microsoft Teams
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
ms.reviewer: asteele
ms.date: 09/07/2022
search.appverid: MET150
f1.keywords:
- NOCSH
description: This article will discuss encoder-based RTMP configuration for Microsoft Teams streaming events.
localization_priority: Normal
appliesto: 
  - Microsoft Teams
ms.custom:
---

# Configuring encoders for live event streaming in Microsoft Teams

> [!NOTE]
> Teams live events will be deprecated on September 30, 2024. We recommend that you use town halls instead. For details, see [Plan for Teams town halls](/microsoftteams/plan-town-halls).

Teams accepts live feeds from a variety of different encoders that output RTMP or RTMPS. Each encoder is different, so make sure to follow the guidelines for the encoder configurations when sending to Teams.

To learn how to set up a Live event in Teams, read about creating live events. If you're already using an encoder that's integrated with Teams, read about [configuring encoders for live streaming](teams-encoder-setup.md).

## Configuration Steps

After you've scheduled the live event using Teams or Viva Engage, and selected the **Teams Encoder** option, you'll be able to retrieve the RTMP URL and key from the meeting invite and use them to send the feed into the Teams producer UI.

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

1. Once you've collected the RTMP information, ensure your encoder is configured with the correct settings as per the recommended encoder settings below.
1. Enter the RTMP URL and Key into your encoder's streaming settings (refer to the manufacturer's documentation for specifics).
1. Configure your encoder with the desired audio and video sources.
1. Open the Teams client and join the live vent as a Producer.
1. Start streaming from the encoder to the Teams RTMP ingest URL.
1. In the Teams Producer window, after a few seconds, the encoder's RTMP feed will appear in the presenter area.
1. Click on the RTMP feed in the presenter area to place it into the queue on the left side.
1. Once you're satisfied with the feed select **Send Live** - the feed will then also appear on right side of the Producer window.
1. Select **Start** to begin the stream.

## Recommended encoder settings

### Ingest protocols

- Single bitrate RTMPS or RTMP

### Video format

- Codec: H.264
- Profile: High (Level 4.0)
- Bitrate: Up to 5 Mbps (5000 kbps)
- Strict Constant Bitrate (CBR)
- Keyframe/GOP: 2 seconds
  - There must be an IDR frame at the beginning of each GOP
  - Frame Rate: 29.97 fps or 30 fps
  - Resolution: 1280 x 720 (720P)
  - Interlace Mode: Progressive

### Audio format

- Codec: AAC (LC)
- Bitrate: 192 kbps
- Sample Rate: 48 kHz or 44.1 kHz (recommend 48 kHz)

### Playback requirements

- Both an audio and video stream must be present in order to playback content in Teams.

### Configuration tips

- Whenever possible, use a hardwired internet connection.
- When determining bandwidth requirements is to double the streaming bitrates. While this is not a mandatory requirement, it will help mitigate the impact of network congestion.
- When using software-based encoders, close any unnecessary programs.
- Don't change your encoder configuration after it has started pushing. It has negative effects on the event and can cause the event to be unstable. If you want to do this before the event has started, you must disconnect using the producer controls in Teams and start setup again.
- If the encoder is disconnected during the live event, reconnect it keeping the same timestamps of continuing process. Any discontinuity may cause audio or video issues on certain browsers and devices.
- Give yourself ample time to setup your event. For high scale events, it's recommended to start the setup an hour before your event.
