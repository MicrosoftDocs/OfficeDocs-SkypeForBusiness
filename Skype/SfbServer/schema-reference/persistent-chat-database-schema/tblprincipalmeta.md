---
title: "tblPrincipalMeta"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 808490d4-7d6d-47a2-b8af-b5940d47073b
description: "tblPrincipalMeta contains the principals that have to be refreshed from Active Directory Domain Services."
---

# tblPrincipalMeta
 
tblPrincipalMeta contains the principals that have to be refreshed from Active Directory Domain Services.
  
**Columns**

|**Column**|**Type**|**Description**|
|:-----|:-----|:-----|
|prinID  <br/> |int, not null  <br/> |Principal ID.  <br/> |
|prinAffiliationsDirty  <br/> |bit, not null  <br/> |True if principal affiliations have to be refreshed.  <br/> |
|prinAttributesDirty  <br/> |bit, not null  <br/> |True if principal attributes have to be refreshed.  <br/> |
|prinDeleted  <br/> |bit, not null  <br/> |True if the principal has been deleted.  <br/> |
|tryCount  <br/> |int  <br/> |Number of attempts to refresh the principal from AD DS that have happened so far.  <br/> |
|lastTry  <br/> |datetime  <br/> |Time stamp from the latest attempt to refresh the principal. Can be null if no refresh has been attempted yet.  <br/> |
|nextTry  <br/> |datetime  <br/> |Time stamp for the next scheduled refresh. Can be null if no further refresh has been scheduled.  <br/> |
   
**Keys**

|**Column**|**Description**|
|:-----|:-----|
|prinID  <br/> |Primary key.  <br/> |
|prinID  <br/> |Foreign key with lookup in tblPrincipal.prinID table.  <br/> |
   

