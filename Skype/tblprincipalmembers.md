---
title: tblPrincipalMembers
ms.prod: SKYPEFORBUSINESS
ms.assetid: 9a3e24cf-6ef7-4b82-99fc-50ba41800b6f
---


# tblPrincipalMembers
[]
tblPrincipalMembers contains principal memberships.
  
    
    


**Columns**


|**Column**|**Type**|**Description**|
|:-----|:-----|:-----|
|prinID  <br/> |int, not null  <br/> |Principal ID.  <br/> |
|memberADPath  <br/> |nvarchar (384), not null  <br/> |Distinguished name of a member. A member does not have to be a principal (in tblPrincipal table).  <br/> |
   

**Keys**


|**Column**|**Description**|
|:-----|:-----|
|<prinID, memberADPath>  <br/> |Primary key.  <br/> |
|prinID  <br/> |Foreign key with lookup in tblPrincipal.prinID.  <br/> |
   

