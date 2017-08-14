---
title: SessionCorrelation table
ms.prod: SKYPEFORBUSINESS
ms.assetid: 041705e1-7290-464f-95f8-96256cfa2e3e
---


# SessionCorrelation table
[]
The SessionCorrelation table is a supporting table. Each record represents one CorrelationID which is used to correlate multiple sessions. 
  
    
    



|****Column****|****Data Type****|****Key/Index****|****Details****|
|:-----|:-----|:-----|:-----|
|**Checksum** <br/> |int  <br/> |||
|**CorrelationKey** <br/> |int  <br/> |Primary  <br/> |Unique number identifying this A/V Conferencing Server.  <br/> |
|**CorrelationID** <br/> |nvarchar(256)  <br/> |Unique  <br/> |Sessions that are correlated will have the same correlation ID.  <br/> |
|**NextUpdateTS** <br/> |datetime  <br/> | <br/> |For internal use only.  <br/> |
   

