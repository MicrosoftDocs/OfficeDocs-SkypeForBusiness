---
title: "tblScopePrincipal"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 422d6c7f-7ba7-4dd4-bacc-95ace47959ff
description: "tblScopePrincipal contains scopes assigned to nodes."
---

# tblScopePrincipal
 
tblScopePrincipal contains scopes assigned to nodes.
  
**Columns**

|**Column**|**Type**|**Description**|
|:-----|:-----|:-----|
|scopeNodeID  <br/> |int, not null  <br/> |Node ID that the scope applies to.  <br/> |
|scopePrinID  <br/> |int, not null  <br/> |Principal ID.  <br/> |
|scopeIsDenied  <br/> |bit, not null  <br/> |True if type of scope is Deny; False if Allow.  <br/> |
|scopeUpdatedBy  <br/> |int, not null  <br/> |ID of the principal that last updated this entry.  <br/> |
   
**Keys**

|**Column**|**Description**|
|:-----|:-----|
|\<scopeNodeID, scopePrinID\>  <br/> |Primary key.  <br/> |
|scopeNodeID  <br/> |Foreign key with lookup in tblNode.nodeID table.  <br/> |
|scopePrinID  <br/> |Foreign key with lookup in tblPrincipal.prinID table.  <br/> |
   

