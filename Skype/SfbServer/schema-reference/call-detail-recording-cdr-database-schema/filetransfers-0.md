---
title: "FileTransfers table in Skype for Business Server 2015"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 7/15/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 5368e67c-d8a9-43a1-9472-a839950dedb3
description: "Each record represents one file transfer session."
---

# FileTransfers table in Skype for Business Server 2015
 
Each record represents one file transfer session.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**SessionIdTime** <br/> |datetime  <br/> |Primary, Foreign  <br/> |Time of session request. Used in conjunction with **SessionIdSeq** to uniquely identify a session. See the [Dialogs table in Skype for Business Server 2015](dialogs.md) for more information. <br/> |
|**SessionIdSeq** <br/> |int  <br/> |Primary, Foreign  <br/> |ID number to identify the session. Used in conjunction with **SessionIdTime** to uniquely identify a session. See the [Dialogs table in Skype for Business Server 2015](dialogs.md) for more information. <br/> |
|**File Name** <br/> |nvarchar(256)  <br/> ||Name of the file.  <br/> |
|**FileIdentity** <br/> |uniqueidentifier  <br/> ||Unique identifier to distinguish between file transfers involving the same file name.  <br/> |
|**Cookie** <br/> |nvarchar(128)  <br/> |Primary  <br/> |Used to identify every follow-up message as being associated with this one.  <br/> |
|**Accept** <br/> |bit  <br/> ||Can be TRUE or NULL. If TRUE, then Reject and Cancel will be NULL.  <br/> |
|**Reject** <br/> |bit  <br/> ||Can be TRUE or NULL. If TRUE, then Accept and Cancel will be NULL.  <br/> |
|**Cancel** <br/> |bit  <br/> ||Can be TRUE or NULL. If TRUE, then Accept and Reject will be NULL.  <br/> |
|**LastModifiedTime** <br/> |Datetime  <br/> ||For internal use by the Monitoring service.  <br/> This field was introduced in Skype for Business Server 2015.  <br/> |
   

