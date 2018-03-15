---
title: "MonitoredRegionLink table in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: cebda194-7be3-42d6-b6f0-c86f8b0f200a
description: "The MonitoredRegionLink table is a supporting table. Each record represents one link between two countries/regions."
---

# MonitoredRegionLink table in Lync Server 2013
[]
The MonitoredRegionLink table is a supporting table. Each record represents one link between two countries/regions.
  
|****Column****|****Data Type****|****Key/Index****|****Details****|
|:-----|:-----|:-----|:-----|
|**Region1Key** <br/> |int  <br/> |Primary, Foreign  <br/> |Referenced from the [Region table in Lync Server 2013](region-table.md).  <br/> |
|**Region2Key** <br/> |int  <br/> |Primary, Foreign  <br/> |Referenced from the [Region table in Lync Server 2013](region-table.md).  <br/> |
   

