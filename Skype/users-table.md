---
title: Users table
ms.prod: SKYPEFORBUSINESS
ms.assetid: a8d71373-4b57-4245-9f02-f7fc0d9fcd3c
---


# Users table
[]
The Users table is a supporting table. Each record in the table stores information about one user involved in calls or sessions that have records in the database.
  
    
    



|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**NextUpdateTS** <br/> |datetime  <br/> ||Time stamp for internal use.  <br/> |
|**UserId** <br/> |int  <br/> |Primary  <br/> |Unique number identifying this user.  <br/> |
|**UserUri** <br/> |nvarchar(450)  <br/> | <br/> |User URI.  <br/> |
|**TenantId** <br/> |int  <br/> |Foreign  <br/> |This user's Tenant ID. See the  [Tenants table](tenants-table.md) for more information. <br/> |
|**UriTypeId** <br/> |int  <br/> |Foreign  <br/> |This user's URI type. See the  [UriTypes table](uritypes-table.md) for more information. <br/> |
   

