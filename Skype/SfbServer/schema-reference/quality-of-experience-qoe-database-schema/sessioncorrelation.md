---
title: "SessionCorrelation table"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 2/1/2018
audience: ITPro
ms.topic: article
ms.service: skype-for-business-server
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.assetid: 041705e1-7290-464f-95f8-96256cfa2e3e
description: "The SessionCorrelation table is a supporting table. Each record represents one CorrelationID which is used to correlate multiple sessions."
---

# SessionCorrelation table
 
The SessionCorrelation table is a supporting table. Each record represents one CorrelationID which is used to correlate multiple sessions. 
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**Checksum** <br/> |int  <br/> |||
|**CorrelationKey** <br/> |int  <br/> |Primary  <br/> |Unique number identifying this A/V Conferencing Server.  <br/> |
|**CorrelationID** <br/> |nvarchar(256)  <br/> |Unique  <br/> |Sessions that are correlated will have the same correlation ID.  <br/> |
|**NextUpdateTS** <br/> |datetime  <br/> | <br/> |For internal use only.  <br/> |
   

