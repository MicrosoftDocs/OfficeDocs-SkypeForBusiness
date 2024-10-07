---
title: "Intelligent media quality classifiers in CQD"
author: mkbond007
ms.author: mabond
manager: pamgreen
ms.reviewer: jamp, oloper, hakanbe, mamcgrath
ms.date: 10/03/2024
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - Tier1
search.appverid: MET150
audience: Admin
appliesto: 
  - Microsoft Teams
  - Skype for Business
ms.localizationpriority: medium
ms.custom: 
 - Reporting
description: "Learn how intelligent media quality classifiers are used to better determine call quality in the Call Quality Dashboard (CQD) for Microsoft Teams and Skype for Business."
---

# Intelligent media quality classifiers in Call Quality Dashboard (CQD)

The Call Quality Dashboard (CQD) for Microsoft Teams and Skype for Business allows you to gain insights into the quality of calls made using Microsoft Teams and Skype for Business services. This topic provides detailed information about intelligent media quality classifiers. To learn more about CQD and how to set it up, see [Set up Call Quality Dashboard](turning-on-and-using-call-quality-dashboard.md).

In CQD, Good and Poor stream classification is performed by a series of conditional statements. For audio, network metrics are used to determine if the performance of the underlying network would have resulted in degraded audio quality, while video and video-based screen sharing (VBSS) use video metrics to perform a similar quality assessment. The intelligent media quality classifiers take a broader and deeper view of the call telemetry, weighing several factors (including network) to determine perceived user experience of the call and to identify possible root cause when there's suspected quality degradation. Because of this difference, it's expected that the Good and Poor values resulting from the [stream classification](stream-classification-in-call-quality-dashboard.md) logic won't necessarily match up with the intelligent media quality classifier findings.

## Overview of intelligent media classifiers in CQD

Intelligent media quality classifiers in CQD use Machine Learning (ML) algorithms that help pinpoint specific problem areas in stream quality. Compared to [Stream classification in CQD](stream-classification-in-call-quality-dashboard.md), intelligent media quality classification in CQD provides IT admins with a more advanced analysis into causality, media degradation, and root cause. These classifiers enable you to take proactive measures for addressing and preventing call quality issues.

To deliver the most comprehensive insights, intelligent media quality classifiers individually address three main real-time media modalities: Audio, Video, and VBSS. These classifiers focus on call quality on a stream level (such as Audio, Video, and VBSS) and then they go further with in-depth analyses in areas such as network, compute device, and input device, allowing for pinpointing specific problem areas.

There are two levels of classification to provide a view into causality and root cause: higher-level and lower-level. Higher-level classifiers predict if audio, video, or VBSS aren't functioning properly, whereas lower-level classifiers predict if a problem was in a network, compute device, or input device.

## Supported platforms and media types

The availability of intelligent media quality classifiers varies depending on the specific platforms and media types, due to differences in telemetry availability across various platforms. We're continuously improving the coverage of the classifiers. The following platforms and media types are covered by intelligent media quality classifiers:

- Media modality and Network classifiers are applied to all platforms and media modalities (Audio, Video, VBSS).
- Compute device classifiers are applied to native platforms (excluding Teams Web, optimized VDI, and CVI) and all media modalities.
- Input device classifiers are applied to native platforms (excluding WebRTC based ones) and audio only.

## When to use intelligent media quality classifiers

There are certain application rules of the intelligent media quality classifiers that determine when to apply the classifiers, with the most basic rules being as follows:  

- Inbound classifiers are applied only if a user is receiving at least 60 seconds of media. In CQD, **this data is recorded** as *Stream Duration Value* for Audio and Video and *Duration Seconds* for Video and VBSS.
- Outbound classifiers are applied only if the user sent at least 60 seconds of respective media. **This data is recorded** as the following:
  - For Audio: AvgFirstReceivedAudioSeconds >= 60
  - For Video and VBSS: SecondVideoDurationSeconds >= 60

## Inbound and outbound streams in Peer-to-Peer (P2P) and Conference calls

In CQD reports, streams are defined as either inbound or outbound. An *inbound stream* is media that's received by a user, whereas an *outbound stream* is media that's sent by a user. You can filter CQD reports by inbound and outbound streams to analyze the quality of media received or sent by users.

Streams are represented with First and Second endpoints. For more information on First and Second endpoint classification, see [Dimensions and measurements available in Call Quality Dashboard (CQD)](dimensions-and-measures-available-in-call-quality-dashboard.md).

The following table provides a summary of the streams in Peer-to-Peer (P2P) and Conference calls:

