---
title: "SessionCorrelation table in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 041705e1-7290-464f-95f8-96256cfa2e3e
description: "The SessionCorrelation table is a supporting table. Each record represents one CorrelationID which is used to correlate multiple sessions."
---

# SessionCorrelation table in Lync Server 2013
[]
The SessionCorrelation table is a supporting table. Each record represents one CorrelationID which is used to correlate multiple sessions. 
  
|****Column****|****Data Type****|****Key/Index****|****Details****|
|:-----|:-----|:-----|:-----|
|**Checksum** <br/> |int  <br/> |||
|**CorrelationKey** <br/> |int  <br/> |Primary  <br/> |Unique number identifying this A/V Conferencing Server.  <br/> |
|**CorrelationID** <br/> |nvarchar(256)  <br/> |Unique  <br/> |Sessions that are correlated will have the same correlation ID.  <br/> |
|**NextUpdateTS** <br/> |datetime  <br/> | <br/> |For internal use only.  <br/> |
   

