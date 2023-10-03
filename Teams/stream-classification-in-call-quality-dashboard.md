---
title: "Stream classification in Call Quality Dashboard (CQD)"
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: gageames
ms.date: 05/22/2018
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.collection: 
  - M365-voice
  - Tier1
search.appverid: MET150
audience: Admin
appliesto: 
  - Skype for Business
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom: 
  - Optimization
description: "Learn how stream quality is classified in the Call Quality Dashboard (CQD) for Microsoft Teams and Skype for Business Online."
---

# Stream Classification in Call Quality Dashboard (CQD)

The Call Quality Dashboard (CQD) for Microsoft Teams and Skype for Business Online allows you to gain insights into the quality of calls made using Microsoft Teams and Skype for Business services. This topic provides detailed information about the quality classification of media streams. To learn more about CQD and how to set it up, see [Set up Call Quality Dashboard](turning-on-and-using-call-quality-dashboard.md).

## Classifier Definitions

Streams in CQD are classified as _Good_, _Poor_, or _Unclassified_ based on the values of the available key quality metrics. The metrics and conditions used to classify stream are shown in the tables that follow. CQD's "Poor Due To" dimensions can be used to understand which metric is responsible for a _Poor_ classification. For more information on these dimensions, see [Dimensions and measures available in Call Quality Dashboard](dimensions-and-measures-available-in-call-quality-dashboard.md).

### Audio Classifier

If one or more of the following conditions are met and Packet Utilization is > 500 packets, an audio stream is marked as _Poor_:

