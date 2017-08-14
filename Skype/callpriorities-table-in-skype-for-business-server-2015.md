---
title: CallPriorities table in Skype for Business Server 2015
ms.prod: SKYPEFORBUSINESS
ms.assetid: 043b63ae-2d64-4f38-a0df-18aa08d6caf5
---


# CallPriorities table in Skype for Business Server 2015
[]
The CallPriorities table is a static table that stores the list of possible call priorities, such as 'emergency', 'urgent', or 'normal'.
  
    
    



|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**PriorityId** <br/> |tinyint  <br/> |Primary  <br/> ||
|**Priority** <br/> |nvarchar(256)  <br/> || Allowed values: <br/>  0 - Unknown <br/>  1 - Non-Urgent <br/>  2 - Normal <br/>  3 - Urgent <br/>  4 - Emergency <br/> |
   

