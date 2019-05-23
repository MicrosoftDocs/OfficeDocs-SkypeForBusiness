---
title: "ErrorCategory table in Skype for Business Server 2015"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 10/20/2015
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 0fde3b73-9a2f-44dd-b8dc-6df512303ff1
description: "The ErrorCategory table contains the friendly name for each Skype for Business Server 2015 diagnostic classification. By default, Skype for Business Server 2015 uses the following classifications:"
---

# ErrorCategory table in Skype for Business Server 2015
 
The ErrorCategory table contains the friendly name for each Skype for Business Server 2015 diagnostic classification. By default, Skype for Business Server 2015 uses the following classifications:
  
- 0 -- Success
    
- 1 -- Expected failure
    
- 2 - Unexpected failure
    
This table was introduced in Microsoft Lync Server 2013.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**CategoryId** <br/> |tinyint  <br/> |Primary  <br/> |Unique identifier for the classification.  <br/> |
|**Name** <br/> |nvarchar(256)  <br/> || Value and friendly name assigned to the classification. Allowed values are: <br/>  0 -- Success <br/>  1 -- Expected failure <br/>  2 - Unexpected failure <br/> |
   

