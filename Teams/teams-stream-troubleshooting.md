---
title: Troubleshooting live streaming in Microsoft Teams
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
description: This article will discuss troubleshooting options for Microsoft Teams streaming events.
localization_priority: Normal
appliesto: 
  - Microsoft Teams
ms.custom:
---

# Troubleshooting live events in Microsoft Teams

> [!IMPORTANT]
> **China**: Users located in China will not be able to set up or attend Teams or Yammer live events or view videos on-demand because currently, Azure CDN, which these apps rely on, might not be accessible in China.
>
> As an administrator, you might need to set up a VPN to connect your corporate network for these apps to work seamlessly. Once that's complete, people in your organization can schedule and attend live events.

## Before a live event

### Make sure all events are reachable in your network

#### General Teams endpoints

Teams requires connectivity to the internet. All endpoints listed on [Office 365 endpoints for Teams](https://support.office.com/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) need to be reachable by users of Teams within your organization's network.

#### External app or device produced live events (formerly external encoder) - RMTP ingest endpoints

To get a video feed for an **External app or device** produced live event sent to Teams from your encoder, you'll need the following IP ranges and ports open in your network's firewall:

- Domains: *.channel.media.azure.net
- Ports: 1935/2935/1936/2936 (for RTMP and RTMPS)

If your specific network setup doesn't allow you to (or you don't want to) open up the domain range above, currently the only option to get specific IP addresses for the RTMP/RTMPS ingest is to get the rotating IP ranges for the Azure data center that your Teams tenant is connected to.

The following JSON files are updated as the IP addresses for Azure data centers change, broken own by region and by the tagged services:

