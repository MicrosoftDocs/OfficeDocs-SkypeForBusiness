---
title: "ConferenceUris table in Skype for Business Server 2015"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 3/9/2015
audience: ITPro
ms.topic: article
ms.service: skype-for-business-server
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.assetid: b1721d52-3c65-45ea-8997-06af8fef93fc
description: "The ConfereneUris table is a supporting table that stores a list of the various conference URIs that have participated in conference sessions recorded in the database. Each record in the table represents one conference URI."
---

# ConferenceUris table in Skype for Business Server 2015
 
The ConfereneUris table is a supporting table that stores a list of the various conference URIs that have participated in conference sessions recorded in the database. Each record in the table represents one conference URI.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**NextUpdateTS** <br/> |datetime  <br/> |Primary  <br/> |Time stamp, Internal used.  <br/> |
|**ConferenceUriId** <br/> |int  <br/> |Primary  <br/> |Unique number identifying this conference URI.  <br/> |
|**ConferenceUri** <br/> |nvarchar(450)  <br/> ||Conference URI.  <br/> |
|**Checksum** <br/> |int  <br/> ||Checksum of ConferenceUri. Used to increases the speed of database searches.  <br/> |
|**UriTypeId** <br/> |int  <br/> |Foreign  <br/> |URI type, such as conf:chat for IM conference, or conf:audio-video for audio/video conference. See the [UriTypes table](uritypes.md) table for more information. <br/> |
   

