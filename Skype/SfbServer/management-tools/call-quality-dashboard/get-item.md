---
title: "Get Item"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: e77bf649-d62a-4d94-80de-066ba47730cd
description: "Summary: Learn about the Get Item operation, which is part of the Item Service. The Item Service is part of the Repository API for Call Quality Dashboard. Call Quality Dashboard is a tool for Skype for Business Server."
---

# Get Item
 
**Summary:** Learn about the Get Item operation, which is part of the Item Service. The Item Service is part of the Repository API for Call Quality Dashboard. Call Quality Dashboard is a tool for Skype for Business Server.
  
The Get Item operation is part of the Item Service in the Repository API for Call Quality Dashboard.
  
## Get Item

Get Item returns a specific item in the repository.
  
|**Method**|**Request URI**|**HTTP Version**|
|:-----|:-----|:-----|
|GET  <br/> |https://\<portal\>/QoERepositoryService/repository/item/{itemId}  <br/> |HTTP/1.1  <br/> |
   
 **URI Parameters** - None.
  
 **Request Headers** - No additional headers.
  
 **Request Body** - None.
  
 **Response** - The response includes an HTTP status code and a set of response headers.
  
 **Status Code** - A successful operation returns status code 200 (OK). If a specified item ID is not found, it returns status code 404 (Not Found).
  
 **Response Headers** - No additional headers.
  
 **Response Body** - Below is a sample response payload in JSON.
  
```
{
"itemId": 1652,
"userId": 0,
"content": "{\"Title\":\"All Audio Streams\",...}",
"type": "application/json",
"subItemIds": [1653, 1710]
}
```

 *itemId*  - ID of the item.
  
 *userId*  - ID of the user who owns this item.
  
 *content*  - The application-specific content.
  
 *type*  - The type of the content. This field is set by the applications.
  
 *subItemIds*  - The IDs of sub-Items, if any. This is a short-circuit of Get Sub-Items operation to save a call. Applications can alternatively obtain the same information using Get Sub-Items operation.
  

