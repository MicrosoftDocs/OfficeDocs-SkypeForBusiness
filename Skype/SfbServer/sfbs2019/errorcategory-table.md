---
title: "ErrorCategory table in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 0fde3b73-9a2f-44dd-b8dc-6df512303ff1
description: "The ErrorCategory table contains the friendly name for each Microsoft Lync Server 2013 diagnostic classification. By default, Lync Server 2013 uses the following classifications:"
---

# ErrorCategory table in Lync Server 2013
[]
The ErrorCategory table contains the friendly name for each Microsoft Lync Server 2013 diagnostic classification. By default, Lync Server 2013 uses the following classifications:
  
- 0 -- Success
    
- 1 -- Expected failure
    
- 2 - Unexpected failure
    
This table was introduced in Microsoft Lync Server 2013.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**CategoryId** <br/> |tinyint  <br/> |Primary  <br/> |Unique identifier for the classification.  <br/> |
|**Name** <br/> |nvarchar(256)  <br/> || Value and friendly name assigned to the classification. Allowed values are:  <br/>  0 -- Success  <br/>  1 -- Expected failure  <br/>  2 - Unexpected failure  <br/> |
   

