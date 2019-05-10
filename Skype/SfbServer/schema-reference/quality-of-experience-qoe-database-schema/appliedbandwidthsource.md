---
title: "AppliedBandwidthSource table"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 2/1/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 24fb3caf-19b3-4c0a-90d7-ca5d53de32ad
description: "The AppliedBandwidthSource table is a supporting table. Each record represents one source."
---

# AppliedBandwidthSource table
 
The AppliedBandwidthSource table is a supporting table. Each record represents one source.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**AppliedBandwidthSourceKey** <br/> |int  <br/> |Primary  <br/> |Unique number identifying the source.  <br/> |
|**AppliedBandwidthSource** <br/> |varchar(256)  <br/> |Unique  <br/> |This is the source of the bandwidth cap being imposed. It describes where the bandwidth limit is coming from (for example, "Policy Server", "TURN Server", or "Modality").  <br/> |
   

