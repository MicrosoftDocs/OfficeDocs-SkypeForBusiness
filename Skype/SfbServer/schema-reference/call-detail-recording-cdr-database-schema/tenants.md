---
title: "Tenants table"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/9/2015
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: c1b070c1-2c59-4ca9-910b-43f673f97fda
description: "The Tenants table is a supporting table that stores a list of the various tenants. Each record in the table represents one tenant."
---

# Tenants table
 
The Tenants table is a supporting table that stores a list of the various tenants. Each record in the table represents one tenant.
  
> [!NOTE]
> In on-premises deployment, CDR uses the build-in Tenant ID to indicate different authentication type, such as public IM connectivity, Federated and Anonymous. 
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**TenantId** <br/> |int  <br/> |Primary  <br/> |Unique number identifying this Tenant ID.  <br/> |
|**TenantKey** <br/> |nvarchar(256)  <br/> || Allowed values: <br/>  00000000-0000-0000-0000-000000000000 - Enterprise <br/>  00000000-0000-0000-0000-000000000001 - Federated <br/>  00000000-0000-0000-0000-000000000002 - Anonymous <br/>  00000000-0000-0000-0000-000000000003 - Public IM connectivity <br/> |
   

