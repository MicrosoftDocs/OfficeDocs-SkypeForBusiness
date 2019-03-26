---
title: "tblADUpdates"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: ba19fa16-4d2d-4635-ac32-f93e09469546
description: "tblADUpdates contains Active Directory Domain Services changes that have not yet been processed by the later Active Directory Sync steps."
---

# tblADUpdates
 
tblADUpdates contains Active Directory Domain Services changes that have not yet been processed by the later Active Directory Sync steps.
  
**Columns**

|**Column**|**Type**|**Description**|
|:-----|:-----|:-----|
|prinGuid  <br/> |GUID, not null  <br/> |Principal GUID of the object that changed.  <br/> |
|prinADPath  <br/> |nvarchar (384), not null  <br/> |Distinguished name of the object.  <br/> |
|prinAttributesChanged  <br/> |bit, not null  <br/> |True if at least one attribute of the object changed.  <br/> |
|prinMembersChanged  <br/> |bit, not null  <br/> |True if the membership changed.  <br/> |
|prinAffiliationsChanged  <br/> |bit, not null  <br/> |Not used.  <br/> |
|prinDeleted  <br/> |bit, not null  <br/> |True if the object was deleted.  <br/> |
|lastUpdated  <br/> |datetime, not null  <br/> |Time stamp of when the row was inserted.  <br/> |
   

