---
title: "Users table"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: a8d71373-4b57-4245-9f02-f7fc0d9fcd3c
description: "The Users table is a supporting table. Each record in the table stores information about one user involved in calls or sessions that have records in the database."
---

# Users table
 
The Users table is a supporting table. Each record in the table stores information about one user involved in calls or sessions that have records in the database.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**NextUpdateTS** <br/> |datetime  <br/> ||Time stamp for internal use.  <br/> |
|**UserId** <br/> |int  <br/> |Primary  <br/> |Unique number identifying this user.  <br/> |
|**UserUri** <br/> |nvarchar(450)  <br/> | <br/> |User URI.  <br/> |
|**TenantId** <br/> |int  <br/> |Foreign  <br/> |This user's Tenant ID. See the [Tenants table](tenants.md) for more information. <br/> |
|**UriTypeId** <br/> |int  <br/> |Foreign  <br/> |This user's URI type. See the [UriTypes table](uritypes.md) for more information. <br/> |
   

