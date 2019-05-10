---
title: "AudioClientEvent table"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 2/1/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: fef73d8f-7261-4e5b-9769-82435b007979
description: "Each record contains a client event for one endpoint in an audio call. Usually, one call has two records, one for caller and one for callee."
---

# AudioClientEvent table
 
Each record contains a client event for one endpoint in an audio call. Usually, one call has two records, one for caller and one for callee.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**ConferenceDateTime** <br/> |datetime  <br/> |Primary  <br/> |Referenced from the [MediaLine table](medialine-0.md).  <br/> |
|**SessionSeq** <br/> |int  <br/> |Primary  <br/> |Referenced from the [MediaLine table](medialine-0.md).  <br/> |
|**MediaLineLabel** <br/> |tinyint  <br/> |Primary  <br/> |Referenced from the [MediaLine table](medialine-0.md).  <br/> |
|**FromCaller** <br/> |bit  <br/> |Primary  <br/> |0: Callee's data  <br/> 1: Caller's data  <br/> |
|**NetworkSendQualityEventRatio** <br/> |decimal(5,2)  <br/> | <br/> |Percentage of session the NetworkSendQuality event was fired for 'Bad' state.  <br/> Network quality in terms of jitter or packet loss is severe and impacting the quality of audio being sent.  <br/> |
|**NetworkReceiveQualityEventRatio** <br/> |decimal(5,2)  <br/> | <br/> |Percentage of session the ReceiveSendQuality event was fired for 'Bad' state.  <br/> Network quality in terms of jitter or packet loss is severe and impacting the quality of audio being received.  <br/> |
|**NetworkDelayEventRatio** <br/> |decimal(5,2)  <br/> | <br/> |Percentage of session the Delay event was fired for 'Bad' state. Network latency is severe and impacting the experience by preventing interactive communication  <br/> |
|**NetworkBandwidthLowEventRatio** <br/> |decimal(5,2)  <br/> | <br/> |Percentage of session the LowBandwidth event was fired for 'Bad' state. The available bandwidth is insufficient for an acceptable voice experience.  <br/> |
|**CPUInsufficientEventRatio** <br/> |decimal(5,2)  <br/> | <br/> |Percentage of session the insufficient CPU event was fired for 'Bad' state. There are insufficient CPU cycles for processing with the current modalities and applications in use. This causes distortions with the audio channel.  <br/> |
|**DeviceHalfDuplexAECEventRatio** <br/> |decimal(5,2)  <br/> | <br/> |Percentage of session the DeviceHalfDuplexAEC event was fired for 'Bad' state. In order to prevent echo, the system has enter half duplex.  <br/> |
|**DeviceRenderNotFunctioningEventRatio** <br/> |decimal(5,2)  <br/> | <br/> |Percentage of session the DeviceRenderNotFunctioning event was fired for 'Bad' state. The render device currently being used for the session is not functioning correctly. This can cause one-way audio issues.  <br/> |
|**DeviceCaptureNotFunctioningEventRatio** <br/> |decimal(5,2)  <br/> | <br/> |Percentage of session the DeviceCaptureNotFunctioning event was fired for 'Bad' state. The capture device currently being used for the session is not functioning correctly. This can cause one-way audio issues.  <br/> |
|**DeviceGlitchesEventRatio** <br/> |decimal(5,2)  <br/> | <br/> |Percentage of session the DeviceGlitches event was fired for 'Bad' state. There are severe glitches in the rendering of audio which is causing distortions. These glitches can be caused by driver issues, deferred procedure calls (DPC) storm (drivers), and high CPU usage.  <br/> |
|**DeviceLowSNREventRatio** <br/> |decimal(5,2)  <br/> | <br/> |Percentage of session the DeviceLowSNR event was fired for 'Bad' state. The capture quality is very poor, either very noisy or user is talking too far away from the microphone. This will cause distortions.  <br/> |
|**DeviceLowSpeechLevelEventRatio** <br/> |decimal(5,2)  <br/> | <br/> |Percentage of session the DeviceLowSpeechLevel event was fired for 'Bad' state. User's speech level is too low and the system cannot increase it any further. This can either cause distortions or perceived as one-way audio.  <br/> |
|**DeviceClippingEventRatio** <br/> |Decimal(5,2)  <br/> | <br/> |Percentage of session the DeviceClipping event was fired for 'Bad' state.  <br/> When near-end speech clips the microphone, far-end hears distortion due to clipping. It is important to avoid near-end microphone clipping.  <br/> |
|**DeviceEchoEventRatio** <br/> |decimal(5,2)  <br/> | <br/> |Percentage of session the DeviceEchoEvent event was fired for 'Bad' state. Device or setup is causing echo beyond the ability of the system to compensate.  <br/> |
|**DeviceNearEndToEchoRatioEventRatio** <br/> |decimal(5,2)  <br/> | <br/> |Percentage of session the DeviceNearEndToEchoRatio event was fired for 'Bad' state. The user's speech is too low compared to the echo being captured which impacts the users experience because it limits how easy it is to interrupt a user. Reduce speaker volume, move the microphone closer to the talker.  <br/> |
|**DeviceMultipleEndpointsEventCount** <br/> |int  <br/> ||Number of times during session the DeviceMultipleEndpoints event was fired for 'Bad' state. Multiple audio endpoints in the same session detected and the system has compensated by reducing render volume.  <br/> |
|**DeviceHowlingEventCount** <br/> |int  <br/> | <br/> |Number of times during session the DeviceHowlingEvent event was fired for 'Bad' state. Audio feedback loop detected (caused by multiple endpoints sharing audio path).  <br/> |
|**DeviceRenderZeroVolumeEventRatio** <br/> |decimal(5,2)  <br/> ||Percentage of session the DeviceRenderZeroVolume event was fired for being in the "Bad' state. The render device was set to zero volume.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
|**DeviceRenderMuteEventRatio** <br/> |decimal(5,2)  <br/> ||Percentage of session the DeviceRenderMute event was fired for being in the "Bad' state. The render device was muted.  <br/> This column was introduced in Microsoft Lync Server 2013.  <br/> |
   

