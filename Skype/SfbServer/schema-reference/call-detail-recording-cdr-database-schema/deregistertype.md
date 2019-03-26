---
title: "DeRegisterType table in Skype for Business Server 2015"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 09148118-6209-4fd7-a494-99118689a245
description: "The DeRegisterType table is a static table that stores the list of possible user de-registers types, such as 'client initiated', 'registration expired', or 'client stopped responding.'"
---

# DeRegisterType table in Skype for Business Server 2015
 
The DeRegisterType table is a static table that stores the list of possible user de-registers types, such as 'client initiated', 'registration expired', or 'client stopped responding.'
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**DeRegisterTypeId** <br/> |tinyint  <br/> |Primary  <br/> ||
|**DeRegisterReason** <br/> |nvarchar(256)  <br/> || Allowed values: <br/>  0 -- Unknown <br/>  1 -- Client Initiated Deregistration <br/>  2 -- Registration Expired <br/>  3 - Client crashed <br/>  4 -- User Attributes Changed <br/>  5 - Preferred Registrar Changed <br/>  6 -- Legacy Client In Survival Mode <br/> |
   

