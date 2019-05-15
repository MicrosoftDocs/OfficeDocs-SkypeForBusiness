---
title: "VideoStream table"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 2/1/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 4275ede7-5467-4a97-b8c8-a4b00917bf32
description: "Each record represents one video stream. One video media line usually contains two video streams."
---

# VideoStream table
 
Each record represents one video stream. One video media line usually contains two video streams.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**ConferenceDateTime** <br/> |datetime  <br/> |Primary  <br/> |Referenced from the [MediaLine table](medialine-0.md).  <br/> |
|**SessionSeq** <br/> |int  <br/> |Primary  <br/> |R Referenced from the [MediaLine table](medialine-0.md).  <br/> |
|**MediaLineLabel** <br/> |tinyint  <br/> |Primary  <br/> |Referenced from the [MediaLine table](medialine-0.md).  <br/> |
|**StreamID** <br/> |int  <br/> |Primary  <br/> |Unique ID within a media line.  <br/> |
|**VideoPayloadDescription** <br/> |smallint  <br/> |Foreign, Primary  <br/> |Payload description. See the [PayloadDescription table](payloaddescription.md) for more information. <br/> |
|**JitterInterArrival** <br/> |int  <br/> | <br/> |Average network jitter from Real Time Control Protocol (RTCP) statistics.  <br/> |
|**JitterInterArrivalMax** <br/> |int  <br/> | <br/> |Maximum network jitter during the video session.  <br/> |
|**RoundTrip** <br/> |int  <br/> | <br/> |Round trip time from RTCP statistics.  <br/> |
|**RoundTripMax** <br/> |int  <br/> | <br/> |Maximum round trip time for the video stream.  <br/> |
|**PacketLossRate** <br/> |decimal(5,4)  <br/> | <br/> |Average packet loss rate during the call.  <br/> |
|**PacketLossRateMax** <br/> |decimal(5,4)  <br/> | <br/> |Maximum packet loss observed during the call.  <br/> |
|**PacketUtilization** <br/> |int  <br/> | <br/> |Packet count for the video stream (Real Time Transport Protocol, RTP).  <br/> |
|**BandwidthEst** <br/> |int  <br/> | <br/> |Bandwidth estimates for the video stream.  <br/> |
|**VideoResolution** <br/> |char(9)  <br/> | <br/> |Resolution of the video in pixels width multiplied by pixels height. Reported as a string.  <br/> |
|**VideoBitRateAvg** <br/> |int  <br/> | <br/> |Average bit rate of the video stream.  <br/> |
|**InboundVideoFrameRateAvg** <br/> |decimal(9,4)  <br/> | <br/> |The video frame rate received.  <br/> |
|**OutboundVideoFrameRateAvg** <br/> |decimal(9,4)  <br/> | <br/> |The video frame rate sent.  <br/> |
|**VideoBitRateMax** <br/> |int  <br/> | <br/> |The maximum video bit rate during the video session.  <br/> |
|**VideoFrameLossRate** <br/> |decimal(9,4)  <br/> | <br/> |The percentage of total video frames that are lost.  <br/> |
|**VideoFEC** <br/> |bit  <br/> | <br/> |Not available.  <br/> |
|**VideoLocalFrameLossPercentageAvg** <br/> |decimal(9,4)  <br/> ||The percentage of total video frames that are lost.  <br/> |
|**CIFQualityRatio** <br/> |tinyint  <br/> ||The percentage of the call that was at the Common Interchange Format (CIF) resolution.  <br/> |
|**VGAQualityRatio** <br/> |tinyint  <br/> ||The percentage of the call that was at VGA resolution.  <br/> |
|**HD720QualityRatio** <br/> |tinyint  <br/> ||The percentage of the call that was at HD720 resolution.  <br/> |
|**NoneDropRatio** <br/> |tinyint  <br/> ||Percentage of call duration with no frame drop.  <br/> |
|**BDropRatio** <br/> |tinyint  <br/> ||Percentage of call duration with B frame drop.  <br/> |
|**BPDropRatio** <br/> |tinyint  <br/> ||Percentage of call duration with BP frame drop.  <br/> |
|**BPSPDropRatio** <br/> |tinyint  <br/> ||Percentage of call duration with BPSP frame drop.  <br/> |
|**BPSPIDropRatio** <br/> |tinyint  <br/> ||Percentage of call duration with BPSPI frame drop.  <br/> |
|**Inbound** <br/> |bit  <br/> | <br/> |Stream data on receiver side is received.  <br/> |
|**Outbound** <br/> |bit  <br/> | <br/> |Stream data on sender side is received.  <br/> |
|**SenderIsCallerPAI** <br/> |bit  <br/> | <br/> |1 means the stream direction is from the caller to callee.  <br/> 0 means the stream direction is from the callee to the caller.  <br/> |
|**LossCongestionPercent** <br/> |float  <br/> ||Indicates the percentage of the time when the call was in a loss congestion state.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**DelayCongestionPercent** <br/> |float  <br/> ||Indicates the percentage of the call during which congestion was caused by the delayed arrival of network packets.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**ContentionDetectedPercent** <br/> |float  <br/> ||Indicates the percentage of the time when the call was competing for network resources.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**BandwidthEstMin** <br/> |int  <br/> ||Minimum amount of bandwidth estimation measured during the call.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**BandwidthEstMax** <br/> |int  <br/> ||Maximum amount of bandwidth estimation measured during the call.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**BandwidthEstStdDev** <br/> |int  <br/> ||Standard deviation of the bandwidth estimation measured during the call.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**BandwidthEstAvge** <br/> |int  <br/> ||Average amount of bandwidth estimation measured during the call.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**LowBandwidthForMultiview** <br/> |float  <br/> ||Percentage of the call where the endpoint determined that the network connection could not support multiview video.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**RelativeOneWayTotal** <br/> |float  <br/> ||Total amount of one-way latency. Relative one-way latency measures the delay between the client and the server.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**RelativeOneWayAverage** <br/> |float  <br/> ||Average amount of one-way latency. Relative one-way latency measures the delay between the client and the server.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**RelativeOneWayMax** <br/> |float  <br/> ||Maximum amount of one-way latency. Relative one-way latency measures the delay between the client and the server.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**RelativeOneWayBurstOccurrences** <br/> |int  <br/> ||Total one-way burst occurrences. A "bursty" transmission is a transmission where data flows in unpredictable bursts as opposed to a steady stream. This metric measures data flow between the client and the server.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**RelativeOneWayBurstDensity** <br/> |int  <br/> ||Total one-way burst density. A "bursty" transmission is a transmission where data flows in unpredictable bursts as opposed to a steady stream. This metric measures data flow between the client and the server.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**RelativeOneWayBurstDuration** <br/> |float  <br/> ||Total one-way burst duration. A "bursty" transmission is a transmission where data flows in unpredictable bursts as opposed to a steady stream. This metric measures data flow between the client and the server.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**RelativeOneWayGapOccurrences** <br/> |int  <br/> ||Total one-way gap occurrences. A "bursty" transmission is a transmission where data flows in unpredictable bursts as opposed to a steady stream; gaps indicate delays between these bursts. This metric measures data flow between the client and the server.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**RelativeOneWayGapDensity** <br/> |float  <br/> ||Total one-way gap density. A "bursty" transmission is a transmission where data flows in unpredictable bursts as opposed to a steady stream; gaps indicate delays between these bursts. This metric measures data flow between the client and the server.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**RelativeOneWayGapDuration** <br/> |float  <br/> ||Total one-way gap duration. A "bursty" transmission is a transmission where data flows in unpredictable bursts as opposed to a steady stream; gaps indicate delays between these bursts. This metric measures data flow between the client and the server.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**VideoPacketLossRate** <br/> |decimal(9,4)  <br/> ||Rate at which video packets were lost.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**VideoAllocateBWAvg** <br/> |int  <br/> ||Average amount of bandwidth allocated for video.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**SendCodecTypes** <br/> |smallint  <br/> |Foreign  <br/> |Type of video codecs used by the sender. See the [CodecDescription table](codecdescription.md) for more information. <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**SendResolutionWidth** <br/> |int  <br/> ||Resolution width used by the sender.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**SendResolutionHeight** <br/> |int  <br/> ||Resolution height used by the sender.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**SendFrameRateAverage** <br/> |float  <br/> ||Average video frame rate transmission used by the sender.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**SendBitRateMaximum** <br/> |int  <br/> ||Maximum bit rate for the sender.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**SendBitRateAverage** <br/> |int  <br/> ||Average bit rate for the sender.  <br/> |
|**SendVideoStreamsMax** <br/> |int  <br/> ||Maximum number of video streams used by the sender.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**RecvCodecTypes** <br/> |smallint  <br/> |Foreign  <br/> |Video codes used by the receiver. See the [CodecDescription table](codecdescription.md) for more information. <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**RecvResolutionWidth** <br/> |int  <br/> ||Resolution width used by the receiver.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**RecvResolutionHeight** <br/> |int  <br/> ||Resolution height used by the receiver.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**RecvFrameRateAverage** <br/> |float  <br/> ||Average video frame rate used by the receiver.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**RecvBitRateMaximum** <br/> |int  <br/> ||Maximum bit rate for the receiver.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**RecvBitRateAverage** <br/> |int  <br/> ||Average bit rate for the receiver.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**RecvVideoStreamsMax** <br/> |int  <br/> ||Maximum video streams for the receiver.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**RecvVideoStreamsMin** <br/> |int  <br/> ||Minimum video streams for the receiver.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**RecvVideoStreamsMode** <br/> |int  <br/> ||Video mode (for example, gallery or single stream) for the receiver.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**VideoPostFECPLR** <br/> |float  <br/> ||Packet loss rate after forward error correction has been applied.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**DynamicCapabilityPercent** <br/> |float  <br/> ||Percentage of time that the dynamic capability flag was active.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**ResolutionMin** <br/> |char(9)  <br/> ||Minimum resolution measured during the call.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**LowBitRateCallPercent** <br/> |float  <br/> ||Percentage of the call below the low bit rate threshold (70 kilobits per second).  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**LowFrameRateCallPercent** <br/> |float  <br/> ||Percentage of the call below the low frame rate threshold (7.5 frames per second, inbound).  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**LowResolutionCallPercent** <br/> |float  <br/> ||Percentage of the call that occurred at the lowest resolution.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**DurationSeconds** <br/> |float  <br/> ||Length of the call in seconds.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**IsAggregatedData** <br/> |bit  <br/> ||Indicates whether the data has been aggregated from multiple calls.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
   

