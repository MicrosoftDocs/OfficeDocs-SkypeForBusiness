---
title: "tblNode"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 10/20/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: a31d2961-aa83-4286-a12e-15d279c95f19
description: "tblNode contains the object tree (with category or chat room nodes) as managed in the control panel and administrative cmdlets."
---

# tblNode
 
tblNode contains the object tree (with category or chat room nodes) as managed in the control panel and administrative cmdlets.
  
**Columns**

|**Column**|**Type**|**Description**|
|:-----|:-----|:-----|
|nodeID  <br/> |int, not null  <br/> |Node ID (unique number).  <br/> |
|nodeGuid  <br/> |GUID, not null  <br/> |Node GUID.  <br/> |
|parentID  <br/> |int  <br/> |Node ID of parent. The root node (with ID 1) includes itself as parent as well.  <br/> |
|nodeType  <br/> |bit, not null  <br/> |True if the node is a category.  <br/> False if the node is a chat room.  <br/> |
|nodeName  <br/> |nvarchar (256), not null  <br/> |Node name.  <br/> |
|nodeDesc  <br/> |nvarchar (256), not null  <br/> |Node description.  <br/> |
|invite  <br/> |bit  <br/> | For categories: <br/>  True if invites are on. <br/>  False if invites are off. <br/>  For rooms: <br/>  False if invites are off (overrides the parent category). <br/>  Null if the invites setting is inherited from the parent category. <br/> |
|logged  <br/> |bit  <br/> | For categories: <br/>  True if chat history is on. <br/>  False if chat history is off. <br/>  For rooms: <br/>  Null. <br/> |
|filePost  <br/> |bit  <br/> | For categories: <br/>  True if file uploads are allowed. <br/>  False if file uploads are disallowed. <br/>  For rooms: <br/>  Null. <br/> |
|disabled  <br/> |bit, not null  <br/> |True if the chat room is disabled. Applies only to chat rooms. (False for categories.)  <br/> |
|behavior  <br/> |smallint, not null  <br/> | Behavior (looked up in EnumValue table): <br/>  4: Normal (normal chat rooms). <br/>  5: Auditorium (auditorium chat rooms, only presenters can contribute). <br/>  Applies only to chat rooms. <br/> |
|visibility  <br/> |smallint, not null  <br/> | Visibility (looked up on EnumValue table): <br/>  2: Private <br/>  3: Scoped <br/>  6: Open <br/>  Applies only to chat rooms. <br/> |
|siopID  <br/> |GUID  <br/> |Add-In GUID if an add-in is associated with this chat room. (Categories do not have add-ins.)  <br/> The add-in information is looked up in SiopWhiteList table.  <br/> |
|nodeAddedBy  <br/> |int, not null  <br/> |ID of the principal that created this node.  <br/> |
|nodeAddedOn  <br/> |bigint, not null  <br/> |Time stamp of the node creation.  <br/> |
|nodeUpdatedBy  <br/> |int, not null  <br/> |ID of the principal that did the latest update of this node.  <br/> |
|nodeUpdatedOn  <br/> |bigint, not null  <br/> |Time stamp of the latest update of this node.  <br/> |
|purgedOn  <br/> |datetime  <br/> |Time of the latest purge operation (removal of scopes from tblScopedPrincipal table and roles from tblPrincipalRole table) that affected this node. This is used by the Chat service's internal cache update mechanism.  <br/> |
   
**Keys**

|**Column**|**Description**|
|:-----|:-----|
|nodeID  <br/> |Primary key.  <br/> |
|behavior  <br/> |Foreign key with lookup in tblEnumValue.valueID table.  <br/> |
|visibility  <br/> |Foreign key with lookup in tblEnumValue.valueID table.  <br/> |
|parentID  <br/> |Foreign key with lookup in tblNode.nodeID table.  <br/> |
|siopID  <br/> |Foreign key with lookup in tblSiopWhiteList.siopId table.  <br/> |
   

