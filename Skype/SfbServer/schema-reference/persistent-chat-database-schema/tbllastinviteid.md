---
title: "tblLastInviteId"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 222b3508-5963-4ddc-b4f3-e8412767e61b
description: "tblLastInviteId contains the last invite ID that was generated (and used in the tblPrincipalInvites table) for each user."
---

# tblLastInviteId
 
tblLastInviteId contains the last invite ID that was generated (and used in the tblPrincipalInvites table) for each user.
  
**Columns**

|**Column**|**Type**|**Description**|
|:-----|:-----|:-----|
|prinID  <br/> |int, not null  <br/> |Principal ID.  <br/> |
|lastInviteID  <br/> |int, not null  <br/> |Last used invite ID.  <br/> |
   
**Keys**

|**Column**|**Description**|
|:-----|:-----|
|prinID  <br/> |Primary key.  <br/> |
|prinID  <br/> |Foreign key with lookup in tblPrincipal.prinID table.  <br/> |
   
## See also

[tblPrincipalInvites](tblprincipalinvites.md)
