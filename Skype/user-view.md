---
title: User view
ms.prod: SKYPEFORBUSINESS
ms.assetid: 796f77e6-1da6-4969-b18b-3537209a1fe4
---


# User view
[]
The User view stores information about users who have been involved in calls or sessions that have records in the database. This view was introduced in Microsoft Lync Server 2013.
  
    
    



|**Column**|**Data Type**|**Details**|
|:-----|:-----|:-----|
|UserId  <br/> |int  <br/> |Unique number identifying this user.  <br/> |
|UserUri  <br/> |nvarchar(450)  <br/> |Uri of the user.  <br/> |
|TenantKey  <br/> |uniqueidentifier  <br/> |Tenant of user. See the  [Tenants table](tenants-table.md) for more information. <br/> |
|UriType  <br/> |nvarchar(256)  <br/> |Type of user URI. See the  [UriTypes table](uritypes-table.md) for more information. <br/> |
   

