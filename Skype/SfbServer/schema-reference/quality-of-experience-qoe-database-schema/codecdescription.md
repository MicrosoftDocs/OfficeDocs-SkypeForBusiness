---
title: "CodecDescription table"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 2/1/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 3598acb8-7ea6-4748-8417-149c971c32a2
description: "The CodecDescription table maps unique codec identifiers to their corresponding codec. Codecs are used to encode digital signals for transmission and broadcast, and then to decode those signals for playback. This table was introduced in Microsoft Lync Server 2013"
---

# CodecDescription table
 
The CodecDescription table maps unique codec identifiers to their corresponding codec. Codecs are used to encode digital signals for transmission and broadcast, and then to decode those signals for playback. This table was introduced in Microsoft Lync Server 2013
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**CodecDescriptionKey** <br/> |smallint  <br/> |Primary  <br/> |Unique identifier assigned to the codec.  <br/> |
|**CodecDescription** <br/> |varchar(256)  <br/> |Unique  <br/> |Unique description of the codec corresponding to the CodecDescriptionKey.  <br/> |
   

