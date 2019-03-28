---
title: "VideoStreamDetail view"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: ec8c45e1-307d-40ec-a75e-6083306105f2
description: "The VideoStreamDetail View stores information about each video stream in the database. This view was introduced in Microsoft Lync Server 2013."
---

# VideoStreamDetail view
 
The VideoStreamDetail View stores information about each video stream in the database. This view was introduced in Microsoft Lync Server 2013.
  
|**Column**|**Data Type**|**Description**|
|:-----|:-----|:-----|
|SessionTime  <br/> |datetime  <br/> |Referenced from the [MediaLine table](medialine-0.md).  <br/> |
|SessionSeq  <br/> |int  <br/> |Referenced from the [MediaLine table](medialine-0.md).  <br/> |
|MediaLineLabel  <br/> |tinyint  <br/> |Referenced from the [MediaLine table](medialine-0.md).  <br/> |
|StreamId  <br/> |int  <br/> |Unique ID within a media line.  <br/> |
|StartTime  <br/> |datetime  <br/> |Start time of the session.  <br/> |
|EndTime  <br/> |datetime  <br/> |End time of the session.  <br/> |
|CallPriority  <br/> |int  <br/> |Priority of the call.  <br/> |
|CallerPool  <br/> |nvarchar(256)  <br/> |Caller pool FQDN.  <br/> |
|CalleePool  <br/> |nvarchar(256)  <br/> |Callee pool FQDN.  <br/> |
|Caller  <br/> |nvarchar(450)  <br/> |Caller's URI.  <br/> |
|Callee  <br/> |nvarchar(450)  <br/> |Callee's URI.  <br/> |
|CallerUserAgent  <br/> |nvarchar(256)  <br/> |Caller's user agent string.  <br/> |
|CallerUserAgentType  <br/> |smallint  <br/> |Type of caller's user agent. See the [UserAgent table](useragent.md) for details. <br/> |
|CallerUserAgentCategory  <br/> |nvarchar(64)  <br/> |Category of caller's user agent. See the [UserAgentDef table (QoE)](useragentdef-qoe.md) for details. <br/> |
|CalleeUserAgent  <br/> |nvarchar(256)  <br/> |Callee's user agent string.  <br/> |
|CalleeUserAgentType  <br/> |smallint  <br/> |Type of callee's user agent. See the [UserAgent table](useragent.md) for information. <br/> |
|CalleeUserAgentCategory  <br/> |nvarchar(64)  <br/> |Category of callee's user agent. See the [UserAgentDef table (QoE)](useragentdef-qoe.md) for information. <br/> |
|CallerEndpoint  <br/> |nvarchar(256)  <br/> |Caller's endpoint name.  <br/> |
|CalleeEndpoint  <br/> |nvarchar(256)  <br/> |Callee's endpoint name.  <br/> |
|CallerOS  <br/> |nvarchar(128)  <br/> |Operating system (OS) of the caller's endpoint.  <br/> |
|CalleeOS  <br/> |nvarchar(128)  <br/> |Operating system (OS) of the callee's endpoint.  <br/> |
|CallerCPUName  <br/> |nvarchar(128)  <br/> |CPU name of the caller's endpoint.  <br/> |
|CalleeCPUName  <br/> |nvarchar(128)  <br/> |CPU name of the callee's endpoint.  <br/> |
|CallerCPUNumberOfCores  <br/> |smallint  <br/> |Number of CPU cores of the caller's endpoint.  <br/> |
|CalleeCPUNumberOfCores  <br/> |smallint  <br/> |Number of CPU cores of the callee's endpoint.  <br/> |
|CallerCPUProcessorSpeed  <br/> |int  <br/> |CPU processor speed of the caller's endpoint.  <br/> |
|CalleeCPUProcessorSpeed  <br/> |int  <br/> |CPU processor speed of the callee's endpoint.  <br/> |
|CallerVirtualizationFlag  <br/> |tinyint  <br/> |Indicates whether the caller's system is running in a virtualized environment. See the [Endpoint table](endpoint.md) for more information. <br/> |
|CalleeVirtualizationFlag  <br/> |tinyint  <br/> |Indicates whether the callee's system is running in a virtualized environment. See the [Endpoint table](endpoint.md) for more information. <br/> |
|ConnectivityIce  <br/> |tinyint  <br/> |Information about media path, such as direct or relayed. See the [MediaLine table](medialine-0.md) for more information. <br/> |
|CallerIceWarningFlags  <br/> |int  <br/> |Information about Interactive Connectivity Establishment (ICE) process described in bits flags for the caller. For details, refer to the Quality of Experience Monitoring Server Protocol Specification.  <br/> |
|CalleeIceWarningFlags  <br/> |int  <br/> |Information about Interactive Connectivity Establishment (ICE) process described in bits flags for the callee. For details, refer to the Quality of Experience Monitoring Server Protocol Specification.  <br/> |
|Transport  <br/> |int  <br/> |Transport type: 0 is UDP, 1 is TCP.  <br/> |
|CallerIPAddr  <br/> |var(50)  <br/> |IP address of the caller. This may be either an IPv4 or an IPv6 address.  <br/> |
|CallerPort  <br/> |int  <br/> |Port used by the caller.  <br/> |
|CallerInside  <br/> |bit  <br/> |Indicates whether the caller is inside the organization network. 1 means caller is inside the enterprise network, 0 means the caller is outside the network.  <br/> |
|CalleeIPAddr  <br/> |var(50)  <br/> |IP address of the callee. This may be either an IPv4 or an IPv6 address.  <br/> |
|CalleePort  <br/> |int  <br/> |Port used by the callee.  <br/> |
|CalleeInside  <br/> |bit  <br/> |Indicates whether the caller is inside the organization network.1 means callee is inside the enterprise network, 0 means the callee is outside the network.  <br/> |
|CallerUserSite  <br/> |nvarchar(128)  <br/> |Name of the caller's site.  <br/> |
|CallerRegion  <br/> |nvarchar(128)  <br/> |Name of the country/region of the caller's site.  <br/> |
|CalleeUserSite  <br/> |nvarchar(128)  <br/> |Name of the callee's site.  <br/> |
|CalleeRegion  <br/> |nvarchar(128)  <br/> |Name of the country/region of the callee's site.  <br/> |
|CallerRelayIPAddr  <br/> |var(50)  <br/> |IP Address of the A/V Edge service used by the caller. See the [IPAddress table](ipaddress.md) for more information. <br/> |
|CallerRelayPort  <br/> |int  <br/> |Port on the A/V Edge service used by the caller.  <br/> |
|CalleeRelayIPAddr  <br/> |var(50)  <br/> |IP Address key of the A/V Edge service used by the callee. See the [IPAddress table](ipaddress.md) for more information. <br/> |
|CalleeRelayPort  <br/> |int  <br/> |Port on the A/V Edge service used by the callee.  <br/> |
|CallerCaptureDev  <br/> |varchar(256)  <br/> |Caller's capture device name.  <br/> |
|CallerRenderDev  <br/> |varchar(256)  <br/> |Caller's render device name.  <br/> |
|CallerCaptureDevDriver  <br/> |varchar(256)  <br/> |Caller's capture device driver name.  <br/> |
|CallerRenderDevDriver  <br/> |varchar(256)  <br/> |Caller's render device driver name.  <br/> |
|CalleeCaptureDev  <br/> |varchar(256)  <br/> |Callee's capture device name.  <br/> |
|CalleeRenderDev  <br/> |varchar(256)  <br/> |Callee's render device name.  <br/> |
|CalleCaptureDevDriver  <br/> |varchar(256)  <br/> |Callee's capture device driver name.  <br/> |
|CalleeRenderDevDriver  <br/> |varchar(256)  <br/> |Callee's render device driver name.  <br/> |
|CallerNetworkConnectionType  <br/> |tinyint  <br/> |Caller's network connection type: 0 is wired, 1 is wireless.  <br/> |
|CallerVPN  <br/> |bit  <br/> |Indicates whether or not the caller connected over a virtual private network. 1 is virtual private network (VPN), 0 is non-VPN.  <br/> |
|CallerLinkSpeed  <br/> |decimal(18,)  <br/> |Network link speed for the caller's endpoint in bps.  <br/> |
|CalleeNetworkConnectionType  <br/> |tinyint  <br/> |Callee's network connection type: 0 is wired, 1 is wireless.  <br/> |
|CalleeVPN  <br/> |bit  <br/> |Indicates whether or not the callee connected over a virtual private network. 1 is virtual private network (VPN), 0 is non-VPN.  <br/> |
|CalleeLinkSpeed  <br/> |decimal(18,0)  <br/> |Network link speed for the callee's endpoint (in bps).  <br/> |
|ConversationalMOS  <br/> |decimal(3,2)  <br/> |Narrowband Conversational MOS of the audio sessions (based on both audio streams).  <br/> |
|AppliedBandwidthLimit  <br/> |int  <br/> |Actual bandwidth applied to the given send side stream given various policy settings (TURN, API, SDP, Policy Server, and so on). This is not to be confused with the effective bandwidth because there can be a lower effective bandwidth based on the bandwidth estimate. This is basically the maximum bandwidth the send stream can take barring limits imposed by the bandwidth estimate.  <br/> |
|JitterInterArrival  <br/> |int  <br/> |Average network jitter from Real Time Control Protocol (RTCP) statistics.  <br/> |
|JitterInterArrivalMax  <br/> |int  <br/> |Maximum network jitter during the call.  <br/> |
|RoundTrip  <br/> |int  <br/> |Round trip time from RTCP statistics.  <br/> |
|RoundTripMax  <br/> |int  <br/> |Maximum round trip time for the audio stream.  <br/> |
|PacketLossRate  <br/> |decimal(5,4)  <br/> |Average packet loss rate during the call.  <br/> |
|PacketLossRateMax  <br/> |decimal(5,4)  <br/> |Maximum packet loss observed during the call.  <br/> |
|PacketUtilization  <br/> |int  <br/> |Packet count for the video stream (Real Time Transport Protocol, RTP).  <br/> |
|BandwidthEst  <br/> |int  <br/> |Bandwidth estimates for the audio stream.  <br/> |
|PayloadDescription  <br/> |int  <br/> |Audio codec used for the call, referenced from the [PayloadDescription table](payloaddescription.md).  <br/> |
|VideoResolution  <br/> |char(9)  <br/> |Resolution of the video in pixels width multiplied by pixels height. Reported as a string.  <br/> |
|VideoBitRateAvg  <br/> |int  <br/> |Average bit rate of the video stream.  <br/> |
|InboundVideoFrameRateAvg  <br/> |decimal(9,4)  <br/> |Frame rate of video received.  <br/> |
|OutboundVideoFrameRateAvg  <br/> |decimal(9,4)  <br/> |Frame rate of video sent.  <br/> |
|ViideoBitRateMax  <br/> |int  <br/> |Maximum video bit rate during the video session.  <br/> |
|VideoPacketLossRate  <br/> |decimal(9,4)  <br/> |Rate at which video packets were lost.  <br/> |
|VideoFrameLossRate  <br/> |decimal(9.4)  <br/> |Percentage of total video frames that are lost.  <br/> |
|VideoFEC  <br/> |bit  <br/> |Not used.  <br/> |
|VideoAllocateBWAvg  <br/> |int  <br/> |Average amount of bandwidth allocated for video.  <br/> |
|VideoLocalFrameLossPercentageAvg  <br/> |decimal(9.4)  <br/> |Percentage of total video frames that were lost.  <br/> |
|SenderIsCallerPAI  <br/> |bit  <br/> |Stream direction for p-asserted identity information. 1 means the stream direction is from the caller to the callee; 0 means the stream direction is from the callee to the caller.  <br/> |
   