|Call type|Direct connection|First/Second endpoint classification|
|:-----|:-----|:-----|:-----|
|P2P|Users are connected to each other through inbound and outbound streams.|First and Second both represent client endpoints.|
|Conference|Users are connected to a server, regardless of inbound or outbound stream direction.|Users are labeled as Second and the server is labeled as First.|

For Conference calls, which are more common, the engagement level of certain users—particularly those actively sharing their screen and engaging with audio and video—can significantly shape the overall call experience for all participants. Detecting the influence of these **other users**, or highly active and dominant participants, on others is essential for effective stream quality assessment in Conference calls.

## Local and remote classifiers

The intelligent media quality classifiers, whether for Conference or P2P calls, are segmented into two primary categories: Local and Remote.  

- **Local classifiers** are tailored to evaluate the end-point user's call experience, addressing concerns stemming from inbound streams or local device capabilities and limitations.  
- **Remote classifiers** encompass issues originating from the other endpoint(s) of the call, offering a comprehensive perspective on the overall call quality.  

In both P2P and Conference configurations, observing a Local classifier in a stream direction called *First-to-Second* indicates the analysis of the inbound stream's impact or the local device's capacity and limitations on the user's (known as Second) own call experience.  

The role of Remote classifiers in Second-to-First stream directions is to evaluate whether a participant, known as Second, is adversely affecting the call quality of other users under the same conditions. Additionally, in the context of Conference calls, observing a Remote classifier on a First-to-Second stream indicates if a highly active user, classified as dominant, is detrimentally impacting the call quality experienced by the user, referred to as Second.

## Intelligent media quality classifier definitions

