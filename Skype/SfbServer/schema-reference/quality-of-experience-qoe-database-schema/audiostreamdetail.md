---
title: "AudioStreamDetail view"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 10/20/2015
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: b6a435b3-103c-41c4-96ed-33c3784534c0
description: "The AudioStreamDetail View stores information about each audio stream in the database. This view was introduced in Microsoft Lync Server 2013."
---

# AudioStreamDetail view
 
The AudioStreamDetail View stores information about each audio stream in the database. This view was introduced in Microsoft Lync Server 2013.
  
|**Column**|**Data Type**|**Details**|
|:-----|:-----|:-----|
|SessionTime  <br/> |datetime  <br/> |Referenced from the [MediaLine table](medialine-0.md).  <br/> |
|SessionSeq  <br/> |int  <br/> |Referenced from the [MediaLine table](medialine-0.md).  <br/> |
|StreamId  <br/> |int  <br/> |Unique ID within a media line.  <br/> |
|StartTime  <br/> |datetime  <br/> |Start time of the session.  <br/> |
|EndTime  <br/> |datetime  <br/> |End time of the session.  <br/> |
|DialogCategory  <br/> |bit  <br/> |Dialog category: 0 is the Skype for Business Server to Mediation Server leg; 1 is the Mediation Server to PSTN gateway leg.  <br/> |
|MediationServerBypassFlag  <br/> |bit  <br/> |Flag indicating if the call was bypassed or not.  <br/> |
|MediaBypassWarningFlag  <br/> |int  <br/> |If present, indicates why a call was not bypassed even if the bypass IDs matched. Only one value is defined:  <br/> 0x0001 - Unknown bypass ID for Default network adapter.  <br/> |
|CallPriority  <br/> |int  <br/> |Priority of the call.  <br/> |
|CallerPool  <br/> |nvarchar(256)  <br/> |Caller pool FQDN.  <br/> |
|CalleePool  <br/> |nvarchar(256)  <br/> |Callee pool FQDN.  <br/> |
|Caller  <br/> |nvarchar(450)  <br/> |Caller's URI.  <br/> |
|Callee  <br/> |nvarchar(450)  <br/> |Callee's URI.  <br/> |
|CallerUserAgent  <br/> |nvarchar(256)  <br/> |Caller's user agent string.  <br/> |
|CallerUserAgentType  <br/> |smallint  <br/> |Type of the caller's user agent. See the [UserAgent table](useragent.md) for details. <br/> |
|CallerUserAgentCategory  <br/> |nvarchar(64)  <br/> |Category of the caller's user agent. See the [UserAgentDef table (QoE)](useragentdef-qoe.md) for details. <br/> |
|CalleeUserAgent  <br/> |nvarchar(256)  <br/> |Callee's user agent string.  <br/> |
|CalleeUserAgentType  <br/> |smallint  <br/> |Type of callee's user agent. See the [UserAgent table](useragent.md) for information. <br/> |
|CalleeUserAgentCategory  <br/> |nvarchar(64)  <br/> |Category of callee's user agent. See the [UserAgentDef table (QoE)](useragentdef-qoe.md) for information. <br/> |
|CallerEndpoint  <br/> |nvarchar(256)  <br/> |Caller's endpoint name.  <br/> |
|CalleeEndpoint  <br/> |nvarchar(256)  <br/> |Callee's endpoint name.  <br/> |
|CallerOS  <br/> |nvarchar(128)  <br/> |Operating system (OS) of the caller's endpoint.  <br/> |
|CalleeOS  <br/> |nvarchar(128)  <br/> |Operating system (OS) of the callee's endpoint.  <br/> |
|CallerCPUName  <br/> |nvarchar(128)  <br/> |CPU name of the caller's endpoint.  <br/> |
|CalleeCPUName  <br/> |nvarchar(128)  <br/> |CPU name of the callee's endpoint.  <br/> |
|CallerCPUNumberOfCores  <br/> |smallint  <br/> |Number of CPU cores in the caller's endpoint.  <br/> |
|CalleeCPUNumberOfCores  <br/> |smallint  <br/> |Number of CPU cores in the callee's endpoint.  <br/> |
|CallerCPUProcessorSpeed  <br/> |int  <br/> |CPU processor speed of the caller's endpoint.  <br/> |
|CalleeCPUProcessorSpeed  <br/> |int  <br/> |CPU processor speed of the callee's endpoint.  <br/> |
|CallerVirtualizationFlag  <br/> |tinyint  <br/> |Indicates whether the caller's system is running in a virtualized environment. See the [Endpoint table](endpoint.md) for more information. <br/> |
|CalleeVirtualizationFlag  <br/> |tinyint  <br/> |Indicates whether the callee's system is running in a virtualized environment. See the [Endpoint table](endpoint.md) for more information. <br/> |
|CorrelationKey  <br/> ||Correlation key. Referenced from the [SessionCorrelation table](sessioncorrelation.md).  <br/> |
|ConnectivityIce  <br/> |tinyint  <br/> |Information about the media path, such as direct or relayed. See the [MediaLine table](medialine-0.md) for more information. <br/> |
|CallerIceWarningFlags  <br/> |int  <br/> |Information about Interactive Connectivity Establishment (ICE) process described in bits flags for the caller. For details, refer to the Quality of Experience Monitoring Server Protocol Specification.  <br/> |
|CalleeIceWarningFlags  <br/> |int  <br/> |Information about Interactive Connectivity Establishment (ICE) process described in bits flags for the callee. For details, refer to the Quality of Experience Monitoring Server Protocol Specification.  <br/> |
|Transport  <br/> |tinyint  <br/> |Transport type: 0 is UDP, 1 is TCP.  <br/> |
|CallerIPAddr  <br/> |var(50)  <br/> |IP address of the caller. This may be either an IPv4 or an IPv6 address.  <br/> |
|CallerPort  <br/> |int  <br/> |Port used by the caller.  <br/> |
|CallerInside  <br/> |bit  <br/> |Indicates whether the caller is inside the interval network: 1 means caller is inside the enterprise network, 0 means the caller is outside the network.  <br/> |
|CalleeIPAddr  <br/> |var(50)  <br/> |IP address of the callee. This may be either an IPv4 or an IPv6 address.  <br/> |
|CalleePort  <br/> |int  <br/> |Port used by the callee.  <br/> |
|CalleeInside  <br/> |bit  <br/> |Indicates whether the callee is inside the interval network: 1 means callee is inside the enterprise network, 0 means the callee is outside the network.  <br/> |
|CallerUserSite  <br/> |nvarchar(128)  <br/> |Name of the caller's site.  <br/> |
|CallerRegion  <br/> |nvarchar(128)  <br/> |Name of the country/region of the caller's site.  <br/> |
|CalleeUserSite  <br/> |nvarchar(128)  <br/> |Name of the callee's site.  <br/> |
|CalleeRegion  <br/> |nvarchar(128)  <br/> |Name of the country/region of the callee's site.  <br/> |
|CallerRelayIPAddr  <br/> |var(50)  <br/> |IP Address of the A/V Edge service used by the caller. See the [IPAddress table](ipaddress.md) for more information. <br/> |
|CallerRelayPort  <br/> |int  <br/> |Port used on the A/V Edge service used by the caller.  <br/> |
|CalleeRelayIPAddr  <br/> |var(50)  <br/> |IP Address key of the A/V Edge service used by the callee. See the [IPAddress table](ipaddress.md) for more information. <br/> |
|CalleeRelayPort  <br/> |int  <br/> |Port used on the A/V Edge service used by the callee.  <br/> |
|CallerCaptureDev  <br/> |varchar(256)  <br/> |Caller's capture device name.  <br/> |
|CallerRenderDev  <br/> |varchar(256)  <br/> |Caller's render device name.  <br/> |
|CallerCaptureDevDriver  <br/> |varchar(256)  <br/> |Caller's capture device driver name.  <br/> |
|CallerRenderDriver  <br/> |varchar(256)  <br/> |Caller's render device driver name.  <br/> |
|CalleeCaptureDev  <br/> |varchar(256)  <br/> |Callee's capture device name.  <br/> |
|CalleeRenderDev  <br/> |varchar(256)  <br/> |Callee's render device name.  <br/> |
|CalleeCaptureDevDriver  <br/> |varchar(256)  <br/> |Callee's capture device driver name.  <br/> |
|CalleeRenderDevDriver  <br/> |varchar(256)  <br/> |Callee's render device driver name.  <br/> |
|CallerNetworkConnectionType  <br/> |tinyint  <br/> |Caller's network connection type: 0 is wired, 1 is wireless.  <br/> |
|CallerVPN  <br/> |bit  <br/> |Indicates whether the caller connected over a virtual private network: 1 is virtual private network (VPN), 0 is non-VPN.  <br/> |
|CallerLinkSpeed  <br/> |decimal(18,0)  <br/> |Network link speed for the caller's endpoint in bps.  <br/> |
|CalleeNetworkConnectionType  <br/> |tinyint  <br/> |Callee's network connection type: 0 is wired, 1 is wireless.  <br/> |
|CalleeVPN  <br/> |bit  <br/> |Indicates whether the caller connected over a virtual private network: 1 is virtual private network (VPN), 0 is non-VPN.  <br/> |
|CalleeLinkSpeed  <br/> |decimal(18,0)  <br/> |Network link speed for the callee's endpoint in bps.  <br/> |
|ConversationalMOS  <br/> |decimal(3,2)  <br/> |Narrowband Conversational MOS of the audio sessions (based on both audio streams).  <br/> |
|AppliedBandwidthLimit  <br/> |int  <br/> |Actual bandwidth applied to the given send side stream given various policy settings (TURN, API, SDP, Policy Server, and so on). This is not to be confused with the effective bandwidth because there can be a lower effective bandwidth based on the bandwidth estimate. This is basically the maximum bandwidth the send stream can take barring limits imposed by the bandwidth estimate  <br/> |
|JitterInterArrival  <br/> |int  <br/> |Average network jitter from Real Time Control Protocol (RTCP) statistics.  <br/> |
|JitterInterArrivalMax  <br/> |int  <br/> |Maximum network jitter during the call.  <br/> |
|PacketLossRate  <br/> |decimal(5,4)  <br/> |Average packet loss rate during the call.  <br/> |
|PacketLossRateMax  <br/> |decimal(5,4)  <br/> |Maximum packet loss observed during the call.  <br/> |
|BurstDensity  <br/> |decimal(9,4)  <br/> |Average density of packet loss during bursts of losses during the call.  <br/> |
|BurstDuration  <br/> |int  <br/> |Average duration of packet loss during bursts of losses during the call.  <br/> |
|BurstGapDensity  <br/> |decimal(9,4)  <br/> |Average density of packet loss during gaps between bursts of packet loss.  <br/> |
|BurstGapDuration  <br/> |int  <br/> |Average duration of gaps between bursts of packet loss.  <br/> |
|PacketUtilization  <br/> |int  <br/> |Packet count for the audio stream.  <br/> |
|BandwidthEst  <br/> |int  <br/> |Bandwidth estimates for the audio stream.  <br/> |
|DegradationAvg  <br/> |decimal(3,2)  <br/> |Network MOS Degradation for the whole call. Range is 0.0 to 5.0. This metric shows the amount the Network MOS was reduced because of jitter and packet loss. For acceptable quality it should less than 0.5.  <br/> |
|DegradationMax  <br/> |decimal(3,2)  <br/> |Maximum Network MOS degradation during the call.  <br/> |
|DegradationJitterAvg  <br/> |decimal(3,2)  <br/> |Network MOS degradation caused by jitter.  <br/> |
|DegradationPacketLossAvg  <br/> |decimal(3,2)  <br/> |Network MOS degradation caused by packet loss.  <br/> |
|PayloadDescription  <br/> |int  <br/> |The audio codec used for the call, referenced from the [PayloadDescription table](payloaddescription.md).  <br/> |
|AudioSampleRate  <br/> |int  <br/> |Sampling rate for the audio stream.  <br/> |
|CallerSendSignalLevel  <br/> |int  <br/> |Post-Analog Gain Control audio signal level for the audio the caller sent. The unit for this metric is dBmo. For acceptable quality, it should be at least 30 dBmo. This metric is not reported by the A/V Conferencing Server or IP phones.  <br/> |
|CallerRecvSignalLevel  <br/> |int  <br/> |Audio signal level for the audio the caller received. The unit for this metric is dBmo. For acceptable quality, it should be at least 30 dBmo. This metric is not reported by the A/V Conferencing Server or IP phones.  <br/> |
|CallerSendNoiseLevel  <br/> |int  <br/> |Post-Analog Gain Control audio noise level for the audio the caller sent. The unit for this metric is dBmo. For acceptable quality, it should be less than 35 dBmo. This metric is not reported by the A/V Conferencing Server or IP phones.  <br/> |
|CallerRecvNoiseLevel  <br/> |int  <br/> |Post-Analog Gain Control audio noise level for the audio the caller received. The unit for this metric is dBmo. For acceptable quality, it should be less than 35 dBmo. This metric is not reported by the A/V Conferencing Server or IP phones.  <br/> |
|CallerEchoReturn  <br/> |int  <br/> |Echo Return Loss Enhancement for the caller. The unit for this metric is dB. Lower values represent less echo. This metric is not reported by the A/V Conferencing Server or IP phones.  <br/> |
|CallerSpeakerGlitchRate  <br/> |int  <br/> |Average glitches per five minutes for the caller's loudspeaker rendering. For good quality, this should be less than one per five minutes. Not reported by A/V Conferencing Servers, Mediation Servers, or IP phones.  <br/> |
|CallerMicGlitchRate  <br/> |int  <br/> |Average glitches per five minutes for the caller's microphone capture. For good quality this should be less than one per five minutes. Not reported by A/V Conferencing Servers, Mediation Servers, or IP phones.  <br/> |
|CallerTimestampDriftRateMic  <br/> |decimal(9,2)  <br/> |Caller's microphone device clock drift rate, relative to CPU clock.  <br/> |
|CallerTimestampDriftRateSpk  <br/> |decimal(9,2)  <br/> |Caller's speaker device clock drift rate, relative to CPU clock.  <br/> |
|CallerTimestampErrorMicMs  <br/> |decimal(9,2)  <br/> |Average microphone capture stream time stamp error, in milliseconds, in the last 20 seconds of the call.  <br/> |
|CallerTimestampErrorSpkMs  <br/> |decimal(9,2)  <br/> |Average of the caller's speaker render stream time stamp error, in milliseconds, in the last 20 seconds of the call.  <br/> |
|CallerVsEntryCauses  <br/> |smallint  <br/> |Voice switch is a half-duplex mode with reduced interruption ability. See the [MediaLine table](medialine-0.md) for more information. <br/> |
|CallerEchoEventCauses  <br/> |tinyint  <br/> |Causes of an echo event for the caller. See the [MediaLine table](medialine-0.md) for more information. <br/> |
|CallerEchoPercentMicIn  <br/> |decimal(5,2)  <br/> |Percentage of time when echo is detected in the caller's microphone capture stream. If headset is used, the value should be low.  <br/> |
|CallerEchoPercentSend  <br/> |decimal(5,2)  <br/> |Percentage of time when echo is detected in the caller's sent stream. High echo percentage in send streams an indication of echo leak.  <br/> |
|CallerRxAGCSignalLevel  <br/> |int  <br/> |Received signal level on the Mediation Server from the Gateway for the caller's audio; this applies only to the Mediation Server. The unit of this metric is dBoV. For good quality, the acceptable range should be -30 to -18 dBoV.  <br/> |
|CallerRxAGCNoiseLevel  <br/> |int  <br/> |Received signal level on the Mediation Server from the Gateway for the caller's audio. This applies only to the Mediation Server. The unit of this metric is dBoV. For good quality, the acceptable range should be less than -50 dBoV.  <br/> |
|CallerRxAGCGain  <br/> |int  <br/> |Automatic gain control (AGC) on the Mediation Server side applied to the caller's audio.  <br/> |
|CallerInitialSignalLevelRMS  <br/> |float  <br/> |Root mean square (RMS) of the incoming signal to the caller for up to the first 30 seconds of the call.  <br/> |
|CalleeSendSignalLevel  <br/> |int  <br/> |Represents the Post-Analog Gain Control audio signal level for the audio the callee sent. The unit for this metric is dBmo. For acceptable quality, it should be at least 30 dBmo. This metric is not reported by the A/V Conferencing Server or IP phones.  <br/> |
|CalleeRecvSignalLevel  <br/> |int  <br/> |Audio signal level for the audio the callee received. The unit for this metric is dBmo. For acceptable quality, it should be at least 30 dBmo. This metric is not reported by the A/V Conferencing Server or IP phones.  <br/> |
|CalleeSendNoiseLevel  <br/> |int  <br/> |Post-Analog Gain Control audio noise level for the audio the callee sent. The unit for this metric is dBmo. For acceptable quality, it should be less than 35 dBmo. This metric is not reported by the A/V Conferencing Server or IP phones.  <br/> |
|CalleeRecvNoiseLevel  <br/> |int  <br/> |Post-Analog Gain Control audio noise level for the audio the callee received. The unit for this metric is dBmo. For acceptable quality, it should be less than 35 dBmo. This metric is not reported by the A/V Conferencing Server or IP phones.  <br/> |
|CalleeEchoReturn  <br/> |int  <br/> |Echo Return Loss Enhancement for the callee. The unit for this metric is dB. Lower values represent less echo. This metric is not reported by the A/V Conferencing Server or IP phones.  <br/> |
|CalleeSpeakerGlitchRate  <br/> |int  <br/> |Average glitches per five minutes for the callee's loudspeaker rendering. For good quality, this should be less than one per five minutes. Not reported by A/V Conferencing Servers, Mediation Servers, or IP phones.  <br/> |
|CalleeMicGlitchRate  <br/> |int  <br/> |Average glitches per five minutes for the callee's microphone capture. For good quality this should be less than one per five minutes. Not reported by A/V Conferencing Servers, Mediation Servers, or IP phones.  <br/> |
|CalleeTimestampDriftRateMic  <br/> |decimal(9,2)  <br/> |Callee's microphone device clock drift rate, relative to CPU clock.  <br/> |
|CalleeTimestampDriftRateSpk  <br/> |decimal(9,2)  <br/> |Callee's speaker device clock drift rate, relative to CPU clock.  <br/> |
|CalleeTimestampErrorMicMs  <br/> |decimal(9,2)  <br/> |Average microphone capture stream time stamp error, in milliseconds, in the last 20 seconds of the call.  <br/> |
|CalleeTimestampErrorSpkMs  <br/> |decimal(9,2)  <br/> |Average of the callee's speaker render stream time stamp error, in milliseconds, in the last 20 seconds of the call.  <br/> |
|CalleeVsEntryCauses  <br/> |smallint  <br/> |Voice switch is a half-duplex mode with reduced interruption ability. See the [MediaLine table](medialine-0.md) for more information. <br/> |
|CalleeEchoEventCauses  <br/> |tinyint  <br/> |Causes of an echo event for the callee. See the [MediaLine table](medialine-0.md) for more information. <br/> |
|CalleeEchoPercentMicIn  <br/> |decimal(5,2)  <br/> |Percentage of time when echo is detected in the callee's microphone capture stream. If headset is used, the value should be low.  <br/> |
|CalleeEchoPercentSend  <br/> |decimal(5,2)  <br/> |Percentage of time when echo is detected in the callee's sent stream. High echo percentage in send streams an indication of echo leak.  <br/> |
|CalleeRxAGCSignalLevel  <br/> |int  <br/> |Received signal level on the Mediation Server from the Gateway for the callee's audio; this applies only to the Mediation Server. The unit of this metric is dBoV. For good quality, the acceptable range should be [-30 to -18] dBoV.  <br/> |
|CalleeRxAGCNoiseLevel  <br/> |int  <br/> |Received signal level on the Mediation Server from the Gateway for the callee's audio. This applies only to the Mediation Server. The unit of this metric is dBoV. For good quality, the acceptable range should be less than -50 dBoV.  <br/> |
|CalleeRxAGCGain  <br/> |int  <br/> |Automatic gain control (AGC) on the Mediation Server side applied to the callee's audio.  <br/> |
|CalleeInitialSignalLevelRMS  <br/> |float  <br/> |Root mean square (RMS) of the incoming signal to the callee for up to the first 30 seconds of the call.  <br/> |
|RatioConcealedSamplesAvg  <br/> |decimal(5,2)  <br/> |Average ratio of concealed samples generated by audio healing to typical samples.  <br/> |
|RatioStretchedSamplesAvg  <br/> |decimal(5,2)  <br/> |Average ratio of stretched samples generated by audio healing to typical samples.  <br/> |
|RatioCompressedSamplesAvg  <br/> |decimal(5,2)  <br/> |Average ratio of compressed samples generated by audio healing to typical samples.  <br/> |
|RoundTrip  <br/> |int  <br/> |Round trip time from RTCP statistics.  <br/> |
|RoundTripMax  <br/> |int  <br/> |Maximum round trip time for the audio stream.  <br/> |
|OverallAvgNetworkMOS  <br/> |decimal(3,2)  <br/> |Average wideband Network MOS for the call. This metric depends on the packet loss, jitter, and codec used. Range is 1.0 to 5.0.  <br/> |
|OverallMinNetworkMOS  <br/> |decimal(3,2)  <br/> |Minimum wideband Network MOS for the call.  <br/> |
|SendListenMOS  <br/> |decimal(3,2)  <br/> |Average predicted wideband Listening MOS score for audio sent, including speech level, noise level and capture device characteristics.  <br/> |
|SendListenMOSMin  <br/> |decimal(3,2)  <br/> |Minimum SendListenMOS for the call.  <br/> |
|RecvListenMOS  <br/> |decimal(3,2)  <br/> |Average predicted wideband Listening MOS score for audio received from the network including speech level, noise level, codec, network conditions and capture device characteristics.  <br/> |
|RecvListenMOSMin  <br/> |decimal(3,2)  <br/> |Minimum RecvListenMOS for the call.  <br/> |
|AudioFECUsed  <br/> |bit  <br/> |Indicates whether audio FEC was used for the call.  <br/> |
|SenderIsCallerPAI  <br/> |bit  <br/> |Indicates direction of the p-asserted identify information; 1 means the stream direction is from the caller to the callee; 0 means the stream direction is from the callee to the caller.  <br/> |
   

