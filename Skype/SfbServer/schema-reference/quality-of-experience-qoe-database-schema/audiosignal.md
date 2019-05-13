---
title: "AudioSignal table"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 2/1/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 0013c8c6-cdf9-4d70-bc2a-cddd1560f66b
description: "Each record represents audio signal metrics for one endpoint. Usually, each call has two records, one is for caller, and one is for callee."
---

# AudioSignal table
 
Each record represents audio signal metrics for one endpoint. Usually, each call has two records, one is for caller, and one is for callee. 
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**ConferenceDateTime** <br/> |datetime  <br/> |Primary  <br/> |Referenced from the [MediaLine table](medialine-0.md).  <br/> |
|**SessionSeq** <br/> |int  <br/> |Primary  <br/> |Referenced from the [MediaLine table](medialine-0.md).  <br/> |
|**MediaLineLabel** <br/> |tinyint  <br/> |Primary  <br/> |Referenced from the [MediaLine table](medialine-0.md).  <br/> |
|**FromCaller** <br/> |bit  <br/> |Primary  <br/> |0: Callee's data  <br/> 1: Caller's data  <br/> |
|**SendSignalLevel** <br/> |int  <br/> | <br/> |Represents the Post-Analog Gain Control audio signal level. The unit for this metric is dBmo. For acceptable quality, it should be at least 30 dBmo. This metric is not reported by the A/V Conferencing Server or IP phones.  <br/> |
|**RecvSignalLevel** <br/> |int  <br/> | <br/> |See SendSignalLevel.  <br/> |
|**SendNoiseLevel** <br/> |int  <br/> | <br/> |Represents the Post-Analog Gain Control audio noise level. The unit for this metric is dBmo. For acceptable quality, it should be less than 35 dBmo. This metric is not reported by the A/V Conferencing Server or IP phones.  <br/> |
|**RecvNoiseLevel** <br/> |int  <br/> | <br/> |See SendNoiseLevel.  <br/> |
|**EchoReturn** <br/> |int  <br/> | <br/> |Echo Return Loss Enhancement metric. The unit for this metric is dB. Lower values represent less echo. This metric is not reported by the A/V Conferencing Server or IP phones.  <br/> |
|**AudioSpeakerGlitchRate** <br/> |int  <br/> | <br/> |Average glitches per five minutes for the loudspeaker rendering. For good quality, this should be less than one per five minutes. Not reported by A/V Conferencing Servers, Mediation Servers, or IP phones.  <br/> |
|**AudioMicGlitchRate** <br/> |int  <br/> | <br/> |Average glitches per five minutes for the microphone capture. For good quality this should be less than one per five minutes. Not reported by A/V Conferencing Servers, Mediation Servers, or IP phones.  <br/> |
|**AudioTimestampDriftRateMic** <br/> |decimal(9,2)  <br/> | <br/> |Microphone device clock drift rate, relative to CPU clock.  <br/> |
|**AudioTimestampDriftRateSpk** <br/> |decimal(9,2)  <br/> | <br/> |Speaker device clock drift rate, relative to CPU clock.  <br/> |
|**AudioTimestampErrorMicMs** <br/> |decimal(9,2)  <br/> | <br/> |Speaker device clock drift rate, relative to CPU clock.  <br/> Average microphone capture stream time stamp error, in milliseconds, in the last 20 seconds of the call.  <br/> |
|**AudioTimestampErrorSpkMs** <br/> |decimal(9,2)  <br/> | <br/> |Average speaker render stream time stamp error, in milliseconds, in the last 20 seconds of the call.  <br/> |
|**VsEntryCauses** <br/> |smallint  <br/> | <br/> |Voice switch is a half-duplex mode with reduced interruption ability. Causes of voice switch entry:  <br/> ENTER_VS_BADTS 0x01  <br/> ENTER_VS_ECHO 0x02  <br/> ENTER_VS_FORCEORCONVERGENCE 0x04  <br/> ENTER_VS_DNLP 0x08  <br/> The cause can be a combination of those individual causes. ENTER_VS_FORCEORCONVERGENCE can only be enabled by regkey for test purpose.  <br/> The data type for this column was changed in Microsoft Lync Server 2013.  <br/> |
|**EchoEventCauses** <br/> |tinyint  <br/> | <br/> |Causes of an echo event:  <br/> ECHO_EVENT_BAD_TIMESTAMP 0x01  <br/> ECHO_EVENT_POSTAEC_ECHO 0x02  <br/> ECHO_EVENT_ANLP 0x04  <br/> ECHO_EVENT_DNLP 0x08  <br/> ECHO_EVENT_MIC_CLIPPING 0x10  <br/> ECHO_EVENT_BAD_STATE 0x20  <br/> The cause can be a combination of those individual causes.  <br/> |
|**EchoPercentMicIn** <br/> |decimal(5,2)  <br/> | <br/> |Percentage of time when echo was detected in the microphone capture stream. Typically, values are low for headsets or handsets, and higher for speaker phones or stand-alone speakers. For devices that support on-board acoustic echo cancellation, high values indicate echo leak. For other devices, this metric should not be used to evaluate device quality.  <br/> |
|**EchoPercentSend** <br/> |decimal(5,2)  <br/> ||Percentage of time when echo is detected in sent stream. High echo percentage in send streams an indication of echo leak.  <br/> |
|**RxAGCSignalLevel** <br/> |int  <br/> | <br/> |Received signal level on the Mediation Server from the Gateway; this applies only to the Mediation Server. The unit of this metric is dBoV. For good quality, the acceptable range should be [-30 to -18] dBoV.  <br/> |
|**RxAGCNoiseLevel** <br/> |int  <br/> | <br/> |Received signal level on the Mediation Server from the Gateway. This applies only to the Mediation Server. The unit of this metric is dBoV. For good quality, the acceptable range should be less than -50 dBoV.  <br/> |
|**RxAvgAGCGain** <br/> |int  <br/> | <br/> |Automatic gain control (AGC) on the Mediation Server side.  <br/> |
|**InitialSignalLevelRMS** <br/> |float  <br/> | <br/> |The root mean square (RMS) of the incoming signal of up to the first 30 seconds of the call.  <br/> |
|**RecvSignalLevelCh1** <br/> |int  <br/> ||Signal level as received on channel 1.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**RecvSignalLevelCh2** <br/> |int  <br/> ||Signal level as received on channel 2.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**RecvNoiseLevelCh1** <br/> |int  <br/> ||Noise level as received on channel 1.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**RecvNoiseLevelCh2** <br/> |int  <br/> ||Noise level as received on channel 2.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**SendSignalLevelCh1** <br/> |int  <br/> ||Signal level as sent on channel 1.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**SendSignalLevelCh2** <br/> |int  <br/> ||Signal level as sent on channel 2.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**SendNoiseLevelCh1** <br/> |int  <br/> ||Noise level as sent on channel 1.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**SendNoiseLevelCh2** <br/> |int  <br/> ||Noise level as sent on channel 2.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**RenderLoopbackSignalLevel** <br/> |int  <br/> ||Level in dBFS of the signal sent to the loudspeaker for playback. Accounts for any gain adjustments made to the received signal. <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |   
|**RenderNoiseLevel** <br/> |int  <br/> ||Level in dBFS of the noise content in the signal sent to the loudspeaker for playback <br/> |

