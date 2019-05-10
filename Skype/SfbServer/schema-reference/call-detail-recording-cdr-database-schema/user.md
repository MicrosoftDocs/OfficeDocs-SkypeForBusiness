---
title: "User view"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 796f77e6-1da6-4969-b18b-3537209a1fe4
description: "The User view stores information about users who have been involved in calls or sessions that have records in the database. This view was introduced in Microsoft Lync Server 2013."
---

# User view
 
The User view stores information about users who have been involved in calls or sessions that have records in the database. This view was introduced in Microsoft Lync Server 2013.
  
|**Column**|**Data Type**|**Details**|
|:-----|:-----|:-----|
|UserId  <br/> |int  <br/> |Unique number identifying this user.  <br/> |
|UserUri  <br/> |nvarchar(450)  <br/> |Uri of the user.  <br/> |
|TenantKey  <br/> |uniqueidentifier  <br/> |Tenant of user. See the [Tenants table](tenants.md) for more information. <br/> |
|UriType  <br/> |nvarchar(256)  <br/> |Type of user URI. See the [UriTypes table](uritypes.md) for more information. <br/> |
   

