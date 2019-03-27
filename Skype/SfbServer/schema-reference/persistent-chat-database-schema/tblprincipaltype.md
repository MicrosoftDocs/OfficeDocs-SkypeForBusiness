---
title: "tblPrincipalType"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 32e1c1d6-80f4-4624-bf4e-b4c77d3982fa
description: "tblPrincipalType contains principal types to categorize what is in the tblPrincipal table."
---

# tblPrincipalType
 
tblPrincipalType contains principal types to categorize what is in the tblPrincipal table.
  
**Columns**

|**Column**|**Type**|**Description**|
|:-----|:-----|:-----|
|ptypeID  <br/> |smallint, not null  <br/> |Principal type ID.  <br/> |
|ptypeDesc  <br/> |nvarchar (256), not null  <br/> |Description of the type.  <br/> |
|ptypeIsSystemUser  <br/> |bit, not null  <br/> |True if the type corresponds to the principals that are used for internal purposes.  <br/> |
|ptypeIsUser  <br/> |bit, not null  <br/> |True if the type is a user type.  <br/> |
   
**Key**

|**Column**|**Description**|
|:-----|:-----|
|ptypeID  <br/> |Primary key.  <br/> |
   
**Principal Values**

|**ID**|**Role**|**Description**|**User**|
|:-----|:-----|:-----|:-----|
|1  <br/> |Any  <br/> |Generic principal with no known type. Not used in tblPrincipal table.  <br/> ||
|2  <br/> |AnyUser  <br/> |Generic principal of user type. Not used in tblPrincipal table.  <br/> |Yes  <br/> |
|3  <br/> |AnyGroup  <br/> |Generic principal with group semantic. Not used in tblPrincipal table.  <br/> ||
|4  <br/> |SystemUser  <br/> |Principal used internally by Persistent Chat Server.  <br/> ||
|5  <br/> |User  <br/> |Regular user.  <br/> |Yes  <br/> |
|8  <br/> |DC  <br/> |Active Directory Domain Services domain controller.  <br/> ||
|9  <br/> |Group  <br/> |Active Directory security group.  <br/> ||
|10  <br/> |Folder  <br/> |Active Directory container or organizational unit.  <br/> ||
   
## See also

[tblPrincipal](tblprincipal.md)
