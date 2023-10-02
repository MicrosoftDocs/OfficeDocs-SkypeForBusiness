---
title: "Roles table"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 3/9/2015
audience: ITPro
ms.topic: article
ms.service: skype-for-business-server
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.assetid: e8eb8a10-26b5-488b-bc8c-f9ef93f98bdb
description: "The Roles table is a static table that stores the list of possible conference roles, such as attendee and presenter."
---

# Roles table
 
The Roles table is a static table that stores the list of possible conference roles, such as attendee and presenter.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**RoleId** <br/> |tinyint  <br/> |Primary  <br/> ||
|**Role** <br/> |nvarchar(256)  <br/> || Allowed values: <br/>  0 - Unknown <br/>  1 - Presenter <br/>  2 - Attendee <br/> |
   

