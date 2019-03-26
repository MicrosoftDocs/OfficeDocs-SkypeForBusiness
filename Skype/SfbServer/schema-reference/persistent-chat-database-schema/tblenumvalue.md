---
title: "tblEnumValue"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: a33df20c-d19d-4f5c-b012-29dab8fb9200
description: "tblEnumValue is a hardcoded table that contains the Visibility and Behavior values of the attributes that are used in the Node table."
---

# tblEnumValue
 
tblEnumValue is a hardcoded table that contains the Visibility and Behavior values of the attributes that are used in the Node table.
  
**Columns**

|**Column**|**Type**|**Description**|
|:-----|:-----|:-----|
|valueID  <br/> |smallint, not null  <br/> |ID of the value.  <br/> |
|attributeID  <br/> |smallint, not null  <br/> |ID of the attribute.  <br/> |
|attributeValue  <br/> |nvarchar (256), not null  <br/> |Name of the value.  <br/> |
   
**Keys**

|**Column**|**Description**|
|:-----|:-----|
|valueID  <br/> |Primary key.  <br/> |
|attributeID  <br/> |Foreign key with lookup in tblEnumAttribute.attributeID table.  <br/> |
   
**Table Values**

|**valueID**|**attributeID**|**attributeValue**|
|:-----|:-----|:-----|
|2  <br/> |1  <br/> |private  <br/> |
|3  <br/> |1  <br/> |scope  <br/> |
|4  <br/> |2  <br/> |normal  <br/> |
|5  <br/> |2  <br/> |auditorium  <br/> |
|6  <br/> |1  <br/> |open  <br/> |
   
## See also

[tblNode](tblnode.md)
