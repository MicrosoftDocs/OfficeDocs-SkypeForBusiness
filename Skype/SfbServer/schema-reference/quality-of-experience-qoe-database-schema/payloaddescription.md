---
title: "PayloadDescription table"
ms.author: serdars
author: SerdarSoysal
manager: laurawi
ms.date: 2/1/2018
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c49d61c0-305a-4770-a5d2-5d9f05decc6d
description: "The PayloadDescription table is a supporting table. Each record represents one Codec, which is used in an audio or video session."
---

# PayloadDescription table
 
The PayloadDescription table is a supporting table. Each record represents one Codec, which is used in an audio or video session.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**PayloadDescriptionKey** <br/> |int  <br/> |Primary  <br/> |Unique number identifying the Codec.  <br/> |
|**PayloadDescription** <br/> |nvarchar(256)  <br/> |Unique  <br/> |Codec name.  <br/> |
   

