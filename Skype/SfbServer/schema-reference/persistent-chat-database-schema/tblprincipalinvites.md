---
title: "tblPrincipalInvites"
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
ms.assetid: 548ec156-4d1a-469d-a804-62cff226e5c2
description: "tblPrincipalInvites contain invitations for all provisioned users for all nodes with autoinvite on."
---

# tblPrincipalInvites
 
tblPrincipalInvites contain invitations for all provisioned users for all nodes with autoinvite on.
  
**Columns**

|**Column**|**Type**|**Description**|
|:-----|:-----|:-----|
|prinID  <br/> |int, not null  <br/> |Principal ID.  <br/> |
|invID  <br/> |int, not null  <br/> |Unique sequential number (per principal ID) generated from tblLastInviteId table.  <br/> |
|nodeID  <br/> |int, not null  <br/> |Node ID (chat room only).  <br/> |
|createdOn  <br/> |datetime, not null  <br/> |Time of creation.  <br/> |
   
**Keys**

|**Column**|**Description**|
|:-----|:-----|
|\<prinID, nodeID\>  <br/> |Primary key.  <br/> |
|prinID  <br/> |Foreign key with lookup in tblPrincipal.prinID table.  <br/> |
|nodeID  <br/> |Foreign key with lookup in tblNode.nodeID table.  <br/> |
   

