---
title: "Conference table"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 2/1/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 2a2c327c-4719-42dc-a3bb-6dbc0864d9af
description: "The Conference table is a supporting table. Each record represents one conference or peer-to-peer session."
---

# Conference table
 
The Conference table is a supporting table. Each record represents one conference or peer-to-peer session.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**ConferenceKey** <br/> |int  <br/> |Primary  <br/> |Unique number identifying this conference record.  <br/> |
|**ConfURI** <br/> |nvarchar(450)  <br/> |unique  <br/> |Conference URI if this is a conference, or DialogID if this is a peer-to-peer session.  <br/> |
|**Checksum** <br/> |int  <br/> |index  <br/> |Checksum of the conference URI. This is used internally.  <br/> |
|**NextUpdateTS** <br/> |datetime  <br/> ||For internal use only.  <br/> |
   

