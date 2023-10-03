---
title: "MonitoredRegionLink table"
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
ms.assetid: cebda194-7be3-42d6-b6f0-c86f8b0f200a
description: "The MonitoredRegionLink table is a supporting table. Each record represents one link between two countries/regions."
---

# MonitoredRegionLink table
 
The MonitoredRegionLink table is a supporting table. Each record represents one link between two countries/regions.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**Region1Key** <br/> |int  <br/> |Primary, Foreign  <br/> |Referenced from the [Region table](region.md).  <br/> |
|**Region2Key** <br/> |int  <br/> |Primary, Foreign  <br/> |Referenced from the [Region table](region.md).  <br/> |
   

