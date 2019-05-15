---
title: "User table"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 2/1/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 6b52047e-286d-47ab-b7bc-a9b266f62d82
description: "The User table is a supporting table that stores a list of the various users who have participated in sessions recorded in the database. Each record in the table represents one user."
---

# User table
 
The User table is a supporting table that stores a list of the various users who have participated in sessions recorded in the database. Each record in the table represents one user.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**UserKey** <br/> |int  <br/> |Primary  <br/> |Unique number identifying this user.  <br/> |
|**URI** <br/> |nvarchar(450)  <br/> |Unique  <br/> |URI string.  <br/> |
|**URIType** <br/> |int  <br/> ||1 is unknown URI type.  <br/> 2 is user URI.  <br/> 4 is conference URI.  <br/> 8 is phone URI.  <br/> |
|**TenantKey** <br/> |int  <br/> |Foreign  <br/> |Tenant of the user, referenced from tenant table.  <br/> |
|**LastPoorCallTime** <br/> |datetime  <br/> ||Latest time stamp when the user had a poor audio call.  <br/> |
|**NextUpdateTS** <br/> |datetime  <br/> ||For internal use only.  <br/> |
   

