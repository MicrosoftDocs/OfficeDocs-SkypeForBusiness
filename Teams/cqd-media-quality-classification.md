---
title: "Media quality classification in CQD"
author: mkbond007
ms.author: mabond
manager: pamgreen
ms.reviewer: jamp, oloper, hakanbe, mamcgrath
ms.date: 09/11/2024
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
  - Skype for Business
  - Microsoft Teams
ms.localizationpriority: medium
ms.custom: 
 - Reporting
description: "Learn how media quality is classified in the Call Quality Dashboard (CQD) for Microsoft Teams and Skype for Business."
---

# Media quality classification in Call Quality Dashboard (CQD)

The Call Quality Dashboard (CQD) for Microsoft Teams and Skype for Business allows you to gain insights into the quality of calls made using Microsoft Teams and Skype for Business services. This topic provides detailed information about the quality classification of media streams. To learn more about CQD and how to set it up, see [Set up Call Quality Dashboard](turning-on-and-using-call-quality-dashboard.md).

## Overview of CQD media classifiers

CQD media classifiers use Machine Learning (ML) algorithms that help pinpoint specific problem areas in call/steam quality. These classifiers enable IT admins to take proactive measures for addressing and preventing call quality issues.

To deliver the most comprehensive insights, CQD media classifiers individually address three main real-time media modalities: Audio, Video, and Screensharing. These classifiers focus on call quality on a stream level (such as Audio, Video, and Screensharing) and then they go further with in-depth analyses in areas such as Network, Compute Device, and Input Device, allowing for pinpointing specific problem areas.

