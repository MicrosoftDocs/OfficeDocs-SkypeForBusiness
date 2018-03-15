---
title: "tblLastChatId in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 17a4ffbe-cca9-4ec5-ae46-38a15274889a
description: "tblLastChatId contains the last chat ID that was generated (and used in the tblChat table) for each user."
---

# tblLastChatId in Lync Server 2013
[]
tblLastChatId contains the last chat ID that was generated (and used in the tblChat table) for each user.
  
**Columns**

|**Column**|**Type**|**Description**|
|:-----|:-----|:-----|
|nodeID  <br/> |int, not null  <br/> |Node ID (chat room-type only).  <br/> |
|lastChatID  <br/> |bigint, not null  <br/> |Last used chat ID.  <br/> |
   
**Keys**

|**Column**|**Description**|
|:-----|:-----|
|\<nodeID, lastChatID\>  <br/> |Primary key (just nodeID is sufficient for processing).  <br/> |
|nodeID  <br/> |Foreign key with lookup in tblNode.nodeID table.  <br/> |
   
## See also

#### 

[tblChat in Lync Server 2013](tblchat.md)