In CQD, intelligent media quality classifiers use local and remote classifiers based on the values of available key quality metrics. The metrics and conditions used to classify media quality are shown in the tables for [Local classifiers](#local-classifiers) and [Remote classifiers](#remote-classifiers).  

The detected problem areas, identified through the intelligent media quality classifiers, indicate quality issues that can be further analyzed by admins to uncover potential root causes. Using CQD, this deeper analysis can provide valuable insights for taking proactive measures to prevent future occurrences.

### Local classifiers

The following Local classifiers are based on a user’s telemetry to predict if the same user experienced issues:

|Classifier|Description|
|:-----|:-----|
|Detected Media Modality|Predicts if the quality of the received media type had issues based on the receive's telemetry.|
|Detected Inbound Network|Predicts if there was an issue with the network on an incoming stream. For Conference calls, this classifier looks at the connection from server to endpoint. For P2P calls, this classifier covers remote user uplink and local downlink issues.|
|Detected Local Compute|Predicts if a user’s compute device (for example: desktop computer or mobile phone running Teams client) is causing degradations to the media quality received by a user.|
|Detected Local Input Device|Predicts if a user’s media capture device (for example: computer’s inbuilt soundcard or microphone) is causing problems for the user.|

#### Local classifier measurements for detected problems

The following list displays the measurements for [Local classifiers](#local-classifiers) using the *Problem* dimension. Each Local classifier is represented with /.../ in the list below:

- /.../ Problem True Count
- /.../ Problem False Count
- /.../ Problem Null Count
- /.../ Problem Rate
- /.../ Problem Rate Upper Limit
- /.../ Problem Rate Lower Limit

For example, the Local classifier *Detected Media Modality* uses the *Problem* dimension with measurements for Problem True Count, Problem False Count, Problem Null Count, Problem Rate, Problem Rate Upper Limit, and Problem Rate Lower Limit.

Detected Inbound Network, Detected Local Compute, and Detected Local Input Device also have the following additional measurements:

- /.../ Caused Problem Rate
- /.../ Caused Problem Rate Upper Limit
- /.../ Caused Problem Rate Lower Limit

### Remote classifiers

The following Remote classifiers are based on a user’s telemetry to predict if the user causes quality issues to other call participants:

|Classifier|Description|
|:-----|:-----|
|Detected Uplink|Predicts if the quality of sent media is degraded due to the link from endpoint to server.|
|Detected Compute Device Causing|Predicts if the quality of sent media is degraded due to user’s compute device.|
|Detected Input Device Causing|Predicts if the quality of sent media is degraded due to user’s media capture device.|

#### Remote classifier measurements for detected problems

The following list displays the measurements for all [Remote classifiers](#remote-classifiers) using the *Problem* dimension. Each Remote classifier is represented with /.../ in the list below:

- /.../ Problem True Count
- /.../ Problem False Count
- /.../ Problem Null Count
- /.../ Problem Rate
- /.../ Problem Rate Upper Limit
- /.../ Problem Rate Lower Limit

For example, the Remote classifier of *Detected Input Device Causing* uses the *Problem* dimension with measurements for Problem True Count, Problem False Count, Problem Null Count, Problem Rate, Problem Rate Upper Limit, and Problem Rate Lower Limit.

### Other user classifiers

Other user classifiers, a type of remote classifier, are based on the problems that a dominant participant has that degrades the experience of the remaining Conference call participants:

|Classifier|Description|
|:-----|:-----|
|Detected Other User Uplink|Predicts if the quality of a user’s received media quality is degraded due to other (dominant) participant’s uplink issues.|
|Detected Other User Compute|Predicts if the quality of a user’s received media quality is degraded due to other (dominant) participant’s compute device issues.|
|Detected Other User Device|Predict if the quality of a user’s received media quality is degraded due to other (dominant) participant’s media capture device issues.|

#### Other user classifier measurement for detected problems

Other user classifiers use the /.../ Problem dimension.

For example, the Other user classifier *Detected Other User Device* has the Problem dimension, listed in CQD as *Detected Other User Device Problem*.

#### Measurement examples

- The dimension *Detected Inbound Network Problem* has measurements for Problem True Count, Problem False Count, Problem Null Count, Problem Rate, Problem Rate Upper Limit, Problem Rate Lower Limit, Caused Problem Rate, Caused Problem Rate Upper Limit, and Caused Problem Rate Lower Limit.
- The dimension *Detected Input Device Causing Problem* includes measurements for a Problem True Count, Problem False Count, Problem Null Count, Problem Rate, Problem Rate Upper Limit, and Problem Rate Lower Limit.

For a list of all available dimensions and measures in CQD, including their name, data type, definition, and possible reasons for blank values, see [Dimensions and measures available in Call Quality Dashboard](dimensions-and-measures-available-in-call-quality-dashboard.md).

## Interpreting intelligent media quality classifiers

Intelligent media quality classifiers assign probabilities to endpoints in calls by learning from user telemetry and Call Quality Feedback ratings. These probabilities are transformed into Boolean values (true/false) that indicate whether the call experience for the corresponding endpoint is considered poor or not.

To determine a stream quality problem rate to help mitigate false predictions, we use percentile-based thresholding. With percentile-based thresholding, the lowest performing 2% of endpoints within a specific platform, region, and media type are identified as having a poor call experience. This thresholding helps IT admins take action on the reported issues that might affect call quality.

The media level classifiers are provided as Local classifiers. For inbound streams or local devices, start by thoroughly assessing the *Detected Media Modality* classifiers that predict the issues related to received Audio, Video, or VBSS. These classifiers incorporate input features from all Local area classifiers--such as *Detected Inbound Network*, *Detected Local Compute*, and *Detected Local Input Device*--along with additional important features that aren't exclusively associated with any area.

In scenarios where the media level classifier predicts a problem, but no area level problems are detected, either the existence of several minor issues or the significant influence of non-overlapping input features suggest further investigation. Usually, at least one Warning field highlights a potential problem.  

If there are area level problem predictions but not at the media level, the classifiers suggest that there were issues with media quality, although they might not have been significant enough to result in a poor user feedback rating.

## Locating the origins of quality issues

In CQD, intelligent media quality classifiers create aggregated views that help address quality issues. These views can be analyzed through a unique set of dimensions that are tailored to specific characteristics of each classifier. This analysis gives admins a more precise understanding of the underlying issues.

For example, Network classifiers might benefit from troubleshooting efforts focused on dimensions such as location and network, whereas Compute and Input Device classifiers might require attention to dimensions related to with device specifications and functionality.

### Network classifier dimensions

Network classifiers include three types of dimensions: location-related, network-related, and device-related.

- Location-related dimensions:
  - Second Domain
  - Second ASN Country
  - Second ASN City
  - Second ASN ISP Name
  - Second Country
  - Second City
  - Second Building Name
- Network-related dimensions:
  - Second Network
  - Second Network Name
  - Second Wifi Band
  - Second Wifi Channel
  - Second Wifi Radio Type
  - Second Wifi Signal Strength
  - Second Network Connection Detail
  - Second Subnet
  - Second BSSID
- Device-related dimensions:
  - Second Wifi Microsoft Driver
  - Second Wifi Vendor Driver
  - Second Compute Device Name

### Compute device classifier dimensions

- Device-related dimensions:
  - Second Compute
  - Device Name
- CPU-related dimensions:
  - Second CPU Name
  - Second CPU Number of Cores
  - Second CPU Processor Speed

### Input device classifier dimensions

- Second Capture
- Dev Name
- Second Capture Device Form Factor
- Second Audio Devices Connection Type
- Second Mic Connection Type
- Second Compute Device Name (if inbuilt audio is used)
- Second Capture Dev Driver

## Troubleshooting quality issues

After [locating the origin of quality issues](#locating-the-origins-of-quality-issues), the detected problem areas identified by [intelligent media quality classifiers](#intelligent-media-quality-classifier-definitions) can be analyzed further to uncover potential root causes and help admins take proactive measures to prevent future issues.

### Network classifiers

Network classifiers predict quality issues largely based on audio telemetry from error handling implemented into Microsoft Teams. This audio telemetry extends the coverage of the raw network degradation distribution effectively. However, if a classifier detects any issues, then there might be visible problems with the raw network metrics as well, except in cases where multiple telemetry collectively influences the outcome. In such instances, the complexity of identifying the root cause might increase due to the combined effects of multiple dimensions. The lowest level CQD dimensions serve as indicators of issues, as listed below.

#### Dimensions related to audio

- Network loss related measures:  
  - Total Call Dropped Failure Percentage  
  - Avg Roaming Count  
- Raw network performance related measures:  
  - Avg Packet Loss Rate
  - Avg Packet Loss Rate Max
  - Avg Round Trip
  - Avg Round Trip Max
  - Avg Network Jitter
  - Avg Network Jitter Max
  - Avg Healed Data Ratio Value
  - Avg Jitter Buffer Size
  - Avg Network Jitter Max
  - Network Avg Loss Rate

#### Dimensions related to video & VBSS

- Recv Avg Freeze Duration
- Avg Recv Freeze Duration Percent
- Avg AV Sync Distance Avg
- Avg AV Sync Distance Min
- Avg AV Sync Distance Max
- Avg AV Sync Distance STDEV
- Avg Video Post FECPLR

#### Network root cause examples

- If the wifi strength is low, then the network classifier indicates that the office location isn't adequately covered with wifi. Check the number and positioning of the access points.
- If the network metrics are worsening periodically in a specific location, then the network classifier indicates that there's network congestion when the calling volume is high. For example, if there are monthly company meetings where a large part of the site is joining, you might consider [deploying eCDN](/ecdn/intro).
- If AV Sync distance values are high, then the network classifier indicates that there are network congestion problems because audio is prioritized over video. Check that there's enough bandwidth, and that the bandwidth is stable enough to allow for good quality video and VBSS.

### Compute classifiers

Compute classifiers predict quality issues primarily based on CPU processing time, while also considering the memory state.

The following compute resource-related dimensions are also available as average metrics that might be useful for finding the root cause:

- Second Process CPU Usage Average
- Second Process CPU Usage Max
- Second System CPU Usage Average
- Second System CPU Usage Max
- Second Process Memory Usage Average
- Second Process Memory Usage Max
- Second System Memory Usage Average
- Second System Memory Usage Max

#### Compute root cause examples

- If the system CPU usage is high but the process CPU is low, then the Compute classifier indicates that a compute device is running other tasks that consume the resources.
- If the process CPU usage is high, then the Compute classifier indicates that there might be problems related to lacking the CPU resources on that platform for calling. Check if video processing is offloaded to the GPU.

### Input device classifiers

Input device classifiers target quality issues associated with audio capture devices, including microphones.  

The following CQD dimensions that can indicate possible audio issues are:

- Avg Second Audio Send Noise Level
- Avg Second Audio Send Signal Level
- Second Mic Device Failure
- Second No Mic Devices Enumerated Failure
- Second Mic Initialization Failure
- Second Mic Device Failure Rate
- Second Device Capture Not Functioning Event Ratio
- Audio Capture Device In Use
- Audio Render Device In Use

The recommended range for signal level is (-24,-14), the optimal for noise is <-60.

#### Input device root cause examples

- If the audio noise level is high, then the device classifier indicates that the microphone might be too far from the user for optimal experience. Check if the device is matching the use case – such as if the speakerphone used in the meeting room is suitable for the meeting room size.
- If the audio signal level is very high, then the device classifier shows that the user is too close to the microphone and even if there isn't microphone overloading, then the user will be noticeably louder than other call participants. Check if the device has the latest drivers.

## Maintenance of classification models

The classifier models are monitored on the general population of Microsoft Teams users. If an anomaly is detected, then it is investigated and there's a high chance that the model is re-trained. This can cause temporal fluctuation of respective problem detection rates. Where these fluctuations would cause a significant change in detection rates, we will post a message to inform Teams admins through the M365 Message Center.

## Related topics

[Dimensions and measures available in Call Quality Dashboard](dimensions-and-measures-available-in-call-quality-dashboard.md)

[Use CQD to manage call and meeting quality](quality-of-experience-review-guide.md)

[Set up Call Quality Dashboard](turning-on-and-using-call-quality-dashboard.md)

[What is Call Quality Dashboard?](CQD-what-is-call-quality-dashboard.md)
