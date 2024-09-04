---
title: "Media table"
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
ms.assetid: 1e1b427f-59b5-4564-bde5-1002a80439ee
description: "Each record represents one media type used in a peer-to-peer session. One session would be represented by multiple records in the table, if more than one media type is used."
---

# Media table
 
Each record represents one media type used in a peer-to-peer session. One session is represented by multiple records in the table, if more than one media type is used.
  
> [!NOTE]
> The Media table should not be used to calculate the media duration for a session. This table contains the signaling details of media exchange in a session. Media exchange is done by the INVITE request, and StartTime indicates the time that the INVITE was sent out. The invite time does not necessarily mean the media start time, because media starts only after the sessionee accepts the session. The EndTime usually means the end time of this session. 
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**SessionIdTime** <br/> |datetime  <br/> |Primary, Foreign  <br/> |Time of session request. Used with **SessionIdSeq** to uniquely identify a session. For more information, see the [Dialogs table in Skype for Business Server 2015](dialogs.md). <br/> |
|**SessionIdSeq** <br/> |int  <br/> |Primary, Foreign  <br/> |ID number to identify the session. Used with **SessionIdTime** to uniquely identify a session. For more information, see the [Dialogs table in Skype for Business Server 2015](dialogs.md). <br/> |
|**MediaId** <br/> |tinyint  <br/> |Primary, Foreign  <br/> |Unique number identifying this media type. For more information, see the [MediaList table](medialist.md). <br/> |
|**StartTime** <br/> |datetime  <br/> |Primary  <br/> |This is the time that a media request was sent out, not the real media start time. **StartTime** includes the session setup time. <br/> |
|**EndTime** <br/> |datetime  <br/> ||This is the end time of the session.  <br/> |
   

