---
title: "Phones table"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 41cb356d-9cc8-42b6-ac23-98a61b25aadc
description: "The Phones table is a supporting table. Each record in the table stores information about one phone number involved in VoIP calls that have records in the database."
---

# Phones table
 
The Phones table is a supporting table. Each record in the table stores information about one phone number involved in VoIP calls that have records in the database.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**PhoneId** <br/> |int  <br/> |Primary  <br/> |Unique number identifying this phone.  <br/> |
|**PhoneUri** <br/> |nvarchar(450)  <br/> | <br/> |Phone number.  <br/> |
|**NextUpdateTS** <br/> |dateTime  <br/> ||Time stamp (for internal use only).  <br/> This field was introduced in Microsoft Lync Server 2013.  <br/> |
   

