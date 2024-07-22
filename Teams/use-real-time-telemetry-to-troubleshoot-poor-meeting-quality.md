---
title: Use real-time telemetry to troubleshoot poor meeting quality
author: jacktremper
ms.author: jtremper
manager: pamgreen
ms.reviewer: vapati
ms.date: 06/17/2024
ms.topic: article
ms.assetid: 66945036-ae87-4c08-a0bb-984e50d6b009
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.collection:
  - m365initiative-meetings
  - Tier1
search.appverid: MET150
audience: Admin
appliesto:
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
  - ms.teamsadmincenter.directrouting.callanalytics
  - ms.teamsadmincenter.users.activity.audioqualitycolumn
  - Reporting
description: Use real-time telemetry with details about devices, networks, and connectivity to troubleshoot user problems with Microsoft Teams scheduled meetings.
---

# Use real-time telemetry to troubleshoot poor meeting quality

This article explains how to use Real-Time Analytics (RTA) to troubleshoot poor Microsoft Teams meeting quality for individual users. You can access Real-Time Analytics if you have one of the following roles:

- Teams Administrator
- Teams Communications Support Specialist
- Teams Communications Support Engineer

For more information on Teams admin roles, see [Use Microsoft Teams administrator roles to manage Teams](/MicrosoftTeams/using-admin-roles).

Real-Time Analytics lets IT admins look at their important users’ scheduled meetings and see audio, video, content sharing, and network-related issues. As an admin, you can use this telemetry to investigate these issues during meetings and troubleshoot in real time.

Real-Time Analytics is available in Commercial, GCC, and GCC High.

You can also set up alerts for audio issues as they occur in in-progress meetings. For more information, see [Alerts for in-progress meeting audio quality issues](alerts/alerts-in-progress-meeting-audio.md).

## What is Real-Time Analytics?

Today, individual meeting troubleshooting is available for Teams administrators through [Call Analytics](use-call-analytics-to-troubleshoot-poor-call-quality.md) after the meeting ends. Real-Time Analytics lets admins troubleshoot scheduled meetings while they're in progress.

Real-Time Analytics shows detailed information about Teams meetings for each user in your Microsoft 365 account, updated in real time. It includes information about devices, network, connectivity, audio, video, and content sharing issues, which will help admins troubleshoot call quality more effectively.

