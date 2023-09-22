---
title: Encoder setup for streaming in Microsoft Teams
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
ms.date: 08/25/2022
search.appverid: MET150
f1.keywords:
- NOCSH
description: This article will discuss encoder-based RTMP setup for Microsoft Teams streaming events.
localization_priority: Normal
appliesto: 
  - Microsoft Teams
ms.custom:
---

# Using an encoder for live streaming with Microsoft Teams

Video encoders allow users to produce Microsoft Teams live events via external hardware or software-based solutions.

## Overview

An encoder takes audio and video content from various sources you use during a live event such as a camera, a microphone, a desktop screen capture, and so on. It compresses and converts that media into a suitable digital format, then sends it to Teams for live streaming to your audience. Consult our [Custom Production playbook](https://aka.ms/CustomProductionVEP) to learn more about how you can use Teams production technologies (such as NDI) with external encoders.

## Production workflow when using an encoder

The workflow for producing a Teams Live Event is as follows:

A live event is scheduled in Teams or Viva Engage, and the **Teams Encoder** option is selected. This provisions an RTMP endpoint, which is provided with an RTMP(S) URL and corresponding stream key. The URL and stream key are used by the encoder to connect to the RTMP endpoint for the scheduled live event.

### Common video encoders used for live streaming

The video encoders in the following list have been validated by Microsoft for live streaming with Teams. 

### Supported encoders

|Encoder                                |Website  |Encoder Type|Native Caption Support|
|---------------------------------------|---------|---------|---------|
|AJA HELO Plus                          |[AJA HELO Plus](https://www.aja.com/products/helo-plus) |Advanced H.264 Streaming and Recording |✔️|
|AWS Elemental Live                     |[AWS Elemental Live](https://aws.amazon.com/elemental-live/) |Encode live on-premises video for events and 24/7 streams ||
|Blackmagic Web Presenter HD            |[Blackmagic Web Presenter](https://www.blackmagicdesign.com/products/blackmagicwebpresenter) |Live stream from any 12G-SDI video source direct to YouTube, Facebook, Twitter and more ||
|Blackmagic ATEM Mini with streaming engine               |[Blackmagic ATEM Mini with streaming engine](https://www.blackmagicdesign.com/products/atemmini) |Introducing low cost, multi camera, live production with advanced broadcast features||
|BrandLive                              |[BrandLive](https://www.brandlive.com/) |Cloud based production platform||
|Epiphan video Pearl Mini               |[Epiphan video Pearl Mini](https://www.epiphan.com/products/pearl-mini/) |Simplify video for everyone on campus ||
|FFmpeg                                 |[FFmpeg](https://ffmpeg.org/) |Open-source suite of software for handling video, audio, and other multimedia files and live streams||
|Haivision                              |[Haivision Makito X4](https://www.haivision.com/microsoft/stream) |Delivers high-quality HD video with Haivision Hub, a powerful alternative to RTMP||
|Live Arena AI Producer                 |[Live Arena AI Producer](https://www.livearena.com/) |Production studio integrated in Microsoft Teams as a meeting app||
|Magewell Ultra Encode AIO              |[Magewell Ultra Encode AIO](https://www.magewell.com/ultra-encode-aio) |Ultra Encode AIO live media encoders take the capabilities of our original Ultra Encode models to a whole new level for advanced use cases ||
|Newtek TriCaster 2 Elite               |[Newtek TriCaster 2 Elite](https://www.vizrt.com/products/tricaster/tricaster-2-elite/) |The TriCaster® 2 Elite is the most complete video production platform available today, and sets a new platinum standard for how much you can achieve with a single system||
|Open Broadcaster Software (OBS Studio) |[Open Broadcaster Software](https://obsproject.com/) |High-performance real-time video/audio capturing and mixing—supporting all streaming platforms, and more||
|Socialive                              |[Socialive](https://socialive.us/) |Cloud video production platform, providing an all-in-one experience for producing and distributing studio-quality video content||
|StreamYard                             |[StreamYard](https://streamyard.com/) |Live streaming studio in a browser||
|Telestream Wirecast                    |[Telestream Wirecast](https://www.telestream.net/wirecast/overview.htm) |Professional live streaming software for everyone||
|Teradek Prism Flex                     |[Teradek Prism Flex](https://teradek.com/pages/prism) |Prism Flex gives you ultra-low latency, 4K HDR streaming in a low-SWaP form factor that fits seamlessly into any video workflow ||
|vMix                                   |[vMix](https://www.vmix.com/) |Software vision mixer that controls recording, mixing, and live streaming of cameras, videos, audio, and more||
|XSplit Broadcaster                     |[XSplit Broadcaster](https://www.xsplit.com/) |Produces, mixes, and delivers rich video content, including gameplay for live streaming||

### Event Setup

- For Microsoft Teams live event creation steps, refer to [this page](/microsoftteams/teams-stream-create-event) 
- For encoder configuration setup, refer to [this guide](/microsoftteams/teams-encoder-configuration)







