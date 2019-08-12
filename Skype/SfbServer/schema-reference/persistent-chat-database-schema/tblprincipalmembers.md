---
title: "tblPrincipalMembers"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/9/2015
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 9a3e24cf-6ef7-4b82-99fc-50ba41800b6f
description: "tblPrincipalMembers contains principal memberships."
---

# tblPrincipalMembers
 
tblPrincipalMembers contains principal memberships.
  
**Columns**

|**Column**|**Type**|**Description**|
|:-----|:-----|:-----|
|prinID  <br/> |int, not null  <br/> |Principal ID.  <br/> |
|memberADPath  <br/> |nvarchar (384), not null  <br/> |Distinguished name of a member. A member does not have to be a principal (in tblPrincipal table).  <br/> |
   
**Keys**

|**Column**|**Description**|
|:-----|:-----|
|\<prinID, memberADPath\>  <br/> |Primary key.  <br/> |
|prinID  <br/> |Foreign key with lookup in tblPrincipal.prinID.  <br/> |
   

