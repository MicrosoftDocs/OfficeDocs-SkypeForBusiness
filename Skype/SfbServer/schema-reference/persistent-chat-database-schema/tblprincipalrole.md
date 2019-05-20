---
title: "tblPrincipalRole"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/9/2015
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: dcd16dc1-a66c-4720-a48f-ec8b28337383
description: "tblPrincipalRole contains explicit roles assigned to nodes."
---

# tblPrincipalRole
 
tblPrincipalRole contains explicit roles assigned to nodes.
  
**Columns**

|**Column**|**Type**|**Description**|
|:-----|:-----|:-----|
|prinRoleNodeID  <br/> |int, not null  <br/> |Node ID that the role applies to.  <br/> |
|prinRolePrinID  <br/> |int, not null  <br/> |Principal ID.  <br/> |
|prinRoleTypeID  <br/> |int, not null  <br/> |Role type ID (from tblRoleType).  <br/> |
|prinRoleUpdatedBy  <br/> |int, not null  <br/> |ID of the principal that last updated this entry.  <br/> |
   
**Keys**

|**Column**|**Description**|
|:-----|:-----|
|\<prinRoleNodeID, prinRolePrinID, prinRoleTypeID\>  <br/> |Primary key.  <br/> |
|prinRoleNodeID  <br/> |Foreign key with lookup in tblNode.nodeID table.  <br/> |
|prinRolePrinID  <br/> |Foreign key with lookup in tblPrincipal.prinID table.  <br/> |
|prinRoleTypeID  <br/> |Foreign key with lookup in tblRoleType.rtypeID table.  <br/> |
   

