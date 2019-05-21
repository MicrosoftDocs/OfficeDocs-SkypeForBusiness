---
title: "tblRoleType"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/9/2015
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 1eac3a54-656a-40ac-b771-edfc64d6e34b
description: "tblRoleType is a static lookup table with role types and their associated permission sets."
---

# tblRoleType
 
tblRoleType is a static lookup table with role types and their associated permission sets.
  
**Columns**

|**Column**|**Type**|**Description**|
|:-----|:-----|:-----|
|rtypeID  <br/> |int, not null  <br/> |Role type ID.  <br/> |
|rtypeDesc  <br/> |nvarchar (256), not null  <br/> | Role type description. There are four available roles: <br/>  Member: Chat room member <br/>  Manager: Chat room manager <br/>  Voiced: Presenter for an auditorium chat room <br/>  Creator: Can create chat rooms <br/> |
|rtypeAllowedPermSet  <br/> |bigint, not null  <br/> | Permission set for the role. The used bits are: <br/>  2: True if the role can manage nodes. <br/>  4: True if the role can create children nodes. <br/>  7: True if the role can join a chat room (or children chat rooms of a category). <br/>  8: True if the role can chat in a chat room (or in children chat rooms of a category). <br/>  10: True if the role can read chat history even when not joined to a chat room. <br/>  11: True if the role can see the chat room. (This is further refined by factors such as scope and visibility.) <br/>  12: True if the role can chat in an auditorium chat room. <br/>  13: True if the role can bypass visibility rules when viewing nodes. <br/> |
   
**Key**

|**Column**|**Description**|
|:-----|:-----|
|rtypeID  <br/> |Primary key.  <br/> |
   

