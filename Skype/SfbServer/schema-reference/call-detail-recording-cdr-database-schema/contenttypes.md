---
title: "ContentTypes table in Skype for Business Server 2015"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/9/2015
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: e3e38035-457c-4173-bdb9-d53a7420eba2
description: "The ContentTypes table is a supporting table that stores a list of the content types used in both peer-to-peer sessions and conference sessions. Each record in the table represents one content type."
---

# ContentTypes table in Skype for Business Server 2015
 
The ContentTypes table is a supporting table that stores a list of the content types used in both peer-to-peer sessions and conference sessions. Each record in the table represents one content type.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**ContentTypeId** <br/> |int  <br/> |Primary  <br/> |Unique number identifying the content type.  <br/> |
|**ContentType** <br/> |nvarchar(256)  <br/> ||Content type name.  <br/> |
   

