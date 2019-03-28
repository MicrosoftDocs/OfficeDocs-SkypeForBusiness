---
title: "tblPrincipal"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 10/20/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 79a24502-b4ce-41f0-8979-8caddf535338
description: "tblPrincipal contains all principals, including users, folders, and groups."
---

# tblPrincipal
 
tblPrincipal contains all principals, including users, folders, and groups.
  
**Columns**

|**Column**|**Type**|**Description**|
|:-----|:-----|:-----|
|prinID  <br/> |int, not null  <br/> |Principal ID.  <br/> |
|prinGuid  <br/> |GUID, not null  <br/> |Principal GUID. This is broadly used as an alternate primary key because its meaning crosses over into the Active Directory Domain Services space. (The GUID for a cached principal is equal to the corresponding Active Directory object GUID.)  <br/> |
|prinUri  <br/> |nvarchar (256), not null  <br/> |Principal URI. The SIP scheme is used for users, and ma-grp is used for almost everything else.  <br/> |
|prinName  <br/> |nvarchar (256)  <br/> |Common name. Used only by user types.  <br/> |
|prinDisplayName  <br/> |Nvarchar (256)  <br/> |Display name. Used only by user types.  <br/> |
|prinCompanyName  <br/> |nvarchar (256)  <br/> |Company name. Used only by user types.  <br/> |
|prinEmail  <br/> |nvarchar (256)  <br/> |Email. Used only by user types.  <br/> |
|prinADPath  <br/> |nvarchar (384)  <br/> |Domain name of the Active Directory object that the principal is a cached version of. Can be Null for types that are not Active Directory objects (such as system users).  <br/> |
|prinADUserPrincipalName  <br/> |nvarchar (256)  <br/> |User's user principal name (UPN). Used only by regular user types.  <br/> |
|prinDisabled  <br/> |smallint, not null  <br/> | 0: Principal is active. <br/>  1: Principal is disabled because user's SIP capabilities are disabled. <br/>  2: Principal is deleted because associated AD object has been deleted. <br/> |
|prinTypeID  <br/> |smallint, not null  <br/> |Principal type (from tblPrincipalType table).  <br/> |
|prinPoolID  <br/> |Int  <br/> |Skype for Business client pool assignment for the principal.  <br/> |
|prinPolicyID  <br/> |Int  <br/> |Persistent Chat Server policy value for user, if tag type policy is present.  <br/> |
|prinAddedBy  <br/> |int  <br/> |Principal ID of the creator.  <br/> |
|prinAddedOn  <br/> |bigint, not null  <br/> |Time stamp for the creation time.  <br/> |
|prinUpdatedBy  <br/> |int  <br/> |ID of the principal that last updated this.  <br/> |
|prinUpdatedOn  <br/> |bigint, not null  <br/> |Time stamp for the last update.  <br/> |
|prinVerifiedOn  <br/> |datetime, not null  <br/> |Date and time of the last Active Directory Sync refresh for the principal.  <br/> |
   
**Keys**

|**Column**|**Description**|
|:-----|:-----|
|prinID  <br/> |Primary key.  <br/> |
|prinTypeID  <br/> |Foreign key with lookup in tblPrincipalType.ptypeID table.  <br/> |
   

