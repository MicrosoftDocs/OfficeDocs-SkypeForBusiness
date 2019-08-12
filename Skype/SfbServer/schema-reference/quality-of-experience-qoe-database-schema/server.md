---
title: "Server table"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 2/1/2018
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 9af89d08-d35a-48e8-b56d-6df292f973cc
description: "The Server table is a supporting table. Each record represents one server."
---

# Server table
 
The Server table is a supporting table. Each record represents one server. 
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**ServerKey** <br/> |int  <br/> |Primary  <br/> |Unique number identifying the server.  <br/> |
|**FQDNOrIP** <br/> |nvarchar(256)  <br/> |index  <br/> |MAC address string.  <br/> |
|**ServerType** <br/> |int  <br/> |Foreign  <br/> |1: Mediation Server  <br/> 2: A/V Conferencing Server16394: A/V Edge service32769: Gateway  <br/> |
|**PoolName** <br/> |nvarchar(512)  <br/> ||Pool the server belongs to. Only applicable for the A/V Conferencing Server.  <br/> |
|**NextUpdateTS** <br/> |datetime  <br/> ||For internal use only.  <br/> |
   

