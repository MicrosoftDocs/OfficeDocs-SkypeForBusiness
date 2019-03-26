---
title: "Clear Cache"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: 08648b16-7a64-41d8-9577-5000a20fce46
description: "Summary: Learn about the Clear Cache operation, which is part of the Data API for Call Quality Dashboard. Call Quality Dashboard is a tool for Skype for Business Server."
---

# Clear Cache
 
**Summary:** Learn about the Clear Cache operation, which is part of the Data API for Call Quality Dashboard. Call Quality Dashboard is a tool for Skype for Business Server.
  
The Clear Cache operation is part of the Data API for Call Quality Dashboard.
  
## Clear Cache

Clear Cache operation deletes the cache on server for queries and data. This will reset the cache and we will get fresh data from QoE Cube afterward for new requests.
  

|**Method**|**Request URI**|**HTTP Version**|
|:-----|:-----|:-----|
|POST  <br/> |https://\<portal\>/QoEDataService/ClearCache  <br/> |HTTP/1.1  <br/> |
   
 **URI Parameters** - None.
  
 **Request Headers** - No additional headers.
  
 **Request Body** - None.
  
 **Response** - The response includes an HTTP status code and a set of response headers.
  
 **Status Code** - A successful operation returns status code 200 (OK).
  
 **Response Headers** - No additional headers.
  
 **Response Body** - None.
  

