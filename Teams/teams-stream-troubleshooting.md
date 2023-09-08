---
title: Troubleshooting live streaming in Microsoft Teams
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
ms.date: 10/03/2022
search.appverid: MET150
f1.keywords:
- NOCSH
description: This article will discuss troubleshooting options for Microsoft Teams streaming events.
localization_priority: medium
appliesto: 
  - Microsoft Teams
ms.custom:
---

# Troubleshooting live events in Microsoft Teams

> [!NOTE]
> Teams live events will be deprecated on September 30, 2024. We recommend that you use town halls instead. For details, see [Plan for Teams town halls](/microsoftteams/plan-town-halls).

> [!IMPORTANT]
> **China**: Users located in China won't be able to set up or attend Teams or Viva Engage live events or view videos on-demand because currently, Azure CDN, which these apps rely on, might not be accessible in China.
>
> As an administrator, you might need to set up a VPN to connect your corporate network for these apps to work seamlessly. Once that's complete, people in your organization can schedule and attend live events.

## Before a live event

### Make sure all events are reachable in your network

#### General Teams endpoints

Teams requires connectivity to the internet. All endpoints listed on [Office 365 endpoints for Teams](https://support.office.com/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) need to be reachable by users of Teams within your organization's network.

#### Teams Encoder live events - RMTP ingest endpoints

To get a video feed for a Teams Encoder live event sent to Teams from your encoder, you'll need the domain name and ports open in your network's firewall:

- Domains: *.rtmpingest.mcr.teams.microsoft.com
- Ports: 1935/1936 (for RTMP/RTMPS)

### Make sure you have enough upload bandwidth

When producing or streaming a live event via RTMP, it’s possible that the internet upload bandwidth at the site pushing the live stream might not be enough. Low upload bandwidth might result in dropped frames or issues in the live video itself, which may result in playback issues for viewers.

Make sure that your upload speed for the machine and network pushing the live stream is higher than the bitrate you set for the live stream. If you're outputting a 5 Mbps stream from your encoder but your upload bitrate is close to or lower than that, you could run into problems not being able to upload your stream fast enough.

If you have upload bandwidth issues, here are a few things you can try:

1. Use a hard-wired ethernet connection for any machine you're pushing the stream from to avoid any drops in WiFi.
1. Lower the encoding bitrate of your live feed to a value well below your max upload speed.

### Preparing your network for many concurrent viewers

During live events many people will be joining to watch your event live. This could put a strain on your network and internet download bandwidth. You need to assess your current network infrastructure and ensure that people within your corporate network will have the bandwidth needed to watch a live event. To help reduce internet traffic needed for live events there are two options:

1. Configure existing cache proxies within your network to cache videos from Teams.
1. Use a third-party eCDN video delivery solution to optimize video traffic.

Viewers receive the Teams live event stream via TCP HTTPS. The following URLs should bypass any proxy servers within your environment, and have SSL inspection disabled:

 - *.media.azure.net
 - bmc.cdn.office.net

### I can't create a live event

There are permissions across Microsoft Teams and Viva Engage that a user needs to be able to create a live event depending on which service you're using for the live event.

1. Check that the Teams admin has enabled you to create live events.
2. Check with your administrator that you have a valid Teams license that allows the creation of live events.
3. Select the following **Run Tests**, which will populate the diagnostic in Microsoft 365 admin center to help you validate if a user is able to schedule Teams live events.

   > [!div class="nextstepaction"]
   > [Run Tests: Schedule Teams live events](https://aka.ms/TeamsLiveEventsDiag)

### Make sure viewers have permission to watch the event

Microsoft Teams live events have a few different roles for permissions on the event itself (Organizer, Producer, Presenter, Attendee).

See [Microsoft Teams event group roles](https://support.office.com/article/microsoft-teams-live-events-overview-d077fec2-a058-483e-9ab5-1494afda578a#bkmk_roles) for more information.

## Producing a live event

### I don't know how to set up my encoder

The easiest way to get started is to follow the instructions outlined from the [Using an encoder for live streaming in Microsoft Teams](teams-encoder-setup.md) article.

### My encoder isn't connecting to the server ingest URL

- Check that the RTMP URL is correctly entered as the output of your encoder.
- Check that the RTMP Key is correctly entered as the output of your encoder.
- Check the status of your internet connection to ensure that your encoder is correctly connected and online.
- You may have network security or firewall-related settings that may be blocking the output of your connection.
- Your encoder may not be supported with Teams. Check out the list of tested encoders in [Using an encoder for live streaming in Microsoft Teams](teams-encoder-setup.md).

### I can't get RTMPs to work

- Some encoders may support a different implementation that isn't supported by Teams. Check out the list of tested encoders that work with Teams in [Using an encoder for live streaming in Microsoft Teams](teams-encoder-setup.md).
- Not all encoders or versions support RTMPs. Check with the manufacturer or software creator to see what they support.

### I tried to start setup and it's taking a long time

In general, it can take a few minutes to get the setup going before you can start pushing your encoder. It is possible if the service is busy that this can take longer to get going, so it's recommended that you give yourself ample time to start the setup before your scheduled live event.

### I tried to start setup but there are too many events happening

If you receive a message when starting an event that the maximum number of events has been reached, reach out to a Teams admin, who has the ability to stop other events to make room for a higher priority event.

### I can't see producer view

1. It may take a few seconds for the producer preview to appear after you've started streaming from your encoder.
1. Make sure that the encoder is connected to Teams.
1. It can sometimes help to refresh the page in Teams. You may be asked if you want to leave the page; this won't affect your live event.
1. Some networks may block access to content. Ensure that your network security and firewall settings allow the RTMP protocol and the [required domains](/microsoft-365/enterprise/urls-and-ip-address-ranges) are in the allowed list. It can help to try to see if it works on a different network environment, independent from a corporate network, VPN, or locked-down network.

### My feed looks bad, has poor quality, or is glitchy

1. Check your upload bandwidth from the machine you're pushing the live stream from. Low bandwidth can cause dropped frames, poor quality, or a glitchy looking video stream. You need an upload bandwidth that is higher than the bitrate you're streaming at.
1. Make sure you're using the recommended encoder settings for Teams. See [Manually configure encoders for live event streaming in Microsoft Teams](teams-encoder-configuration.md) for more info.
1. Check that the audio/video coming into the encoder doesn't have any issues. The source audio or video feeds routed to the encoder could have issues itself, which would result in a bad experience sent out to viewers.
1. Check the CPU load on your encoder. You may be maxing out your CPU with the source content and/or with the bitrate you're trying to push. If the CPU load is too high, try reducing the complexity of your live feed overlays/content or reduce the bitrate you're streaming at.
1. Make sure your encoder is up to date. If it's a hardware encoder, ensure you have the latest firmware updates. If it's a software encoder, make sure you're running the latest version.
1. Try resetting or restarting your encoder. Note that if you do this during a live stream your viewers will see an error during playback while your encoder is restarting. After you restart live streaming from the encoder, viewers will have to reload the page to get the live stream again.

### I ended my live event from my encoder, but viewers are seeing an error

Select **Stop event** before disconnecting your encoder. If you've already disconnected your encoder, you can still select **Stop event**, but viewers may see an error.

### My viewers are seeing issues

- If a single viewer is reporting an issue, ensure that viewer has enough bandwidth and is on a good internet connection to watch the event.
- If multiple people within the same network are having issues, you may be experiencing network congestion related issues. Review [Scale video delivery and monitor network traffic by using eCDNs with Microsoft Teams](teams-stream-ecdn.md) to see if you can identify a solution to your issue.
- Many times, when multiple viewers are seeing an issue, it actually related to the encoder feed.
  - Check that the encoder is properly set to the specifications outlined in the encoder setup, and configured correctly.
  - Ensure that you have enough upload bandwidth to stream. You can try reducing the bandwidth from the encoder output.
  - Sometimes resetting the encoder helps, but note that you must maintain the same settings when reconnected. Audience members may see an error or glitch in the live event.

### I, or my viewers, can't hear the video

1. Check that the encoder is sending audio.
1. Check that the audio device is plugged in.
1. If on Windows, make sure the correct audio device is selected and unmuted.
1. If there was an encoder disruption, some browsers or devices may not be able to recover and play back the audio correctly.

> [!NOTE]
> If you've deployed Microsoft eCDN as your video distribution provider for live events, please refer to [Troubleshooting eCDN performance issues](/ecdn/troubleshooting/troubleshoot-ecdn-performance-issues) for more details on troubleshooting the eCDN performance issues you may be experiencing.
