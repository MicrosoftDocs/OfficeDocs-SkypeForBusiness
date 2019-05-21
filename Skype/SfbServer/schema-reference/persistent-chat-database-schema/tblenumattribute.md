---
title: "tblEnumAttribute"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/9/2015
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 17f8b87e-36a6-4f6a-8630-7c76b61a7595
description: "tblEnumAttribute is a hardcoded table that contains the Visibility and Behavior attributes that are used in the Node table."
---

# tblEnumAttribute
 
tblEnumAttribute is a hardcoded table that contains the Visibility and Behavior attributes that are used in the Node table.
  
**Columns**

|**Column**|**Type**|**Description**|
|:-----|:-----|:-----|
|attributeID  <br/> |smallint, not null  <br/> |ID of the attribute.  <br/> |
|attributeName  <br/> |nvarchar (256), not null  <br/> |Name of the attribute.  <br/> |
   
**Key**

|**Column**|**Description**|
|:-----|:-----|
|attributeID  <br/> |Primary key.  <br/> |
   
**Table Values**

|**attributeID**|**attributeName**|
|:-----|:-----|
|1  <br/> |Visibility.  <br/> |
|2  <br/> |Behavior.  <br/> |
   
## See also

[tblNode](tblnode.md)
