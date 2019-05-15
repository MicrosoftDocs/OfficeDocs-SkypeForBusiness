---
title: "FileTransfers view"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: e52c3ad0-152e-4a18-af1c-1aff0d205151
description: "The FileTransfer view stores information about peer-to-peer file transfer sessions. This view was introduced in Microsoft Lync Server 2013."
---

# FileTransfers view
 
The FileTransfer view stores information about peer-to-peer file transfer sessions. This view was introduced in Microsoft Lync Server 2013.
  
> [!NOTE]
> The FileTransfers view contains all of the columns in the [SessionDetails view](sessiondetails-0.md) in addition the columns listed below.
  
|**Column**|**Data Type**|**Details**|
|:-----|:-----|:-----|
|**FileName** <br/> |nvarchar(256)  <br/> |Name of the file transferred.  <br/> |
|**Cookie** <br/> |nvarchar(128)  <br/> |Used to identify every follow-up message as being associated with this one.  <br/> |
|**FileIdentity** <br/> |uniqueidentifier  <br/> |Unique identifier to distinguish between file transfers involving the same file name.  <br/> |
|**Accept** <br/> |bit  <br/> |Can be TRUE or NULL. If TRUE, then Reject and Cancel will be NULL.  <br/> |
|**Reject** <br/> |bit  <br/> |Can be TRUE or NULL. If TRUE, then Accept and Cancel will be NULL.  <br/> |
|**Cancel** <br/> |bit  <br/> |Can be TRUE or NULL. If TRUE, then Accept and Reject will be NULL.  <br/> |
   

