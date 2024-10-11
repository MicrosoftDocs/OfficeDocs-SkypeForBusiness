---
title: Encoder setup for live event streaming in Microsoft Teams
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
description: This article discusses encoder-based RTMP setup for Microsoft Teams streaming events.
ms.localizationpriority: medium
appliesto: 
  - Microsoft Teams
ms.custom:
---


# Using an encoder for live event streaming with Microsoft Teams

> [!NOTE]
> We're currently still supporting live events. While we still recommend you to upgrade to [Teams town halls](plan-town-halls.md) to take advantage of new features and experiences, your users can continue to schedule events. For more information, see [Updates for Town Hall in Microsoft Teams and Teams Live Events](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/extension-for-teams-live-events-retirement/ba-p/4148352).

**APPLIES TO:** ✔️Meetings ✖️Webinars ✔️Town halls ✔️Live events

Video encoders allow users to produce Microsoft Teams live events via external hardware or software-based solutions.

## Overview

An encoder takes audio and video content from various sources you use during a live event such as a camera, a microphone, a desktop screen capture. The encoder compresses and converts that media into a suitable digital format, and sends it to Teams for live streaming to your audience. To learn more about how you can use Teams production technologies (such as NDI) with external encoders, see our [Custom Production playbook](https://aka.ms/CustomProductionVEP).

## Production workflow when using an encoder

Here's the workflow for producing a Teams Live Event:

For a live event scheduled in Teams or Viva Engage, the **Teams Encoder** option must be selected. For a town hall, the **RTMP-In** meeting option must be turned on. This option creates an RTMP endpoint, which is provided with an RTMP(S) URL and corresponding stream key. The URL and stream key are used by the encoder to connect to the RTMP endpoint for the scheduled live event.

### Common video encoders used for live streaming

Microsoft validated the video encoders for live streaming with Teams in the following list:

### Supported encoders

|Encoder                                |Website  |Encoder Type|Native Caption Support|
|---------------------------------------|---------|---------|---------|
|AJA HELO Plus                          |[AJA HELO Plus](https://www.aja.com/products/helo-plus) |Hardware|✔️|
|AWS Elemental Live                     |[AWS Elemental Live](https://aws.amazon.com/elemental-live/) |Hardware|✔️|
|Blackmagic Web Presenter HD            |[Blackmagic Web Presenter](https://www.blackmagicdesign.com/products/blackmagicwebpresenter) |Hardware|✔️|
|Blackmagic ATEM Mini with streaming engine               |[Blackmagic ATEM Mini with streaming engine](https://www.blackmagicdesign.com/products/atemmini) |Hardware||
|BrandLive                              |[BrandLive](https://www.brandlive.com/) |Service||
|Epiphan video Pearl Nano               |[Epiphan video Pearl Nano](https://www.epiphan.com/products/pearl-nano/) |Hardware||
|FFmpeg                                 |[FFmpeg](https://ffmpeg.org/) |Software|✔️|
|Haivision                              |[Haivision Makito X4](https://www.haivision.com/microsoft/stream) |Hardware|✔️|
|Live Arena AI Producer                 |[Live Arena AI Producer](https://www.livearena.com/) |Service||
|Magewell Ultra Encode AIO              |[Magewell Ultra Encode AIO](https://www.magewell.com/ultra-encode-aio) |Hardware|✔️|
|Matrox Monarch EDGE Series             |[Matrox Monarch EDGE Series](https://video.matrox.com/en/products/encoders-decoders/monarch-edge-series) |Hardware|✔️*|
|Newtek TriCaster 2 Elite               |[Newtek TriCaster 2 Elite](https://www.vizrt.com/products/tricaster/tricaster-2-elite/) |Hardware||
|Open Broadcaster Software (OBS Studio) |[Open Broadcaster Software](https://obsproject.com/) |Software||
|Socialive                              |[Socialive](https://socialive.us/) |Service||
|StreamYard                             |[StreamYard](https://streamyard.com/) |Service||
|Telestream Wirecast                    |[Telestream Wirecast](https://www.telestream.net/wirecast/overview.htm) |Software||
|Teradek Prism Flex                     |[Teradek Prism Flex](https://teradek.com/pages/prism) |Hardware|✔️|
|vMix                                   |[vMix](https://www.vmix.com/) |Software||
|XSplit Broadcaster                     |[XSplit Broadcaster](https://www.xsplit.com/) |Software||

*Native caption support coming soon

### Event Setup

- For Microsoft Teams live event creation steps, see [Plan and schedule a live event](https://support.microsoft.com/office/plan-and-schedule-a-live-event-f92363a0-6d98-46d2-bdd9-f2248075e502).
- For encoder configuration setup, see [Configuring encoders for live event streaming in Microsoft Teams](/microsoftteams/teams-encoder-configuration).