As a Teams admin, you get full access to all real-time telemetry data for each user. In addition, you can assign Microsoft Entra roles to support staff. To learn more about these roles, see [Give permission to support and help desk staff](set-up-call-analytics.md#give-permission-to-support-and-helpdesk-staff).

## Where to find per-user real-time troubleshooting telemetry

To see all meeting information and data for a user, go to the [Teams admin center](https://admin.teams.microsoft.com). Under **Users** > **Manage users**, select a user, and open the **Meetings & calls** tab on the user's profile page. Under **Recent meetings**, there is a list of meetings the user attended within the past 24 hours for which real-time telemetry is available, including any in progress meetings. If the meeting isn't in progress or doesn't have real-time telemetry data, it's listed under **Past meetings**.

Real-time telemetry is gathered automatically for all users who have a Teams Premium license and is retained for seven days. For users who don't have a Teams Premium license, real-time telemetry is only gathered when you access the in-progress meeting in the Teams admin center and is retained for 24 hours.

:::image type="content" alt-text="Screenshot of recent meetings table." source="media/recent-meetings.png" lightbox="media/recent-meetings.png":::

To get additional information about participants of a meeting that's in progress, including their device, network, and audio statistics, find the meeting in **Recent meetings** and select the link under the **Participants** column.

:::image type="content" alt-text="Screenshot of participant details table." source="media/participant-details-edit.png" lightbox="media/participant-details-edit.png":::

To look at the telemetry of a given user for an in-progress meeting, including information around device, network, audio, video, and content sharing details, select the **Meeting ID**.

:::image type="content" alt-text="Screenshot of call analytics user session data." source="media/real-time-telemetry-edit.png" lightbox="media/real-time-telemetry-edit.png":::

## Details and measures available in Real-Time Analytics

### Device information
| Name | Description | Possible reasons for blank values|
|:---|:---|:---|
| Audio capture device | Name of the audio capture device (for example, microphone) in use | System might not have a name associated with the device (for example, Remote Desktop or Virtual machine 'Remote audio' device)  |
| Audio render device | Name of the audio render device (for example, speakers or headphones) in use | System might not have a name associated with the device (for example, Remote Desktop or Virtual machine 'Remote audio' device)  |
| Video capture device | Name of the video capture device in use | User isn't sending video from the endpoint being monitored |

### Connectivity information
| Metric | Units / Possible values | Description | Possible reasons for blank values|
|:---|:---|:---|:---|
| Network type | &bull; Ethernet <br/> &bull; Wi-Fi | Type of network connection in use | |
| Wi-Fi strength | &bull; Excellent: -50 dBm or greater <br/> &bull; Good: -51 dBm to -64 dBm<br/> &bull; Poor: -65 dBm or lower | Received signal strength indicator (RSSI) of the user's current Wi-Fi connection measured in decibel-milliwatts | User isn't connected to Wi-Fi |
| Wi-Fi channel | Integer | Channel over which the Wi-Fi network's access point is broadcasting | User isn't connected to Wi-Fi |
| Physical type | String <br/> &bull; Example: 802.11ac | Wireless infrastructure type in use | User isn't connected to Wi-Fi |
| Wi-Fi band | 2.4 GHz or 5 GHz | Wi-Fi band to which the user is connected | User isn't connected to Wi-Fi |
| Location | String | Country/Region in which the user is located | User's location information is blocked or unavailable |
| Local IP address | String (IP:Port) | Local IP address of the user's endpoint and the media port | |
| Server reflexive IP address | String (IP:Port) | Public IP address of the user's endpoint and the media port | |
| Connectivity type | UDP or TCP | Transport layer protocol in use; UDP is preferred for real-time media | |

### User signals
User signals identify when a user is actively participating in the call, isn't speaking but unmuted, or is muted. Currently, user signals are only available for audio.

| Modality | Possible values | Description |
|:---|:---|:---|
| Audio | &bull; Unmuted, participant speaking <br/> &bull; Unmuted, not speaking <br/> &bull; Muted | Indicates the behavior of the user for the audio portion of the call  |


### Audio
|Measure Name |Units |Good Threshold |Description |
|:---|:---|:---|:---|
|Jitter |Milliseconds |Less than 30 ms |Jitter is a measure of the variation in packet delay for a data stream. When jitter is too high, audio can become choppy. Real-Time Analytics displays network inter-arrival jitter, not audio jitter. | 
|Packet Loss |Percentage |Less than 5% |Packet loss occurs when data packets fail to reach their destination. The percentage of packets lost is based on the total number of packets sent. |
|Round Trip Time (RTT) |Milliseconds |Less than 500 ms |Round trip time is the time it takes for a single packet to travel from the client to the remote endpoint and back to the client. High round trip time can cause delays in stream playback. An example of high RTT is when two people in a meeting are unintentionally speaking over each other due to the delay. Shown for outbound audio only. |
|Bitrate |Kilobits per second (Kbps) |Greater than 24 Kbps |Throughput of the audio stream expressed in kilobits per second. |
| Codec | String <br/> &bull; Example: SATIN | Information only | Displays the audio codec being sent and received. A different codec can be received than the one being sent. |
| Local Healed Ratio | Ratio | Less than 0.07 | Indicates when the audio healer is being invoked on the local endpoint for the inbound audio stream. High healer usage is experienced by end-users as "choppy audio".|


### Video
|Measure Name |Units |Good Threshold |Description |
|:---|:---|:---|:---|
|Round Trip Time (RTT) |Milliseconds | Less than 500 ms |Round trip time is the time it takes for a single packet to travel from the client to the remote endpoint and back to the client. High round trip time can cause delays in stream playback. An example of high RTT is when two people in a meeting are unintentionally speaking over each other due to the delay. |
|Bitrate |Megabits per second (Mbps) | Information only |Throughput of the video stream expressed in megabits per second. |
|Frame Rate (Video) |Frames per second |360p or better: 25-30 FPS <br/> 270p or lower: 7-15 FPS |For outbound video streams, frame rate (FPS) is the number of frames per second of video the client is sending. Lower than expected values here may suggest system resource constraints, insufficient network bandwidth, or misbehaving video capture devices. Different resolutions have different acceptable FPS ranges. |
|Codec |String | Information only |Displays the video codec and rendering mode of the outbound video stream. (Example: H264 SW HW indicates an H264 video stream using both software and hardware rendering.)|
|Resolution |Pixels | Information only |The resolution of the video being sent. Outbound video resolution is dynamic, based on the highest requirement from an endpoint in the meeting. A client capable of 1920 x 1080 video will only send 640 x 360 video if no clients are displaying that user's video in a frame larger than 640 x 360 |
| Source Freeze Count | Count | Less than 2 | The number of times the camera didn’t generate a new frame for more than one second at a stretch. For video, this metric is typically indicative of an issue with the device generating content at the asked format. |
| Loss Recovery Attempt Rate | Count | Less than 21 | Indicates the number of times there was a request to recover from network loss causing video to freeze. This value is typically caused by packet loss on the network and can result in short to long freezes depending on the nature of loss. Mitigating the source of network loss should improve quality. |
| Video Encoder Hardware Failure | Boolean | False | This flag indicates that there was an error from the hardware encoding component. Typically, Teams handles video encoder errors by falling back to software encoding, but software encoding can result in degraded performance if the endpoint doesn’t have sufficient processing power. |



### Application Sharing (VBSS)
|Measure Name |Units |Good Threshold |Description |
|:---|:---|:---|:---|
|Packet Loss |Percentage |Less than 5% |Packet loss occurs when data packets fail to reach their destination. The percentage of packets lost is based on the total number of packets sent. |
|Round Trip Time (RTT) |Milliseconds |Less than 500 ms |Round trip time is the time it takes for a single packet to travel from the client to the remote endpoint and back to the client. High round trip time can cause delays in stream playback. An example of high RTT is when two people in a meeting are unintentionally speaking over each other due to the delay. |
|Bitrate |Megabits per second (Mbps) | Information only |Throughput of the VBSS stream expressed in megabits per second. |
|Frame Rate |Frames per second (FPS) | Information only |For VBSS, frame rate is content-aware to ensure as many frames as necessary are sent to ensure a good experience while avoiding sending frames if they're not needed. For example, sharing a text document on-screen only requires one frame-per-second to produce a good experience, whereas sharing a video or content with more activity will increase frames per second to a maximum of 30 FPS to produce a smoother experience. |
|Codec |String | Information only |Displays the codec and rendering mode of the VBSS stream. (Example: H264 SW HW indicates an H264 VBSS stream using both software and hardware rendering.)|
|Resolution |Pixels | Information only |The resolution of the VBSS stream being sent and received. |
| Normalized Freeze Duration | Milliseconds per minute| Less than 25 | This metric is the rate of video freezing that is observed on the receiver side and is represented in milliseconds of freeze per minute of active video. Loss-free networks should have a value of 0. Video freeze is typically caused by network loss. Larger percentages of loss or short, high bursts of loss may lead to higher normalized freeze. |
| Harmonic Frame Rate Average | Frames per second (FPS) | Greater than 0.15 | The harmonic average of the incoming video framerate. This typically represents the regularity of the incoming frames along with the rate of frames. A low value can stem from jitter in the incoming frames, freezes, burst arrivals, and low FPS itself. These are typically related to network issues, but (rarely) can also be caused by devices not producing consistent output framerates.|
| Audio / Video Sync | Milliseconds | Between -900 ms to 900 ms | This metric indicates the audio / video sync in milliseconds. The sync value is calculated as (audioDelay – videoDelay). A positive value indicates audio is behind while a negative value indicates video is behind. Audio video sync issues may be caused by various factors, most common of which include bad capture devices and network issues delaying one modality more than the other. |
| Loss Recovery Attempt Rate | Count | Less than 21 | Indicates the number of times there was a request to recover from network loss causing video to freeze. This metric is typically caused by packet loss on the network and can result in short to long freezes depending on the nature of loss. Mitigating the source of network loss should improve quality. |
| Source Freeze Count | Count | Less than 75 | The number of times the outbound screen share didn’t generate a new frame for more than one second at a stretch. For screen sharing, this value can potentially relate to permissions of screen capture, and can also result from performance issues causing glitches while capturing screen content. |
| Video Encoder / Decoder Hardware Failure | Boolean | False | This flag indicates that there has been an error raised from the hardware encoding (or decoding) component. Typically, such errors are handled by the application by falling back to software encoding / decoding but it can result in degraded performance if the endpoint doesn’t have a CPU with sufficient processing power. |

### CPU and Battery Details
|Measure Name |Units |Good Threshold |Description |
|:---|:---|:---|:---|
|System CPU Usage | Percentage | Less than 80% | The percentage of system CPU resources being consumed during the call. If System CPU usage is high relative to the Teams app CPU usage, it can indicate resource contention on the host. |
|Teams app CPU Usage | Percentage |Less than 80% | The percentage of system CPU resources being consumed specifically by the Teams app during the call. |
| Battery level | Charging or Percentage | Greater than 10% | Where an endpoint includes a battery as a power source, this metric indicates the percentage of the battery remaining or if the device is plugged in and charging. |


## Client platforms that support real-time telemetry

- Windows
- macOS
- Android
- iOS
- Teams web client (including VDI 1.0 and VDI 2.0)

Real-time telemetry isn't available in older versions of Teams. If no telemetry is available, try updating your client.

## Teams devices that support real-time telemetry

- Teams displays
- Teams phone
- Teams Rooms
- Teams Rooms on Surface Hub

> [!NOTE]
> Devices that joined the meeting using Cloud Video Interop (CVI) solutions are not supported in Real-Time Analytics.

## Limitations

- Real-time telemetry is only available for scheduled meetings and Meet Now. For PSTN, 1:1 calls, and group calls, real-time telemetry isn't available.
- Real-time telemetry doesn't support view-only participants in meetings.
- Real-time telemetry is only available for presenters of live events and town halls. It's not available for live events or town halls attendees.
- If external participants join a meeting, their display name shows as **unavailable** to retain cross-tenant privacy. The real-time telemetry of anonymous users isn't supported and these users are excluded from the participant list in Real-Time Analytics.
- If a meeting is longer than 3 hours, real-time telemetry is only available for the *last 3 hours*.
- If an organization's users join a federated meeting but didn't organize the meeting, that organization only sees details for their own users in Real-time telemetry. An organization that organizes a federated meeting sees all participants.

## Related topics

[Set up per-user call analytics](set-up-call-analytics.md)

[Use Microsoft Teams administrator roles to manage Teams](/MicrosoftTeams/using-admin-roles).
