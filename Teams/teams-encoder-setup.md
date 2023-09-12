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

# Using an encoder for live streaming in Microsoft Teams

Teams encoders allow users to produce live events directly from an external hardware or software-based encoder with Microsoft Teams.

## Overview

An encoder takes audio and video content from various sources you use during a live event such as a camera, a microphone, a desktop screen capture, and so on. It compresses and converts that media into a suitable digital format, then sends it to Teams for live streaming to your audience. Consult our [Custom Production playbook](https://aka.ms/CustomProductionVEP) to learn more about how you can use Teams production technologies (such as NDI) with external encoders.

## Production workflow when using an encoder

The workflow for producing a Teams Live Event is as follows:

A live event is scheduled in Teams or Viva Engage, and the **Teams Encoder** option is selected. This provisions an RTMP endpoint, which is provided with an RTMP(S) URL and corresponding key. The URL and key are used by the encoder to connect to the RTMP endpoint for the scheduled live event.

### Common encoders used with live events

The encoders in the following list have been tested by Microsoft for live streaming with Teams. The list is a subset of these encoders, which have been tested with the product for ease of use and quick setup.

### Supported encoders

|Encoder                                |Website  |Details  |
|---------------------------------------|---------|---------|
|AJA HELO Plus                          |[AJA HELO Plus](https://www.aja.com/products/helo-plus) |Advanced H.264 Streaming and Recording |
|AWS Elemental Live                     |[AWS Elemental Live](https://www.elemental.com/products/aws-elemental-appliances-software/#elemental-live) |Real-time video and audio recording for live streaming to internet-connected devices |
|BrandLive                              |[BrandLive](https://www.brandlive.com/) |Cloud based production platform. |
|FFmpeg                                 |[FFmpeg](https://ffmpeg.org/) |Open-source suite of software for handling video, audio, and other multimedia files and live streams. |
|Haivision                              |[Haivision Makito X4](https://www.haivision.com/microsoft/stream) |Delivers high-quality HD video with Haivision Hub, a powerful alternative to RTMP. |
|Live Arena AI Producer                 |AI Producer |Production studio integrated in Microsoft Teams as a meeting app.|
|Open Broadcaster Software (OBS Studio) |[Open Broadcaster Software](https://obsproject.com/) |High-performance real-time video/audio capturing and mixing—supporting all streaming platforms, and more. |
|Production Truck                       |[Production Truck](https://www.blueframetech.com/productiontruck) |Films and streams events on location from a mobile van or truck. |
|Socialive                              |Socialive |Cloud video production platform, providing an all-in-one experience for producing and distributing studio-quality video content.|
|StreamYard                             |StreamYard |Live streaming studio in the browser.|
|Switcher Studio                        |[Switcher Studio](https://www.switcherstudio.com/microsoft-stream) |Syncs multiple Apple devices with one or more cameras for real-time video capture and edit. |
|vMix                                   |[vMix](https://www.vmix.com/) |Software vision mixer that controls recording, mixing, and live streaming of cameras, videos, audio, and more. |
|Wirecast                               |[Wirecast](https://www.telestream.net/wirecast) |Webcasting software that covers all the basics + multi-camera production. |
|XSplit Broadcaster                     |[XSplit Broadcaster](https://www.xsplit.com/) |Produces, mixes, and delivers rich video content, including gameplay for live streaming. |

### Event Setup

- For Microsoft Teams live event creation steps, refer to [this page](/microsoftteams/teams-stream-create-event) 
- For encoder configuration setup, refer to [this guide](/microsoftteams/teams-encoder-configuration)



