---
title: "VideoClientEvent table"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 2/1/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: e8ab963b-fe1d-45b3-b9bd-66a5f44c1629
description: "Each record contains client event for one endpoint in a video call. Usually, one call has two records, one for caller and one for callee."
---

# VideoClientEvent table
 
Each record contains client event for one endpoint in a video call. Usually, one call has two records, one for caller and one for callee.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**ConferenceDateTime** <br/> |datetime  <br/> |Primary  <br/> |Referenced from the [MediaLine table](medialine-0.md).  <br/> |
|**SessionSeq** <br/> |int  <br/> |Primary  <br/> |Referenced from the [MediaLine table](medialine-0.md).  <br/> |
|**MediaLineLabel** <br/> |tinyint  <br/> |Primary  <br/> |Referenced from the [MediaLine table](medialine-0.md).  <br/> |
|**FromCaller** <br/> |bit  <br/> |Primary  <br/> |0: Callee's data  <br/> 1: Caller's data  <br/> |
|**NetworkBandwidthLowEventRatio** <br/> || <br/> |Percentage of session the LowBandwidth event was fired for 'Bad' state. The available bandwidth is insufficient for an acceptable voice experience.  <br/> |
|**NetworkReceiveQualityEventRatio** <br/> || <br/> |Percentage of session the ReceiveSendQuality event was fired for 'Bad' state.  <br/> Network quality in terms of jitter or packet loss is severe and impacts the quality of audio being received.  <br/> |
   

