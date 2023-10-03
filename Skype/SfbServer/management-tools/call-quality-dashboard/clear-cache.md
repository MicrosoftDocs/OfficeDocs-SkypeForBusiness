---
ms.date: 03/17/2018
title: "Clear Cache"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
audience: ITPro
ms.topic: article
ms.service: skype-for-business-server
f1.keywords:
- NOCSH
ms.localizationpriority: medium
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
  


