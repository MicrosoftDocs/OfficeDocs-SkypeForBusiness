---
title: "tblPrincipalAffiliations"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 45fd8484-5837-44d2-85bb-45c83546607c
description: "tblPrincipalAffiliations contains the principal affiliations that describe memberships in locations, including Active Directory Domain Services security groups, in Active Directory containers, in domains."
---

# tblPrincipalAffiliations
 
tblPrincipalAffiliations contains the principal affiliations that describe memberships in locations, including Active Directory Domain Services security groups, in Active Directory containers, in domains.
  
**Columns**

|**Column**|**Type**|**Description**|
|:-----|:-----|:-----|
|principalID  <br/> |int, not null  <br/> |ID of the affiliated principal.  <br/> |
|affiliationID  <br/> |int, not null  <br/> |ID of the principal representing the affiliation. Each principal (except system-user-types) has a self-affiliation as well.  <br/> |
|index  <br/> |int, not null  <br/> |Index. The value for self-affiliations is -1, and for the other affiliations it increases sequentially from 1 within each \<principalID, affiliationId\> bucket.  <br/> |
|updatedBy  <br/> |int, not null  <br/> |Principal that did the latest update. This is usually 1, which means Active Directory Sync.  <br/> |
   
**Keys**

|**Columns**|**Description**|
|:-----|:-----|
|\<principalID, index, affiliationID\>  <br/> |Primary key.  <br/> |
|principalID  <br/> |Foreign key with lookup in tblPrincipal.prinID table.  <br/> |
|affiliationID  <br/> |Foreign key with lookup in tblPrincipal.prinID table.  <br/> |
   

