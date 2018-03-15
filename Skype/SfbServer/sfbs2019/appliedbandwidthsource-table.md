---
title: "AppliedBandwidthSource table in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 24fb3caf-19b3-4c0a-90d7-ca5d53de32ad
description: "The AppliedBandwidthSource table is a supporting table. Each record represents one source."
---

# AppliedBandwidthSource table in Lync Server 2013
[]
The AppliedBandwidthSource table is a supporting table. Each record represents one source.
  
|****Column****|****Data Type****|****Key/Index****|****Details****|
|:-----|:-----|:-----|:-----|
|**AppliedBandwidthSourceKey** <br/> |int  <br/> |Primary  <br/> |Unique number identifying the source.  <br/> |
|**AppliedBandwidthSource** <br/> |varchar(256)  <br/> |Unique  <br/> |This is the source of the bandwidth cap being imposed. It describes where the bandwidth limit is coming from (for example, "Policy Server", "TURN Server", or "Modality").  <br/> |
   