|Metric|Scenario|Condition|Explanation|
|:-----|:-----|:-----|:-----|
|Round Trip|ALL|> 500|Average round-trip network propagation time, computed in milliseconds. Details available in [RFC3550](https://tools.ietf.org/html/rfc3550).|
|Packet Loss Rate|ALL|> 0.1|Average packet loss rate for stream.|
|Jitter|ALL|> 30|Average jitter for stream in milliseconds.|
||||

### Video Classifier due to Freeze

The video stream is marked  _Good_ or _Poor_ based on the value of a classifier score generated to estimate that the end user experienced Frozen Video. This classifier is available for Microsoft Teams product only.

|Step #|Metric|Scenario|Condition |Classification if Condition is True |Classification if Condition is False |Classification if Metric is Unavailable |Explanation |
|:--- |:--- |:--- |:--- |:--- |:--- |:--- |:--- |
|1|Video Poor Due to Freeze Classifier |Is Server Pair is Client : Server|>0.246|_Poor_|_Good_|_Unclassified_|A Score between 0 and 1 that is generated based on a combination of user experience, freeze duration statistics and overall call experience |
|2|Video Poor Due to Freeze Classifier |Is Server Pair is Client : Client|>0.524|_Poor_|_Good_|_Unclassified_|A Score between 0 and 1 that is generated based on a combination of user experience, freeze duration statistics and overall call experience |
|  |  |  |  |  |  |  |

### Video Classifier
A video stream is marked as _Good_ or _Poor_ based on the value of the first available metric in the following order:

|Step #|Metric|Condition |Classification if Condition is True |Classification if Condition is False |Classification if Metric is Unavailable |Explanation |
|:--- |:--- |:--- |:--- |:--- |:--- |:--- |
|1|Video Local Frame Loss Percentage Avg|> 50% |_Poor_|_Good_|Proceed to step 2|Average percentage of video frames lost as displayed to the user. The average includes frames recovered from network losses.|
|2|Video Frame Rate Avg|< 7|_Poor_|_Good_|Proceed to step 3|Average frames per second received for a video stream, computed over the duration of the session.|
|3|Video Post FECPLR|> 0.15|_Poor_|_Good_|_Unclassified_|Packet loss rate after FEC has been applied aggregated across all video streams and codecs.|
|  |  |  |  |  |  |  |

### VBSS Classifier

A VBSS stream is marked as _Good_ or _Poor_ based on the value of the first available metric in the following order:

|Step # |Metric |Condition |Classification if Condition is True |Classification if Condition is False |Classification if Metric is Unavailable |Explanation |
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|1|Video Local Frame Loss Percentage Avg|Codec is NOT H264S</br>And</br>StreamDirection is Inbound</br></br>If FrameLoss > 50%|_Poor_|_Good_|_Unclassified_|Average percentage of video frames lost as displayed to the user. The average includes frames recovered from network losses. FrameLoss is only used for classifying inbound non-H264S streams.|
|2|Video Frame Rate Avg|< 1|_Poor_|_Good_|_Unclassified_|Average frames per second received for a video stream, computed over the duration of the session. Applies to all outbound streams and either StreamDirection for H264S.|
| |  | | | |  ||


### Application Sharing Classifier

An application sharing stream is marked as _Poor_ if one or more of the following conditions are met:

| Metric     | Condition | Explanation |
|:---        |:---       | :--- |
| Spoiled Tile Percent Total | > 36 | Percentage of tiles that are discarded instead of sent to a remote peer (for example, from the MCU to a viewer). Discarded (or spoiled) tiles might be caused by bandwidth restrictions between client and server. |
| AppSharing RDP Tile Processing Latency Average | > 400 | Average latency in milliseconds processing tiles on the RDP Stack at the conferencing server. |
| AppSharing Relative OneWay Average | > 1.75 | Average relative one-way delay between the endpoints in seconds for application sharing streams. |
| | | |

## Unclassified Streams

In CQD, a stream is marked _Unclassified_ when Interactive Connectivity Establishment (ICE) connectivity fails or when all the metrics required to compute the stream classification are not reported.

To check for ICE connectivity failures, examine the dimensions "First Connectivity Ice" and "Second Connectivity Ice" for a "FAILED" value. If either value indicates a failure, the stream is marked as _Unclassified_.

If ICE connectivity succeeded for an _Unclassified_ stream, the stream is likely considered _Unclassified_ because key stream metrics were not reported. There are a few reasons these metrics may not be reported:

- **QoE reports were not received** — The metrics used for classification are reported in a QoE report sent at the end of a call. If this report is not produced (for example, because some third-party endpoints may not send QoE) or could not be sent (for example, because of a network outage), CQD is unable to classify the stream.

  > [!TIP]
  > The "QoE Record Available" dimension can be used to determine whether a QoE report was received for a stream. Note that this dimension will have a value of "True" if a QoE report was received from either endpoint. A QoE report from both endpoints is required for the most accurate reporting of metrics.

- **Short calls** — Short calls may not have enough media activity to compute key stream metrics. Without these metrics, CQD is unable to classify the stream.

  > [!TIP]
  > The dimensions "Duration (Seconds)", "Duration (Minutes)", "Duration 5 seconds or less", and "Duration 60 seconds or more" can be used to determine the duration of a stream. The measurement "Avg Call Duration" can also be used to compute the average duration for a set of streams.

- **Low packet utilization** — Like the "short call" scenario, sufficient packet utilization is required for computation of key stream metrics. Without these metrics, CQD is unable to classify the stream.
  - A common low packet utilization scenario occurs when an attendee joins a meeting to listen to the presenter, but never speaks (the microphone is muted for most of the call). Here, the audio stream inbound to the client has high packet utilization while the audio stream outbound from the client has little to no packet utilization. The duration of the stream may be an hour or longer but the packet utilization on the stream from the client to the server is low since the microphone was muted, and an _Unclassified_ stream results.

  > [!TIP]
  > The "Packet Utilization" dimension and "Avg Packet Utilization" measurement can be used to determine the packet activity of a stream.

## Related Topics
[Improve and monitor call quality for Teams](monitor-call-quality-qos.md)

[What is CQD?](CQD-what-is-call-quality-dashboard.md)

[Set up Call Quality Dashboard (CQD)](turning-on-and-using-call-quality-dashboard.md)

[Upload tenant and building data](CQD-upload-tenant-building-data.md)

[CQD data and reports](CQD-data-and-reports.md)

[Use CQD to manage call and meeting quality](quality-of-experience-review-guide.md)

[Dimensions and measures available in CQD](dimensions-and-measures-available-in-call-quality-dashboard.md)

[Use Power BI to analyze CQD data](CQD-Power-BI-query-templates.md)
