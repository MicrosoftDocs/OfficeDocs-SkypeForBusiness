---
title: "Get Item Ancestors"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: d39b1dbc-1514-43ec-8593-9f23b3fcae62
description: "Summary: Learn about the Get Item Ancestors operation, which is part of the Item Service. The Item Service is part of the Repository API for Call Quality Dashboard. Call Quality Dashboard is a tool for Skype for Business Server."
---

# Get Item Ancestors
 
**Summary:** Learn about the Get Item Ancestors operation, which is part of the Item Service. The Item Service is part of the Repository API for Call Quality Dashboard. Call Quality Dashboard is a tool for Skype for Business Server.
  
The Get Item Ancestors operation is part of the Item Service in the Repository API for Call Quality Dashboard.
  
## Get Item Ancestors

Get Item Ancestors returns a specific items ancestors from the repository.
  

|**Method**|**Request URI**|**HTTP Version**|
|:-----|:-----|:-----|
|GET  <br/> |https://\<portal\>/QoERepositoryService/repository/itemAncestors/{itemId}  <br/> |HTTP/1.1  <br/> |
   
 **URI Parameters** - None.
  
 **Request Headers** - No additional headers.
  
 **Request Body** - None.
  
 **Response** - The response includes an HTTP status code and a set of response headers.
  
 **Status Code** - A successful operation returns status code 200 (OK). If a specified user ID is not found, it returns status code 404 (Not Found).
  
 **Response Headers** - No additional headers.
  
 **Response Body** - Below is a sample response payload in JSON.
  
```
[{
"item1": 1653,
"item2": 0,
"item3": "Audio Streams Monthly Trend"
},
{
"item1": 1652,
"item2": 1,
"item3": "All Audio Streams"
}]
```

 *Item1*  - ID of the item.
  
 *Item2*  - Depth is the distance from the Item. 0 is the immediate parent.
  
 *Item3*  - Title of the item.
  

