---
title: "ClientVersions table in Skype for Business Server 2015"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/9/2015
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 542316cf-a6db-4d52-ab28-8bf6d27a3b48
description: "The ClientVersions table is a supporting table that stores a list of the various client types and versions that have participated in sessions recorded in the database. Each record in the table represents one client version."
---

# ClientVersions table in Skype for Business Server 2015
 
The ClientVersions table is a supporting table that stores a list of the various client types and versions that have participated in sessions recorded in the database. Each record in the table represents one client version.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**VersionId** <br/> |**int** <br/> |Primary  <br/> |Unique number identifying this client type and version.  <br/> |
|**Version** <br/> |**nvarchar(256)** <br/> ||Version name.  <br/> |
|**ClientType** <br/> |int  <br/> ||Specifies the type of client used in the session. See the [UserAgentDef table](useragentdef.md) for more information. <br/> This field was introduced in Microsoft Lync Server 2013.  <br/> |
   