- Public: [https://www.microsoft.com/download/details.aspx?id=56519](https://www.microsoft.com/download/details.aspx?id=56519)
- US Gov: [https://www.microsoft.com/download/details.aspx?id=57063](https://www.microsoft.com/download/details.aspx?id=57063)
- Germany: [https://www.microsoft.com/download/details.aspx?id=57064](https://www.microsoft.com/download/details.aspx?id=57064)
- China: [https://www.microsoft.com/download/details.aspx?id=57062](https://www.microsoft.com/download/details.aspx?id=57062)

> [!NOTE]
> These files are updated weekly and include versioning both for the full file and each individual service tag in that file.

To find the Azure data center for your Teams tenant:

1. In Teams, XXX.
1. Select XXX.
1. XXX.

After you find out the Azure data center for your Teams tenant, find the corresponding IP ranges in the XML file above, and then update your firewall/proxy with the specific IP ranges for your data center. As the XML file changes you'll need to update your firewall/proxy settings as well.

For example:

- If XXX says that your data is stored in "East US 2"
- In the XML file, you would look for a node labeled <Region Name="useast2">
- Under that Region node, there would be several entries for all the IP ranges (<IpRange Subnet="13.68.0.0/17">)
- You would need to configure your firewall\proxy to allow all of these IP ranges and change them on a regular basis when the XML file changes.

Users in the community have written code that on a schedule it takes the XML file above and converts the data into an API that can be queried. Your organization may be able to learn from what was done with this open source project and build your own similar solution to regularly update your firewall/proxy settings.

- Example: http://iprange.omartin2010.com/
- Source code on GitHub: [https://github.com/omartin2010/AzureRange](https://github.com/omartin2010/AzureRange)

### Make sure you have enough upload bandwidth

When producing or streaming a live event via RTMP, it’s possible that the internet upload bandwidth at the site pushing the live stream might not be enough. Low upload bandwidth might result in dropped frames or issues in the live video itself, which may result in playback issues for viewers.

Make sure that your upload speed for the machine and network pushing the live stream is higher than the bitrate you set for the live stream. If you are outputting a 5 Mbps stream from your encoder but your upload bitrate is close to or lower than that, you could run into problems not being able to upload your stream fast enough.

If you have upload bandwidth issues, here are a few things you can try:

1. Use a hard-wired ethernet connection for any machine you are pushing the stream from to avoid any drops in WiFi.
1. Lower the encoding bitrate of your live feed to a value well below your max upload speed.

### Preparing your network for many concurrent viewers

During live events many people will be joining to watch your event live. This could put a strain on your network and internet download bandwidth. You need to assess your current network infrastructure and ensure that people within your corporate network will have the bandwidth needed to watch a live event. To help reduce internet traffic needed for live events there are two options:

1. Configure existing cache proxies within your network to cache videos from Teams.
1. Use a third-party eCDN video delivery solution to optimize video traffic.

### I can't create a live event

There are permissions across Microsoft Teams and Yammer that a user needs to be able to create a live event depending on which service you are using for the live event.

1. Check that the Teams admin has enabled you to create live events.
1. Check with your administrator that you have a valid Teams license that allows the creation of live events.

### Microsoft 365

- You can only create live events from Yammer groups that are M365 group connected. If you have a Yammer group that's not connected to an M365 group, you won't be able to use live events in that group.
- The user needs to be an admin of the Yammer group.
- [The user needs to be enabled for "live event scheduling" in Teams](teams-live-events/what-are-teams-live-events.md).
- If the user is going to create "external app or device" events they need to have permission to create live events in Teams.
- Ensure you have a valid M365 license that allows the creation of live events in M365.

### How do I get my live event to show up in Microsoft Teams?

If you want your event to show up in Microsoft Teams you can create your event from either Yammer or Microsoft Teams. See feature comparison by service and event type for more information.

### Make sure viewers have permission to watch the event

#### Yammer

If your Yammer group is public to the organization then you won't need to worry about permissions for the live event. Everyone in the organization will be able to watch the live event.

If your Yammer group is private, then you'll need to make sure that everyone who needs to watch the live event is a member of your Yammer group. Make sure that you have someone on hand before and during the event to approve member requests. It can be common for people to not be part of the Yammer group but realize they need access to watch the live event.

#### Teams

Live events from Microsoft Teams have a few different roles for permissions on the event itself (Organizer, Producer, Presenter, Attendee).

See [Microsoft Teams event group roles](https://support.office.com/article/microsoft-teams-live-events-overview-d077fec2-a058-483e-9ab5-1494afda578a#bkmk_roles) for more information.

## Producing a live event

### I don't know how to set up my encoder

The easiest way to get started is to follow the instructions outlined from the [Using an encoder for live streaming in Microsoft Teams](teams-stream-setup.md) article.

### My encoder isn't connecting to the server ingest URL

- Check that you've selected **Start setup** on the producer page and waited until you're in the pre-live state. You'll only be able to push from your encoder after the setup is ready to receive.
- Check that the RTMP URL is correctly entered as the output of your encoder.
- If a stream key is required for your encoder, you can fill this in with any string, for example "stream".
- Check the status of your internet connection to ensure that your encoder is correctly connected and online.
- You may have network security or firewall-related settings that may be blocking the output of your connection.
- Your encoder may not be supported with Teams. Check out the list of tested encoders in [Using an encoder for live streaming in Microsoft Teams](teams-stream-setup.md).

### I can't get RTMPs to work

- Some encoders may support a different implementation that is not supported by Teams. Check out the list of tested encoders that work with Teams in [Using an encoder for live streaming in Microsoft Teams](teams-stream-setup.md).
- Not all encoders or versions support RTMPs. Check with the manufacturer or software creator to see what they support.

### I tried to start setup and it's taking a long time

In general, it can take a few minutes to get the setup going before you can start pushing your encoder. It is possible if the service is busy that this can take longer to get going, so it's recommended that you give yourself ample time to start the setup before your scheduled live event.

### I tried to start setup but there are too many events happening

If the maximum number of concurrent active events is reached, a Teams admin has the ability to stop other events to make room for a higher priority event.

### I can't see producer view

1. It may take around thirty seconds for the producer preview to appear after you've started streaming from your encoder.
1. Make sure that that the encoder is connected to Teams.
1. It can sometimes help to refresh the page in Teams. You may be asked if you want to leave the page; this will not affect your live event.
1. Some networks may block access to content. Ensure that your network security and firewall settings allow the RTMP protocol and the [required domains](https://learn.microsoft.com/microsoft-365/enterprise/urls-and-ip-address-ranges) are in the allowed list. It can help to try to see if it works on a different network environment, independent from a corporate network, VPN, or locked-down network.

### My feed looks bad, has poor quality, or is glitchy

1. Check your upload bandwidth from the machine you're pushing the live stream from. Low bandwidth can cause dropped frames, poor quality, or a glitchy looking video stream. You need an upload bandwidth that is higher than the bitrate you're streaming at.
1. Ensure that you're using the recommended encoder settings for Teams. See [Manually configure encoders for live event streaming in Microsoft Teams](teams-stream-configuration.md) for more info.
1. Check that the audio/video coming into the encoder doesn't have any issues. The source audio or video feeds routed to the encoder could have issues itself, which would result in a bad experience sent out to viewers.
1. Check the CPU load on your encoder. You may be maxing out your CPU with the source content and/or with the bitrate you are trying to push. If the CPU load is too high, try reducing the complexity of your live feed overlays/content or reduce the bitrate you are streaming at.
1. Ensure that your encoder is up to date. If it's a hardware encoder, ensure you have the latest firmware updates. If it's a software encoder, make sure you are running the latest version.
1. Try resetting or restarting your encoder. Note that if you do this during a live stream your viewers will see an error during playback while your encoder is restarting. After you restart live streaming from the encoder, viewers will have to reload the page to get the live stream again.

### I started my live event, but didn't connect my encoders

If you started your event and the encoder isn't connected, you and your viewers may have a bad viewing experience. Ensure that your encoder is connected and the preview is coming through before your start your live event.

### I ended my live event from my encoder, but viewers are seeing an error

Select **Stop event** before disconnecting your encoder. If you've already disconnected your encoder, you can still select **Stop event**, but viewers may see an error.

### My viewers are seeing issues

- If a single viewer is reporting an issue, ensure that viewer has enough bandwidth and is on a good internet connection to watch the event.
- If multiple people within the same network are having issues, you may be experiencing network congestion related issues. Review [Scale video delivery and monitor network traffic by using eCDNs with Microsoft Teams](teams-stream-ecdn.md) to see if you can identify a solution to your issue.
- Many times, when multiple viewers are seeing an issue, it actually related to the encoder feed.
  - Check that the encoder is properly set to the specifications outlined in the encoder setup, and configured correctly.
  - Ensure that you have enough upload bandwidth to stream. You can try reducing the bandwidth from the encoder output.
  - Sometimes resetting the encoder helps, but note that you must maintain the same settings when reconnected. Audience members may see an error or glitch in the live event.

For other common playback errors when viewing the preview, or to find out how to report an issue, see XXX.

### I, or my viewers, can't hear the video

1. Check that the encoder is sending audio.
1. Check that the audio device is plugged in.
1. If on Windows, make sure the correct audio device is selected and unmuted.
1. If there was an encoder disruption, some browsers or devices may not be able to recover and playback the audio correctly.
1. If you you select **As soon as encoder is set up**, then navigate back to the producer page, you might see the warning message, "Your scheduled time has passed". You can ignore it.

## Common live event error codes

|Errors ending in:                  |Potential causes: |
|-----------------------------------|------------------|
|0200194                            |1) If you haven't connected your encoder, but have started the live event, you may experience this error. Check your encoder to make sure it's properly connected. 2) If your encoder is connected, it is possible that you're experiencing poor streaming quality generally caused by low upload bandwidth or high CPU usage from the encoder, causing packet loss. Check the encoder to lower the output bandwidth. 3) It's possible that this is a transient network issue. Try refreshing the producer page to see if the issue fixes. 4) The content may be deleted in another window, app or tab. Try refreshing the producer page to see if the event was removed. |
|020019c, 0400005                   |1) Check that your encoder is connected. 2) You may have stopped streaming from your encoder, but forgot to end the event. Select Stop event from the producer page. 3) Check your encoder to ensure you are using the recommended settings. Check to make sure that the you are sending two-second fragment chunks (sometimes known as key frames or GOP boundaries) that are key frame aligned. |
|02001f4, 02001f6, 02001f7, 02001f8 |There is something wrong with the service. This may be transient. Try refreshing the page. |
|0200258                            |This error typically happens when either the internet connection is limited, or there's a transient network issue. Check these settings and try refreshing the page. |
|0200259                            |This error typically happens when either the internet connection is limited, or the ingest endpoint is blocked by a firewall setting. Check these settings and try refreshing the page. |
|0300000                            |Something went wrong trying to playback the video in this browser on your system. Sometimes, this happens if you remove or disable the audio device, minimize the playback in iOS, or run out of memory. Trying in another browser may help the situation. |
|0400000, 0400002, 0400003          |The feed is neither supported by the service nor the browser that you're viewing on. Check that your encoder is sending both an audio and video stream of the required codecs or try a different browser. Learn more about encoder settings. |
|0500004, 0500005, 0400003          |These are sometimes transient errors. Try refreshing to fix the issue. |
|0600001                            |Your browser requires Flash to playback content. Either Flash is not enabled, or the version of Flash is not currently supported. Note that Flash v30 is not current supported. |

XXX SHOULD WE REMOVE MENTIONS OF FLASH

## Other live event error messages

|Message  |Explanation  |
|---------|---------|
|Another operation is modifying the live ingest.          |The requested action can't be completed because another action is currently in progress. Try the requested action again later. |
|Another operation is already running on the live ingest. |The requested action can't be completed because another action is currently in progress. Try the requested action again later. |
|Live ingest cannot be stopped as it is not running.      |The event's already stopped. This can happen if the event has already been automatically shut down from the service or if it's in a bad state. Refreshing the producer page may help to reflect the correct state. |
|The video could not be found.                            |The video can't be found to complete the action on. It's possible that the video's been deleted. |
|Cannot start the live event if the video is deleted.     |The video's been deleted. |
|Looks like your encoder may not be connected. Starting your event when the encoder isn’t connected can result in a bad viewing experience. |The system isn't able to properly detect if your encoder is correctly connected to Teams. If you choose to start your event at this point and your encoder isn't correctly connected, your viewers will experience an error. Use caution and ensure your encoder is connected before starting your event. |
|Sorry, we can’t start your setup. Looks like your organization is using the maximum allowable active events right now. |If the maximum number of concurrent active events is reached, a Teams admin has the ability to stop other events to make room for a higher priority event. |
