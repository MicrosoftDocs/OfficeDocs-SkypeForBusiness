---
title: "AppSharingStream table"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 2/1/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 391490cb-d7b8-44ca-b4d1-429600da909c
description: "The AppSharingStream table contains Quality of Experience metrics for the network streams used for application sharing. This table was introduced in Microsoft Lync Server 2013."
---

# AppSharingStream table
 
The AppSharingStream table contains Quality of Experience metrics for the network streams used for application sharing. This table was introduced in Microsoft Lync Server 2013.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**ConferenceDateTime** <br/> |dateTime  <br/> |Primary, Foreign  <br/> |Date and time that the session started.  <br/> |
|**SessionSeq** <br/> |int  <br/> |Primary, Foreign  <br/> |Sequential identifier used to distinguish between sessions that started on the same date and at the same time.  <br/> |
|**MediaLineLabel** <br/> |tinyint  <br/> |Primary, Foreign  <br/> | See [MediaLine Table](https://docs.microsoft.com/skypeforbusiness/schema-reference/quality-of-experience-qoe-database-schema/medialine-0). <br/> |
|**StreamID** <br/> |int  <br/> |Primary  <br/> |Unique identifier of the application sharing stream.  <br/> |
|**JitterInterArrival** <br/> |int  <br/> ||Average jitter detected between RTP packet arrivals. (Jitter is a measure of the "shakiness" of a call.) High jitter values are typically caused by congestion or an overloaded media server, and result in distorted or lost audio.  <br/> |
|**JitterInterArrivalMax** <br/> |int  <br/> ||Maximum jitter detected between RTP packet arrivals. (Jitter is a measure of the "shakiness" of a call.) High jitter values are typically caused by congestion or an overloaded media server, and result in distorted or lost audio.  <br/> |
|**RoundTrip** <br/> |int  <br/> ||Average amount of (in milliseconds) required for a Real-Time Transport Protocol packet to travel to another endpoint and then back. Round-trip times of 200 milliseconds or less are considered of acceptable quality.  <br/> High round-trip values can be caused by international call routing; a routing misconfiguration; or an overloaded media server. High round-trip times result in difficulties with two-way, real-time audio conversations.  <br/> |
|**RoundTripMax** <br/> |int  <br/> ||Maximum amount of (in milliseconds) required for a Real-Time Transport Protocol packet to travel to another endpoint and then back. Round-trip times of 200 milliseconds or less are considered of acceptable quality.  <br/> High round-trip values can be caused by international call routing; a routing misconfiguration; or an overloaded media server. High round-trip times result in difficulties with two-way, real-time audio conversations.  <br/> |
|**PacketLossRate** <br/> |float  <br/> ||Average rate of Real-Time Transport Protocol (RTP) packet loss. (Packet loss occurs when RTP packets, a protocol used for transmitting audio and video across the Internet, failed to reach their destination.) High loss rates are generally caused by congestion; lack of bandwidth; wireless congestion or interference; or an overloaded media server. Packet loss typically results in distorted or lost audio.  <br/> |
|**PacketLossRateMax** <br/> |float  <br/> ||Maximum rate of Real-Time Transport Protocol (RTP) packet loss. (Packet loss occurs when RTP packets, a protocol used for transmitting audio and video across the Internet, failed to reach their destination.) High loss rates are generally caused by congestion; lack of bandwidth; wireless congestion or interference; or an overloaded media server. Packet loss typically results in distorted or lost audio.  <br/> |
|**PacketUtilization** <br/> |int  <br/> ||Number of packets sent.  <br/> |
|**BandwidthEst** <br/> |int  <br/> ||Estimated one-way bandwidth available at the end of the session. Reported in bits per second.  <br/> |
|**AppSharingPayloadDescription** <br/> |int  <br/> ||Description of the application sharing payload.  <br/> |
|**RelativeOneWayTotal** <br/> |float  <br/> ||Total amount of one-way latency. Relative one-way latency measures the delay between the client and the server.  <br/> |
|**RelativeOneWayAverage** <br/> |float  <br/> ||Average amount of one-way latency. Relative one-way latency measures the delay between the client and the server.  <br/> |
|**RelativeOneWayMax** <br/> |float  <br/> ||Maximum amount of one-way latency. Relative one-way latency measures the delay between the client and the server.  <br/> |
|**RelativeOneWayBurstOccurrences** <br/> |int  <br/> ||Total one-way burst occurrences. A "bursty" transmission is a transmission where data flows in unpredictable bursts as opposed to a steady stream. This metric measures data flow between the client and the server.  <br/> |
|**RelativeOneWayBurstDensity** <br/> |float  <br/> ||Total one-way burst density. A "bursty" transmission is a transmission where data flows in unpredictable bursts as opposed to a steady stream. This metric measures data flow between the client and the server.  <br/> |
|**RelativeOneWayBurstDuration** <br/> |float  <br/> ||Total one-way burst duration. A "bursty" transmission is a transmission where data flows in unpredictable bursts as opposed to a steady stream. This metric measures data flow between the client and the server.  <br/> |
|**RelativeOneWayGapOccurrences** <br/> |int  <br/> ||Total one-way gap occurrences. A "bursty" transmission is a transmission where data flows in unpredictable bursts as opposed to a steady stream; gaps indicate delays between these bursts. This metric measures data flow between the client and the server.  <br/> |
|**RelativeOneWayGapDensity** <br/> |float  <br/> ||Total one-way gap density. A "bursty" transmission is a transmission where data flows in unpredictable bursts as opposed to a steady stream; gaps indicate delays between these bursts. This metric measures data flow between the client and the server.  <br/> |
|**RelativeOneWayGapDuration** <br/> |float  <br/> ||Total one-way gap duration. A "bursty" transmission is a transmission where data flows in unpredictable bursts as opposed to a steady stream; gaps indicate delays between these bursts. This metric measures data flow between the client and the server.  <br/> |
|**ApplicationSharingType** <br/> |varChar(256)  <br/> ||Application role (Sharer or Viewer) and content type.  <br/> |
|**RDPTileProcessingLatencyTotal** <br/> |float  <br/> ||Total processing time for remote desktop protocol (RDP) tiles. A higher total equates to a longer delay in the viewing experience.  <br/> |
|**RDPTileProcessingLatencyAverage** <br/> |float  <br/> ||Average processing time for remote desktop protocol (RDP) tiles. A higher total equates to a longer delay in the viewing experience.  <br/> |
|**RDPTileProcessingLatencyMax** <br/> |float  <br/> ||Maximum processing time for remote desktop protocol (RDP) tiles. A higher total equates to a longer delay in the viewing experience.  <br/> |
|**RDPTileProcessingLatencyBurstOccurrences** <br/> |int  <br/> ||Burst occurrences in the processing time for remote desktop protocol (RDP) tiles. A "bursty" transmission is a transmission where data flows in unpredictable bursts as opposed to a steady stream.  <br/> |
|**RDPTileProcessingLatencyBurstDensity** <br/> |float  <br/> ||Burst density in the processing time for remote desktop protocol (RDP) tiles. A "bursty" transmission is a transmission where data flows in unpredictable bursts as opposed to a steady stream.  <br/> |
|**RDPTileProcessingLatencyBurstDuration** <br/> |float  <br/> ||Burst duration in the processing time for remote desktop protocol (RDP) tiles. A "bursty" transmission is a transmission where data flows in unpredictable bursts as opposed to a steady stream.  <br/> |
|**RDPTileProcessingLatencyGapOccurrences** <br/> |int  <br/> ||Gap occurrences in the processing time for remote desktop protocol (RDP) tiles.  <br/> |
|**RDPTileProcessingLatencyGapDensity** <br/> |float  <br/> ||Gap density in the processing time for remote desktop protocol (RDP) tiles. Low gap density equates to a better viewing experience.  <br/> |
|**RDPTileProcessingLatencyGapDuration** <br/> |float  <br/> ||Gap duration in the processing time for remote desktop protocol (RDP) tiles. Short gap durations equate to a better viewing experience.  <br/> |
|**CaptureTileRateTotal** <br/> |float  <br/> ||Total rate of captured tiles (in tiles per second).  <br/> |
|**CaptureTileRateAverage** <br/> |float  <br/> ||Average rate of captured tiles (in tiles per second).  <br/> |
|**CaptureTileRateMax** <br/> |float  <br/> ||Maximum rate of captured tiles (in tiles per second).  <br/> |
|**CaptureTileRateBurstOccurrences** <br/> |in t  <br/> ||Burst occurrences in the rate of captured tiles (in tiles per second).  <br/> |
|**CaptureTileRateBurstDensity** <br/> |float  <br/> ||Burst density in the rate of captured tiles (in tiles per second).  <br/> |
|**CaptureTileRateBurstDuration** <br/> |float  <br/> ||Burst duration in the rate of captured tiles (in tiles per second).  <br/> |
|**CaptureTileRateGapOccurrences** <br/> |int  <br/> ||Gap occurrences in the rate of captured tiles (in tiles per second).  <br/> |
|**CaptureTileRateGapDensity** <br/> |float  <br/> ||Gap density in the rate of captured tiles (in tiles per second).  <br/> |
|**CaptureTileRateGapDuration** <br/> |float  <br/> ||Gap duration in the rate of captured tiles (in tiles per second).  <br/> |
|**SpoiledTilePercentTotal** <br/> |float  <br/> ||Total percentage of the content that did not reach the viewer but was instead discarded and overwritten by fresh content.  <br/> |
|**SpoiledTilePercentAverage** <br/> |float  <br/> ||Average percentage of the content that did not reach the viewer but was instead discarded and overwritten by fresh content.  <br/> |
|**SpoiledTilePercentMax** <br/> |float  <br/> ||Maximum percentage of the content that did not reach the viewer but was instead discarded and overwritten by fresh content.  <br/> |
|**SpoiledTilePercentBurstOccurrences** <br/> |int  <br/> ||Burst occurrences for the content that did not reach the viewer but was instead discarded and overwritten by fresh content.  <br/> |
|**SpoiledTilePercentBurstDensity** <br/> |float  <br/> ||Burst density for the content that did not reach the viewer but was instead discarded and overwritten by fresh content.  <br/> |
|**SpoiledTilePercentBurstDuration** <br/> |float  <br/> ||Burst duration for the content that did not reach the viewer but was instead discarded and overwritten by fresh content.  <br/> |
|**SpoiledTilePercentGapOccurrences** <br/> |int  <br/> ||Gap occurrences for the content that did not reach the viewer but was instead discarded and overwritten by fresh content.  <br/> |
|**SpoiledTilePercentGapDensity** <br/> |float  <br/> ||Gap density for the content that did not reach the viewer but was instead discarded and overwritten by fresh content.  <br/> |
|**SpoiledTilePercentGapDuration** <br/> |float  <br/> ||Gap duration for the content that did not reach the viewer but was instead discarded and overwritten by fresh content.  <br/> |
|**ScrapingFrameRateTotal** <br/> |float  <br/> ||Total number of frames scraped from the graphics source.  <br/> |
|**ScrapingFrameRateAverage** <br/> |float  <br/> ||Average number of frames scraped from the graphics source.  <br/> |
|**ScrapingFrameRateMax** <br/> |float  <br/> ||Maximum number of frames scraped from the graphics source.  <br/> |
|**ScrapingFrameRateBurstOccurrences** <br/> |int  <br/> ||Burst occurrences in the frames scraped from the graphics source.  <br/> |
|**ScrapingFrameRateBurstDensity** <br/> |float  <br/> ||Burst density in the frames scraped from the graphics source.  <br/> |
|**ScrapingFrameRateBurstDuration** <br/> |float  <br/> ||Burst duration in the frames scraped from the graphics source.  <br/> |
|**ScrapingFrameRateGapOccurrences** <br/> |int  <br/> ||Gap occurrences in the frames scraped from the graphics source.  <br/> |
|**ScrapingFrameRateGapDensity** <br/> |float  <br/> ||Gap density in the frames scraped from the graphics source.  <br/> |
|**ScrapingFrameRateGapDuration** <br/> |float  <br/> ||Gap duration in the frames scraped from the graphics source.  <br/> |
|**IncomingTileRateTotal** <br/> |float  <br/> ||Total incoming frame rate as received by the viewer.  <br/> |
|**IncomingTileRateAverage** <br/> |float  <br/> ||Average incoming frame rate as received by the viewer.  <br/> |
|**IncomingTileRateMax** <br/> |float  <br/> ||Maximum incoming tile rate as received by the viewer.  <br/> |
|**IncomingTileRateBurstOccurrences** <br/> |int  <br/> ||Burst occurrences in the incoming tile rate as received by the viewer.  <br/> |
|**IncomingTileRateBurstDensity** <br/> |float  <br/> ||Burst density in the incoming tile rate as received by the viewer.  <br/> |
|**IncomingTileRateBurstDuration** <br/> |float  <br/> ||Burst duration in the incoming tile rate as received by the viewer.  <br/> |
|**IncomingTileRateGapOccurrences** <br/> |int  <br/> ||Gap occurrences in the incoming tile rate as received by the viewer.  <br/> |
|**IncomingTileRateGapDensity** <br/> |float  <br/> ||Gap density in the incoming tile rate as received by the viewer.  <br/> |
|**IncomingTileRateGapDuration** <br/> |float  <br/> ||Gap duration in the incoming tile rate as received by the viewer.  <br/> |
|**IncomingFrameRateTotal** <br/> |float  <br/> ||Total incoming frame rate as received by the viewer.  <br/> |
|**IncomingFrameRateAverage** <br/> |float  <br/> ||Average incoming frame rate as received by the viewer.  <br/> |
|**IncomingFrameRateMax** <br/> |float  <br/> ||Maximum incoming frame rate as received by the viewer.  <br/> |
|**IncomingFrameRateBurstOccurrences** <br/> |int  <br/> ||Burst occurrences in the incoming frame rate as received by the viewer.  <br/> |
|**IncomingFrameRateBurstDensity** <br/> |float  <br/> ||Burst density in the incoming frame rate as received by the viewer.  <br/> |
|**IncomingFrameRateBurstDuration** <br/> |float  <br/> ||Burst duration in the incoming frame rate as received by the viewer.  <br/> |
|**IncomingFrameRateGapOccurrences** <br/> |int  <br/> ||Gap occurrences in the incoming frame rate as received by the viewer.  <br/> |
|**IncomingFrameRateGapDensity** <br/> |float  <br/> ||Gap density in the incoming frame rate as received by the viewer.  <br/> |
|**IncomingFrameRateDuration** <br/> |float  <br/> ||Gap duration in the incoming frame rate as received by the viewer.  <br/> |
|**OutgoingTileRateTotal** <br/> |float  <br/> ||Total outgoing tile rate for the sender.  <br/> |
|**OutgoingTileRateAverage** <br/> |float  <br/> ||Average outgoing tile rate for the sender.  <br/> |
|**OutgoingTileRateMax** <br/> |float  <br/> ||Maximum outgoing tile rate for the sender.  <br/> |
|**OutgoingTileRateBurstOccurrences** <br/> |int  <br/> ||Burst occurrences in the outgoing tile rate for the sender.  <br/> |
|**OutgoingTileRateBurstDensity** <br/> |float  <br/> ||Burst density in the outgoing tile rate for the sender.  <br/> |
|**OutgoingTileRateBurstDuration** <br/> |float  <br/> ||Burst duration in the outgoing tile rate for the sender.  <br/> |
|**OutgoingTileRateGapOccurrences** <br/> |int  <br/> ||Gap occurrences in the outgoing tile rate for the sender.  <br/> |
|**OutgoingTileRateGapDensity** <br/> |float  <br/> ||Gap density in the outgoing tile rate for the sender.  <br/> |
|**OutgoingTileRateGapDuration** <br/> |float  <br/> ||Gap duration in the outgoing tile rate for the sender.  <br/> |
|**OutgoingFrameRateTotal** <br/> |float  <br/> ||Total outgoing frame rate for the sender.  <br/> |
|**OutgoingFrameRateAverage** <br/> |float  <br/> ||average outgoing frame rate for the sender.  <br/> |
|**OutgoingFrameRateMax** <br/> |float  <br/> ||Maximum outgoing frame rate for the sender.  <br/> |
|**OutgoingFrameRateBurstOccurrences** <br/> |int  <br/> ||Burst occurrences in the outgoing frame rate for the sender.  <br/> |
|**OutgoingFrameRateBurstDensity** <br/> |float  <br/> ||Burst density in the outgoing frame rate for the sender.  <br/> |
|**OutgoingFrameRateBurstDuration** <br/> |float  <br/> ||Burst duration in the outgoing frame rate for the sender.  <br/> |
|**OutgoingFrameRateGapOccurrences** <br/> |int  <br/> ||Gap occurrences in the outgoing frame rate for the sender.  <br/> |
|**OutgoingFrameRateGapDensity** <br/> |float  <br/> ||Gap density in the outgoing frame rate for the sender.  <br/> |
|**OutgoingFrameRateGapDuration** <br/> |float  <br/> ||Gap duration in the outgoing frame rate for the sender.  <br/> |
|**AverageRectangleHeight** <br/> |int  <br/> ||Average video resolution height, in pixels.  <br/> |
|**AverageRectangleWidth** <br/> |int  <br/> ||Average video resolution width, in pixels.  <br/> |
|**Inbound** <br/> |bit  <br/> ||Average frame rate (in frames per second) for inbound transmissions.  <br/> |
|**Outbound** <br/> |bit  <br/> ||Average frame rate (in frames per second) for outbound transmissions.  <br/> |
|**SenderIsCallerPAI** <br/> |bit  <br/> ||1 means the stream direction is from the caller to callee.  <br/> 0 means the stream direction is from the callee to the caller.  <br/> |
   

