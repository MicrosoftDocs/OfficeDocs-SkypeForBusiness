---
title: Encoder setup for streaming in Microsoft Teams events
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
ms.date: 07/01/2023
search.appverid: MET150
f1.keywords:
- NOCSH
description: Learn about encoder-based RTMP setup for Microsoft Teams streaming events.
localization_priority: medium
appliesto: 
  - Microsoft Teams
ms.custom:
---

# Encoder setup for streaming in Microsoft Teams events

**APPLIES TO:** ✔️Meetings ✖️Webinars ✔️Town halls ✔️Live events

Teams encoders allow users to produce Teams streaming events directly from an external hardware or software-based encoder with Microsoft Teams.

An encoder takes audio and video content from various sources you use during a streaming event such as a camera, a microphone, a desktop screen capture, and so on. It compresses and converts that media into a suitable digital format, then sends it to Teams for live streaming to your audience. Consult our [Custom Production playbook](https://aka.ms/CustomProductionVEP) to learn more about how you can use Teams production technologies (such as NDI) with external encoders.

## Production workflow when using an encoder

The workflow for producing a Teams streaming event is as follows:

An event is scheduled in Teams or Viva Engage, and the **Teams Encoder** option is selected. This provisions an RTMP endpoint, which is provided with an RTMP(S) URL and corresponding key. The URL and key are used by the encoder to connect to the RTMP endpoint for the scheduled streaming event.

### Common encoders used with streaming events

The encoders in the following two lists have been tested by Microsoft for live streaming with Teams. The first list is a subset of these encoders, which have been tested with the product for ease of use and quick setup.

#### Stream-ready encoders

|Encoder                                |Website  |Details  |
|---------------------------------------|---------|---------|
|Haivision                              |[Haivision Makito X](https://www.haivision.com/microsoft/stream) |Delivers high-quality HD video with Haivision Hub, a powerful alternative to RTMP. |
|Haivision                              |[Haivision KB](https://www.haivision.com/microsoft/stream) |H.264 and HEV video encoders deliver high-quality ABR video cascades for resolutions up to 4K. |
|Open Broadcaster Software (OBS Studio) |[Open Broadcaster Software](https://obsproject.com/) |High-performance real-time video/audio capturing and mixing—supporting all streaming platforms, and more. |
|vMix                                   |[vMix](https://www.vmix.com/) |Software vision mixer that controls recording, mixing, and live streaming of cameras, videos, audio, and more. |
|Wirecast                               |[Wirecast](https://www.telestream.net/wirecast) |Webcasting software that covers all the basics + multi-camera production. |
|Switcher Studio                        |[Switcher Studio](https://www.switcherstudio.com/microsoft-stream) |Syncs multiple Apple devices with one or more cameras for real-time video capture and edit. |
|AWS Elemental Live                     |[AWS Elemental Live](https://www.elemental.com/products/aws-elemental-appliances-software/#elemental-live) |Real-time video and audio recording for live streaming to internet-connected devices |
|XSplit Broadcaster                     |[XSplit Broadcaster](https://www.xsplit.com/) |Produces, mixes, and delivers rich video content, including gameplay for live streaming. |
|FFmpeg                                 |[FFmpeg](https://ffmpeg.org/) |Open-source suite of software for handling video, audio, and other multimedia files and live streams. |
|Production Truck          |[Production Truck](https://www.blueframetech.com/productiontruck) |Films and streams events on location from a mobile van or truck. |
|Live Arena AI Producer                 |AI Producer |Production studio integrated in Microsoft Teams as a meeting app.|
|StreamYard                             |StreamYard |Live streaming studio in the browser.|
|Socialive                              |Socialive |Cloud video production platform, providing an all-in-one experience for producing and distributing studio-quality video content.|
|Brandlive                              |BrandLive |Cloud based production platform.|

### Haivision Makito X Encoder and Makito KB Encoder

If you have an existing Haivision X or Makito KB encoder, you can choose the appropriate option from the drop-down list and follow the list of instructions.

1. Select **Start setup** to create a channel for live streaming. Wait for the setup to complete. You'll see a **Ready to connect** message on the screen.
1. After that's complete, download the preset that contains all of the encoding parameters including the ingest URL and event name. Import the preset into the encoder and start the encoder.
1. Go back to Teams. After you are able to see the preview from the encoder, select **Start event** to go live so your audience can see the streaming event.

> [!NOTE]
> Haivision KB Encoder support for RTMPS has not been tested yet. Haivision Makito X Encoder does not support RTMPS. The downloaded presets for both encoders contain the RTMP ingest URL.

### Switcher Studio

You can use Switcher Studio to start streaming to Teams using iPhone or iPad.

1. Select **Start setup** to create a channel for live streaming. Wait for the setup to complete. You'll see a **Ready to connect** message on the screen.
2. Switcher Studio will open the Switcher Studio dashboard to add the streaming event to your account.

> [!NOTE]
> If you don't already have a Switcher Studio account, you'll need to create one).

3. When this is complete, you can go to your Switcher Studio app on your iPhone or iPad, select Teams in the Output tab and start streaming to Teams.
4. Go back to Teams. After you're able to see the preview from the encoder, select **Start event** to go live so your audience can see the streaming event.

> [!NOTE]
> Switcher Studio uses the RTMP ingest URL.

### Wirecast

If you're an existing user of Wirecast, you can choose this option from the drop-down list to send a live stream to Teams. Note that you'll need Wirecast version 10 or later.

1. Select **Start setup** to create a channel for live streaming. Wait for the setup to complete. You'll see a **Ready to connect** message on the screen.
1. The encoder will launch the Wirecast app on your machine pre-configured with the correct encoding parameters and ingest URL for that streaming event. When ready click the Teams icon in the Wirecast app to start streaming to Teams.
1. Go back to Teams. After you're able to see the preview from the encoder, select **Start event** to go live so your audience can see the streaming event.

> [!NOTE]
> The Wirecast app is launched with the RTMPS ingest URL pre-configured.
