---
title: "Use real-time telemetry to troubleshoot poor meeting quality"
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.reviewer: mikedav, vkorlep
ms.topic: article
ms.assetid: 66945036-ae87-4c08-a0bb-984e50d6b009
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.collection:
  - M365-voice
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

## What is Real-Time Analytics?

Today, individual meeting troubleshooting is available for Teams administrators through [Call Analytics](use-call-analytics-to-troubleshoot-poor-call-quality.md) after the meeting ends. Real-Time Analytics lets admins troubleshoot scheduled meetings while they're in progress.

Real-Time Analytics shows detailed information about Teams meetings for each user in your Office 365 account, updated in real time. It includes information about devices, network, connectivity, audio, video, and content sharing issues, which will help admins troubleshoot call quality more effectively.

As a Teams admin, you get full access to all real-time telemetry data for each user. In addition, you can assign Azure Active Directory roles to support staff. To learn more about these roles, see [Give permission to support and help desk staff](set-up-call-analytics.md#give-permission-to-support-and-helpdesk-staff).

## Where to find per-user real-time troubleshooting telemetry

To see all meeting information and data for a user, go to the [Teams admin center](https://admin.teams.microsoft.com). Under **Users** > **Manage users**, select a user, and open the **Meetings & calls** tab on the user's profile page. Under **Recent meetings**, you'll see a list of meetings the user has attended within the past 24 hours *for which real-time telemetry is available*, including any in progress meetings. If the meeting is not in progress or doesn't have real-time telemetry data, it will show up in **Past meetings**.

:::image type="content" alt-text="Screenshot of recent meetings table." source="media/recent-meetings.png" lightbox="media/recent-meetings.png":::

To get additional information about participants of a meeting that's in progress, including their device, network, and audio statistics, find the meeting in **Recent meetings** and select the link under the **Participants** column.

:::image type="content" alt-text="Screenshot of participant details table." source="media/participant-details-edit.png" lightbox="media/participant-details-edit.png":::

To look at the telemetry of a given user for an in-progress meeting, including information around device, network, audio, video, and content sharing details, select the **Meeting ID**.

:::image type="content" alt-text="Screenshot of call analytics user session data." source="media/real-time-telemetry-edit.png" lightbox="media/real-time-telemetry-edit.png":::

## Measures available in Real-Time Analytics

### Audio
|Measure Name |Units |Good Threshold |Description |
|:---|:---|:---|:---|
|Jitter |Milliseconds |Less than 30 ms |Jitter is a measure of the variation in packet delay for a data stream. When this is too high, audio can become choppy. | 
|Packet Loss |Percentage |Less than 5% |Packet loss occurs when data packets fail to reach their destination. The percentage of packets lost is based on the total number of packets sent. |
|Round Trip Time |Milliseconds |Less than 500 ms |Round trip time is the time it takes for a single packet to travel from the client to the remote endpoint and back to the client. High round trip time can cause delays in stream playback. An example of this is when two people in a meeting are unintentionally speaking over each other due to the delay. |
|Bitrate |Kilobits per second (Kbps) |Greater than 24 Kbps |Throughput of the audio stream expressed in kilobits per second. |


### Video
|Measure Name |Units |Good Threshold |Description |
|:---|:---|:---|:---|
|Round Trip Time |Milliseconds |Less than 500 ms |Round trip time is the time it takes for a single packet to travel from the client to the remote endpoint and back to the client. High round trip time can cause delays in stream playback. An example of this is when two people in a meeting are unintentionally speaking over each other due to the delay. |
|Bitrate |Megabits per second (Mbps) | Information only |Throughput of the video stream expressed in megabits per second. |
|Frame Rate (Video) |Frames per second |360p or better: 25-30 FPS <br/> 270p or lower: 7-15 FPS |For outbound video streams, frame rate (FPS) is the number of frames per second of video the client is sending. Lower than expected values here may suggest system resource constraints, insufficient network bandwidth, or misbehaving video capture devices. Different resolutions have different acceptable FPS ranges. |
|Codec |String | Information only |Displays the video codec and rendering mode of the outbound video stream. (Example: H264 SW HW indicates an H264 video stream using both software and hardware rendering.)|
|Resolution |Pixels | Information only |The resolution of the video being sent. Outbound video resolution is dynamic, based on the highest requirement from an endpoint in the meeting. A client capable of 1920 x 1080 video will only send 640 x 360 video if no clients are displaying that user's video in a frame larger than 640 x 360 |


### Application Sharing (VBSS)
|Measure Name |Units |Good Threshold |Description |
|:---|:---|:---|:---|
|Packet Loss |Percentage |Less than 5% |Packet loss occurs when data packets fail to reach their destination. The percentage of packets lost is based on the total number of packets sent. |
|Round Trip Time |Milliseconds |Less than 500 ms |Round trip time is the time it takes for a single packet to travel from the client to the remote endpoint and back to the client. High round trip time can cause delays in stream playback. An example of this is when two people in a meeting are unintentionally speaking over each other due to the delay. |
|Bitrate |Megabits per second (Mbps) | Information only |Throughput of the VBSS stream expressed in megabits per second. |
|Frame Rate |Frames per second (FPS) | Information only |For VBSS, frame rate is content-aware to ensure as many frames as necessary are sent to ensure a good experience while avoiding sending frames if they're not needed. For example, sharing a text document on-screen only requires 1 frame-per-second to produce a good experience, whereas sharing a video or content with more activity will increase frames per second to a maximum of 30 FPS to produce a smoother experience. |
|Codec |String | Information only |Displays the codec and rendering mode of the VBSS stream. (Example: H264 SW HW indicates an H264 VBSS stream using both software and hardware rendering.)|
|Resolution |Pixels | Information only |The resolution of the VBSS stream being sent and received. |


## Client platforms supported for real-time telemetry

- Windows
- macOS
- Linux
- Android
- iOS

> [!NOTE]
> Teams Web client (including VDI) does not support delivery of telemetry in real time.

## Teams devices with support for real-time telemetry

- MTR - Surface Hub
- MTR - Teams Display
- MTR - Collaboration bar
- IP Phone devices

> [!NOTE]
> Devices that joined the meeting using Cloud Video Interop (CVI) solutions are not supported in Real-Time Analytics.


## Limitations

- Real-time telemetry is only available for scheduled meetings. For ad hoc meetings like Meet Now, PSTN, 1:1 calls, and group calls, real-time telemetry isn't available.
- Real-time telemetry is only available for presenters of scheduled live event. It's currently not available for live event attendees.
- Real-time telemetry data is available for a meeting under **Recent meetings** for 24 hours after the meeting has ended. After 24 hours, you can't access the data and the meeting moves to **Past meetings**. If a meeting is longer than 3 hours, real-time telemetry will only be available for the *last 3 hours*.
- Telemetry isn't available in real time when using older versions of Teams. If no telemetry is available, try updating your client.
- If external participants or anonymous users join a meeting, their display name will show as **unavailable** to retain cross-tenant privacy.

## Related topics

[Set up per-user call analytics](set-up-call-analytics.md)

[Use Microsoft Teams administrator roles to manage Teams](/MicrosoftTeams/using-admin-roles).