These CQD media quality classifiers provide a view into causality and root cause. We determine two levels of classification/classifiers to provide a view into causality and root cause. Higher-level classifiers predict/determine if audio, video, or screensharing are not functioning properly and lower-level classifiers **(also called area classifers?)** predict/determine if a problem was in the network, compute device, or media capture device. For more information on determining causality, see [](#internal-link). For more information on diagnosing root cause and troubleshooting, see [](#internal-link).

## Supported platforms and media types

The availability of the CQD Media classifiers varies depending on the specific platforms and media types, due to differences in telemetry availability across various platforms. We are continuously improving the coverage of the classifiers. The following platforms and media types are covered by CQD media classifiers:

- Media Modality and Network classifiers are applied to all platforms and media modalities (Audio, Video, Screen Sharing).
- Compute Device classifiers are applied to native platforms (excluding Teams Web, optimized VDI, and CVI) and all media modalities.
- Input Device classifiers are applied to native platforms (excluding WebRTC based ones) and audio only.

## When to use media classifiers

There are certain application rules of the CQD media classifiers that determine when to apply the classifiers, with the most basic rules being as follows:  

- Inbound classifiers are applied only if a user is receiving at least 60 seconds of media. In CQD, **this data is recorded** as *Stream Duration Value* for Audio and Video and *Duration Seconds* for Video and Screensharing.
- Outbound classifiers are applied only if the user sent at least 60 seconds of respective media. **This data is recorded** as the following:
  - For Audio: Avg First Received Audio Seconds >= 60
  - For Video and Screensharing: Second Video Duration Seconds

## Inbound and outbound streams in Peer-to-Peer (P2P) and Conference calls

In CQD reports, streams are **defined/listed/reported** as either inbound or outbound. An **inbound stream** is media that's received by the user, while an **outbound stream** is media that are sent by the user. The following table provides a summary of the streams in Peer-to-Peer (P2P) and Conference calls:

|Call type|Direct connection|First/Second endpoint classification|
|:-----|:-----|:-----|:-----|
|P2P|Users are connected to each other through inbound and outbound streams.|Both participants are labeled as First and Second, reflecting their equal status in the direct connection.|
|Conference|Users are connected to a server, regardless of inbound or outbound stream direction.|Users are labeled as Second and the server is labeled as First.|

For Conference calls, which are more common, the engagement level of certain users—particularly those actively sharing their screen and engaging with audio and video—can significantly shape the overall call experience for all participants. Detecting the influence of these **other users**, or highly active and dominant participants, on others is essential for effective call quality assessment in Conference calls.

## Local and remote classifiers

The CQD media classifiers, whether for Conference or P2P calls, are segmented into two primary categories: Local and Remote.  

- **Local classifiers** are tailored to evaluate the end-point user's call experience, addressing concerns stemming from inbound streams or local device capabilities and limitations.  
- **Remote classifiers** encompass issues originating from the other end point(s) of the call, offering a comprehensive perspective on the overall call quality.  

In the both P2P and Conference configurations, observing a Local classifier in a stream direction called *First-to-Second* indicates the analysis of the inbound stream's impact or the local device's capacity and limitations on the user's (known as Second) own call experience.  

The role of Remote classifiers in Second-to-First stream directions is to evaluate whether a participant, known as Second, is adversely affecting the call quality of other user(s) under the same conditions. Additionally, in the context of Conference calls, observing a Remote classifier on a First-to-Second stream indicates if a highly active user, classified as dominant, is detrimentally impacting the call quality experienced by the user referred to as Second.

For more information on First and Second endpoint classification, see [Dimensions and measurements available in Call Quality Dashboard (CQD)](dimensions-and-measures-available-in-call-quality-dashboard.md).

## Media quality classifier definitions

In CQD, media quality classifiers use local and remote classifiers **(and other user classifiers?)......** based on the values of the available key quality metrics. The metrics and conditions used to classify media quality are shown in the tables that follow.  

The detected problem areas, identified through the CQD media classifiers, indicate quality issues that can be further analyzed by admins to uncover potential root causes. This deeper analysis using CQD can provide valuable insights for taking proactive measures to prevent future occurrences.

### Local classifiers

The following Local classifiers are based on a user’s telemetry to predict if the same user experienced issues:

|Classifier|Description|
|:-----|:-----|
|Detected Media Modality|Predicts if the quality of the received media type had issues based on the receive's telemetry.|
|Detected Inbound Network|Predicts if there was an issue with the network on an incoming stream. For Conference calls, this classifier looks at the connection from server to endpoint. For P2P calls, this classifier covers remote user uplink and local downlink issues.|
|Detected Local Compute|Predicts if a user’s compute device (for example: desktop computer or mobile phone running Teams client) is causing degradations to the media quality received by a user.|
|Detected Local Input Device|Predicts if a user’s media capture device (for example: computer’s inbuilt soundcard or microphone) is causing problems for the user.|

#### Local classifier measurements for detected problems

**INSERT INFO HERE**

### Remote classifiers

The following Remote classifiers are based on a user’s telemetry to predict if the user causes quality issues to other call participants:

|Classifier|Description|
|:-----|:-----|
|Detected Uplink Problem|Predicts if the quality of sent media is degraded due to the link from endpoint to server.|
|Detected Compute Device Causing|Predicts if the quality of sent media is degraded due to user’s compute device.|
|Detected Input Device Causing|Predicts if the quality of sent media is degraded due to user’s media capture device.|
|Detected Leaking Echo|Predicts if the quality of sent audio is degraded due to acoustic echo.|

#### Remote classifier measurements for detected problems

**INSERT INFO HERE**

### Other user classifiers

The following Other user classifiers are based on the problems that a dominant participant has that degrades the experience of the remaining Conference call participants:

|Classifier|Description|
|:-----|:-----|
|Detected Other User Uplink|Predicts if the quality of a user’s received media quality is degraded due to other (dominant) participant’s uplink issues.|
|Detected Other User Compute|Predicts if the quality of a user’s received media quality is degraded due to other (dominant) participant’s compute device issues.|
|Detected Other User Device|Predict if the quality of a user’s received media quality is degraded due to other (dominant) participant’s media capture device issues.|
|Detected Hearing Echo|Predicts if the quality of a user’s received media quality is degraded due to other (dominant) participant’s echo issues.|

#### Other user classifier measurements for detected problems

**INSERT INFO HERE**

## Interpreting media quality classifiers

CQD media classifiers assign probabilities to endpoints in calls by learning from user telemetry and Call Quality Feedback ratings. These probabilities are transformed into Boolean values (true/false) that indicate whether the call experience for the corresponding endpoint is considered poor or not.

To determine a stream quality problem rate to help mitigate false predictions, we use percentile-based thresholding. With percentile-based thresholding, the lowest performing 2% of endpoints within a specific platform and region are identified as **having poor call experiences/a poor call experience**. This thresholding helps IT admins take action on the reported issues that might affect call quality.

**The area classifiers are provided as Local classifiers.** For inbound streams or local devices, start by thoroughly assessing the *Detected Media Modality* classifiers that predict the issues related to received Audio, Video or Screensharing. These classifiers incorporate input features from all Local area classifiers--such as *Detected Inbound Network*, *Detected Local Compute*, and *Detected Local Input Device*--along with additional important features that are not exclusively associated with any area.

In scenarios where the media level classifier predicts a problem, but no area level problems are detected, either the existence of several minor issues or the significant influence of non-overlapping input features suggest further investigation. Usually, at least one Warning field highlights a potential problem.  

If there are area level problem predictions but not at the media level, the classifiers suggest that there were issues with media quality, although they may not have been significant enough to result in a poor user feedback rating.

## Locating origins of quality issues

CQD media classifiers create aggregated views that help address quality issues. These views can be analyzed through a unique set of dimensions that are tailored to specific characteristics of each classifier. This analysis gives admins a more precise understanding of the underlying issues.

For example, Network classifiers might benefit from troubleshooting efforts focused on dimensions such as location and network, whereas Compute and Input Devices classifiers might require attention to dimensions related to with device specifications and functionality.

**INSERT DIMENSIONS INFO HERE**

## Troubleshooting quality issues

After [locating the origin of quality issues](#locating-origins-of-quality-issues), the detected problem areas identified by [CQD media classifiers](#media-quality-classifier-definitions) can be analyzed further to uncover potential root causes and help admins take proactive measures to prevent future issues.

### Network classifiers

**INSERT DIMENSIONS INFO HERE**

#### Network root cause examples

### Compute classifiers

**INSERT DIMENSIONS INFO HERE**

#### Compute root cause examples

### Input device classifiers

**INSERT DIMENSIONS INFO HERE**

#### Input device root cause examples

## Maintenance of classification models

The classifier models are monitored on the general population of Microsoft Teams users. If an anomaly is detected, then it is investigated and there is a high chance that the model is re-trained. This can cause temporal fluctuation of respective problem detection rates. Where these fluctuations would cause a significant change in detection rates, we will post a message to inform Teams admins through the M365 Message Center.

## Related topics

[Dimensions and measures available in Call Quality Dashboard](dimensions-and-measures-available-in-call-quality-dashboard.md)

[Use CQD to manage call and meeting quality](quality-of-experience-review-guide.md)

[Set up Call Quality Dashboard](turning-on-and-using-call-quality-dashboard.md)

[What is Call Quality Dashboard?](CQD-what-is-call-quality-dashboard.md)
