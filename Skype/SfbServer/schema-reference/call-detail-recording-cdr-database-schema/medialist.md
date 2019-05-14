---
title: "MediaList table"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 7/12/2016
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 1f440590-c1bc-483e-b7bc-6cc763847768
description: "The MediaList table is a static table that stores the list of various media types."
---

# MediaList table
 
The MediaList table is a static table that stores the list of various media types.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**MediaId** <br/> |tinyint  <br/> |Primary  <br/> |Values: 1-7  <br/> |
|**Media** <br/> |nvarchar(256)  <br/> || Static mapping of MediaID and Media values: <br/>  1 -- IM <br/>  2 - File Transfer <br/>  3 - Remote Assistance <br/>  4 - Application Sharing <br/>  5 -- Audio <br/>  6 -- Video <br/>  7 - App Invite <br/> |
   
If you are trying to determine the modality type for the values in LcsCDR.SessionDetailsView.MediaTypes, then you need to use the following Join snippet: 
  
```
LEFT JOIN on Media.MediaId = MediaList.MediaId
```
