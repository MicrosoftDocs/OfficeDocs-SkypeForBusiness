---
title: "tblSkippedAffiliations"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 0b129b54-a7a8-42a6-9279-0e08410c06ec
description: "tblSkippedAffiliations contains the affiliations that could not be read (usually due to Active Directory Domain Services access errors)."
---

# tblSkippedAffiliations
 
tblSkippedAffiliations contains the affiliations that could not be read (usually due to Active Directory Domain Services access errors).
  
**Columns**

|**Column**|**Type**|**Description**|
|:-----|:-----|:-----|
|prinID  <br/> |int, not null  <br/> |Principal ID.  <br/> |
|affDescription  <br/> |nvarchar (256), not null  <br/> |A string identifying the affiliation.  <br/> The format is: guid:  _{0}_ uri: _{1}_> id:  _{2}_ <br/> |
|updatedBy  <br/> |int, not null  <br/> |ID of the principal that updated this row. It is always 1 (system user) because Active Directory Sync is the only source for these entries.  <br/> |
   
**Keys**

|**Column(s)**|**Description**|
|:-----|:-----|
|\<prinID, affDescription\>  <br/> |Primary key.  <br/> |
|prinID  <br/> |Foreign key with lookup in tblPrincipal.prinID table.  <br/> |
   

