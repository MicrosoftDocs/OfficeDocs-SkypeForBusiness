---
title: ErrorDef table in Skype for Business Server 2015
ms.prod: SKYPEFORBUSINESS
ms.assetid: 6acf3b86-da61-4923-9812-300db6f66dec
---


# ErrorDef table in Skype for Business Server 2015
[]
The ErrorDef table stores information about each type of error that may occur. Each record is one type of error.
  
    
    



|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**ErrorId** <br/> |int  <br/> |Primary  <br/> |Unique ID number identifying this type of error.  <br/> |
|**ResponseCode** <br/> |int  <br/> | <br/> |Standard SIP response code associated with this error.  <br/> |
|**MsDiagId** <br/> |int  <br/> | <br/> |Microsoft Diagnostic ID.  <br/> |
|**CallTypeId** <br/> |Int  <br/> |Foreign  <br/> |Type of the call. See the  [CallType table in Skype for Business Server 2015](calltype-table-in-skype-for-business-server-2015.md) for more information. <br/> |
|**RequestType** <br/> |varbinary(33)  <br/> | <br/> |Type of request that failed.  <br/> This data can be converted to text format by using this syntax:  <br/>  `cast(cast(RequestType as varbinary(max)) as varchar(max))` <br/> |
|**ContentType** <br/> |varbinary(257)  <br/> | <br/> |Content type of the request that failed.  <br/> This data can be converted to text format by using this syntaxt:  <br/>  `cast(cast(ContentType as varbinary(max)) as varchar(max))` <br/> |
   

