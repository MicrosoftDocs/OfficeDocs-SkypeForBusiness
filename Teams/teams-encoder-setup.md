---
title: Encoder setup for streaming in Microsoft Teams
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
description: This article will discuss encoder-based RTMP setup for Microsoft Teams streaming events.
localization_priority: Normal
appliesto: 
  - Microsoft Teams
ms.custom:
---

# Using an encoder for live streaming in Microsoft Teams

To start live streaming a large event using Microsoft Teams, you need an encoder. An encoder (sometimes called a live streaming or media encoder) can be either software or hardware that's used together with recording equipment when live streaming content to a large group of viewers.

## Overview

An encoder takes audio and video content from various sources you use during a live event such as a camera, a microphone, a desktop screen capture, and so on. It compresses and converts that media into a suitable digital format, then sends it to Teams for live streaming to your audience.

## How to choose an encoder

If you're not sure if your software or hardware encoder will work seamlessly with Teams, read on to see which ones we've already tested that work best.

> [!TIP]
> We recommend you select and set up an encoder well before you begin your live event.

### List of encoders tested by Microsoft

The encoders in the following two lists have been tested by Microsoft for live streaming with Teams. The first list is a subset of these encoders, which have been tested with the product for ease of use and quick setup.

#### Stream-ready encoders

TABLETABLETABLE XXX

#### Additional encoders

TABLETABLETABLE XXX

##### Our encoder is not on either list

Not a problem! Sometimes your team or organization has a designated encoder they want you to use and you want to ensure it's ready to stream live with Teams. If so, you can learn how to manually configure your own encoder to stream live events to Teams.

## Set up a Teams-ready encoder

XXX After you schedule your live event you can see the list of available encoders in the **Select encoder drop-down** list on the **Encoder setup** tab.

Each encoder mentioned in the respective tables above has a slightly different setup described below.

### Haivision Makito X Encoder and Makito KB Encoder

If you have an existing Haivision X or Makito KB encoder, you can choose the appropriate option from the drop-down list and follow the list of instructions.

1. Select **Start setup** to create a channel for live streaming. Wait for the setup to complete. You'll see a **Ready to connect** message on the screen.
1. After that's complete, download the preset that contains all of the encoding parameters including the ingest URL and event name. Import the preset into the encoder and start the encoder.
1. Go back to Teams. After you are able to see the preview from the encoder, select **Start event** to go live so your audience can see the live event.

> [!NOTE]
> Haivision KB Encoder support for RTMPS has not been tested yet. Haivision Makito X Encoder does not support RTMPS. The downloaded presets for both encoders contain the RTMP ingest URL.

### Switcher Studio

You can use Switcher Studio to start streaming to Teams using iPhone or iPad.

1. Select **Start setup** to create a channel for live streaming. Wait for the setup to complete. You'll see a **Ready to connect** message on the screen.
2. Switcher Studio will open the Switcher Studio dashboard to add the live event to your account.

> [!NOTE]
> If you don't already have a Switcher Studio account, you'll need to create one).

3. When this is complete, you can go to your Switcher Studio app on your iPhone or iPad, select Teams in the Output tab and start streaming to Teams.
4. Go back to Teams. After you're able to see the preview from the encoder, select **Start event** to go live so your audience can see the live event.

> [!NOTE]
> Switcher Studio uses the RTMP ingest URL.

### Wirecast

If you're an existing user of Wirecast, you can choose this option from the drop-down list to send a live stream to Teams. Note that you'll need Wirecast version 10 or later.

1. Select **Start setup** to create a channel for live streaming. Wait for the setup to complete. You'll see a **Ready to connect** message on the screen.
1. The encoder will launch the Wirecast app on your machine pre-configured with the correct encoding parameters and ingest URL for that live event. When ready click the Teams icon in the Wirecast app to start streaming to Teams.
1. Go back to Teams. After you're able to see the preview from the encoder, select **Start event** to go live so your audience can see the live event.

> [!NOTE]
> The Wirecast app is launched with the RTMPS ingest URL pre-configured.

### Wirecast S

If you're new to streaming, you can try Wirecast S by choosing it from the drop-down list. Wirecast S is built specifically for Teams.

1. Select **Start setup** to create a channel for live streaming. Wait for the setup to complete. You'll see a **Ready to connect** message on the screen.
1. The encoder will launch the Wirecast S app on your machine pre-configured with the correct encoding parameters and ingest URL for that live event. You can choose to automatically start streaming to Teams by selecting that option in the Wirecast S setup screen.
1. Go back to Teams. After you're able to see the preview from the encoder, select **Start event** to go live so your audience can see the live event.

> [!NOTE]
> The Wirecast S app is launched with the RTMPS ingest URL pre-configured.
