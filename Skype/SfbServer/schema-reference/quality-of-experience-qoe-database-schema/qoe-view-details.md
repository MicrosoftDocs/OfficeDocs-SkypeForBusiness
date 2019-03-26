---
title: "QoE view details"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 6a658318-a317-4546-a44c-a9c473d8e86a
description: "Views cover the most common scenarios for returning data from the QoE SQL database. It is recommended views used for building custom reports instead of directly accessing the database tables; that's because views are more likely to maintain backwards compatibility with future releases."
---

# QoE view details
 
Views cover the most common scenarios for returning data from the QoE SQL database. It is recommended views used for building custom reports instead of directly accessing the database tables; that's because views are more likely to maintain backwards compatibility with future releases.
  
|**View Name**|**Description**|
|:-----|:-----|
|[AudioStreamDetail view](audiostreamdetail.md) <br/> |Stores information about each audio stream in the database.  <br/> |
|[MediaLine view](medialine.md) <br/> |Stores information about each media line in the database. One audio session typically contains one audio media line. One audio and video (A/V) session typically contains one audio media line and one video media line; however, the session might contain two video media lines if a conferencing device is used or if Gallery View is used.  <br/> |
|[NetworkConfigurationSettings view](networkconfigurationsettings.md) <br/> |Stores information about the network configuration.  <br/> |
|[Session view](session-0.md) <br/> |Stores information about sessions that have records in the database.  <br/> |
|[UserAgent view](useragent-0.md) <br/> |Stores information about the user agents that have been involved in sessions that have records in the database.  <br/> |
|[VideoStreamDetail view](videostreamdetail.md) <br/> |Stores information about each video stream in the database.  <br/> |
   

