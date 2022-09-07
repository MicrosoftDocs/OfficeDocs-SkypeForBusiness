---
title: Encoder configuration for streaming in Microsoft Teams
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
description: This article will discuss encoder-based RTMP configuration for Microsoft Teams streaming events.
localization_priority: Normal
appliesto: 
  - Microsoft Teams
ms.custom:
---

# Manually configure encoders for live event streaming in Microsoft Stream

If you have an encoder that's not directly integrated into Teams, learn how to setup and configure the encoder manually for Live streaming with Teams.

Teams accepts live feeds from a variety of different encoders that output RTMP or RTMPS. Each encoder is different, so make sure to follow the guidelines for the encoder configurations when sending to Teams. Check out the list of tested encoders with easy setup to get started.

To learn how to set up a Live event in Teams, read about creating live events. If you're already using an encoder that's integrated with Teams, read about [configuring encoders for live streaming](teams-encoder-setup.md).

## Configure manually

After you save the live event (read Creating live events for details), you can see the list of integrated encoders in the **Select encoder** drop-down list on the **Encoder setup** tab. The ingest URLs are also generated at this time. Select **Configure manually** to set up an encoder if it's not in the list of integrated encoders.

## Setup

1. Select Start setup to create an ingest channel for live streaming. Wait for the setup to be complete. You will see a **Ready to connect** message on the screen.
1. Copy and paste the following settings into the encoder of your choice:
    1. **Server ingest URL**: In your encoder, this may be called URL or Address. Teams doesn't require a stream key or name, so you can fill this in with any non-empty value, such as TeamStream.
    2. **Secondary server ingest URL**: If supported by your encoder, use this URL to double push to improve durability and resiliency. Since this is outputting a redundant stream from your encoder, it will require double bandwidth. So, make sure that you have the required bandwidth capacity to support this. This is listed under the advanced section.
    3. Use the **Secure Connection (SSL)** toggle to switch between RMTP or RTMPS protocols for the ingest URLs. Your encoder must support RTMPS to use it here.
1. Teams doesn't require a stream key or name, so you can fill this in with any non-empty value such as, TeamsStream. Depending on the encoder, this may be entered on a separate field or appended to the end of the ingest URL, for example, /TeamsStream.
1. Make sure your encoder's configured with the correct settings as per our recommended encoder settings below.
1. Configure your encoder with the desired audio and video sources.
1. Start streaming from your encoder to the Teams ingest endpoints.
1. Go back to Teams. After you're able to see the preview from the encoder, select Start event to go live so your audience can see the live event.

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
- Pixel Aspect Ratio (PAR): Square

### Audio format

- Codec: AAC (LC)
- Bitrate: 192 kbps
- Sample Rate: 48 kHz or 44.1 kHz (recommend 48 kHz)

### Playback requirements

- Both an audio and video stream must be present in order to playback content in Microsoft Stream.

### Configuration tips

- Whenever possible, use a hardwired internet connection.
- When determining bandwidth requirements is to double the streaming bitrates. While this is not a mandatory requirement, it will help mitigate the impact of network congestion.
- When using software-based encoders, close any unnecessary programs.
- Don't change your encoder configuration after it has started pushing. It has negative effects on the event and can cause the event to be unstable. If you want to do this before the event has started, you must disconnect using the producer controls in Microsoft Stream (Classic) and start setup again.
- If the encoder is disconnected during the live event, reconnect it keeping the same timestamps of continuing process. Any discontinuity may cause audio or video issues on certain browsers and devices.
- Give yourself ample time to setup your event. For high scale events, it's recommended to start the setup an hour before your event.
