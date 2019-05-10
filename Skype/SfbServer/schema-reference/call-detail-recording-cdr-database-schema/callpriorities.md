---
title: "CallPriorities table in Skype for Business Server 2015"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 043b63ae-2d64-4f38-a0df-18aa08d6caf5
description: "The CallPriorities table is a static table that stores the list of possible call priorities, such as 'emergency', 'urgent', or 'normal'."
---

# CallPriorities table in Skype for Business Server 2015
 
The CallPriorities table is a static table that stores the list of possible call priorities, such as 'emergency', 'urgent', or 'normal'.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**PriorityId** <br/> |tinyint  <br/> |Primary  <br/> ||
|**Priority** <br/> |nvarchar(256)  <br/> || Allowed values: <br/>  0 - Unknown <br/>  1 - Non-Urgent <br/>  2 - Normal <br/>  3 - Urgent <br/>  4 - Emergency <br/> |
   

