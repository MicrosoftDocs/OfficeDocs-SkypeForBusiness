---
title: "tblPrincipalInvites in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 548ec156-4d1a-469d-a804-62cff226e5c2
description: "tblPrincipalInvites contains invitations for all provisioned users for all nodes with auto-invite on."
---

# tblPrincipalInvites in Lync Server 2013
[]
tblPrincipalInvites contains invitations for all provisioned users for all nodes with auto-invite on.
  
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
   

