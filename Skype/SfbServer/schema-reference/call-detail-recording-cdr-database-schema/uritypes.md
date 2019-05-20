---
title: "UriTypes table"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 10/20/2015
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 77c4dfae-1b29-4e81-ba05-609e61643998
description: "The UriTypes Table contains the different URI (Uniform resource identifier) types monitored in Skype for Business Server 2015."
---

# UriTypes table
 
The UriTypes Table contains the different URI (Uniform resource identifier) types monitored in Skype for Business Server 2015.

When the CDR DB is created, two records to represent PhoneUri and UserUri are created, and records created after that are dynamically assigned UriTypeId. 
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**UriTypeId** <br/> |tinyint  <br/> |Primary  <br/> |Unique identifier assigned to a URI type.  <br/> Possible values - 0 to 255 |
|**UriType** <br/> |nvarchar(256)  <br/> || Descriptions of the different URI types. The following values are pre-assigned: <br/>  1 - Phone Uri <br/>  0 - User Uri <br/> <br/>  Other possible types include: <br/>conf:applicationsharing <br/> conf:audio-video<br/> conf:chat<br/>    conf:focus<br/>   mras<br/>
