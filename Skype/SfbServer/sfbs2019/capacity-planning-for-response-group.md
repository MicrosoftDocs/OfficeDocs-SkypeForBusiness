---
title: "Capacity planning for Response Group in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: a2459a69-1f45-4f2f-bca5-d4f442708e44

---

# Capacity planning for Response Group in Lync Server 2013
[]The following table describes the Response Group user model that you can use as the basis for capacity planning requirements.
  
> [!NOTE]
> The numbers in the following table assume that you use 16 kHz, mono, 16-bit Wave (.wav) files for all response group audio files. If you use other file formats, such as Windows Media Audio (.wma), the numbers may vary. 
  
> [!IMPORTANT]
> Keep in mind that for disaster recovery capacity planning, each pool of a paired pool should be able to handle the workloads for all the response groups in both pools. 
  
**Response Group User Model**

|**Metric**|**Per Enterprise Edition pool  <br/> (With 8 Front End Servers)**|**Per Standard Edition server**|
|:-----|:-----|:-----|
|Incoming calls per second  <br/> |16  <br/> |2  <br/> |
|Concurrent calls connected to IVR or MoH  <br/> |480  <br/> |60  <br/> |
|Concurrent anonymous sessions (without IM)  <br/> |224  <br/> |28  <br/> |
|Concurrent anonymous sessions (with IM)  <br/> |64  <br/> |8  <br/> |
|Active agents (formal and informal)  <br/> |1200  <br/> |1200  <br/> |
|Number of hunt groups  <br/> |400  <br/> |400  <br/> |
|Number of IVR groups (use speech recognition)  <br/> |200  <br/> |200  <br/> |
   

