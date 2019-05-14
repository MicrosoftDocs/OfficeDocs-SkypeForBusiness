---
title: "Get Sub-Items"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: 0542eba9-3dda-40de-bba8-095d22825e4e
description: "Summary: Learn about the Get Sub-Items operation, which is part of the Item Service. The Item Service is part of the Repository API for Call Quality Dashboard. Call Quality Dashboard is a tool for Skype for Business Server."
---

# Get Sub-Items
 
**Summary:** Learn about the Get Sub-Items operation, which is part of the Item Service. The Item Service is part of the Repository API for Call Quality Dashboard. Call Quality Dashboard is a tool for Skype for Business Server.
  
The Get Sub-Items operation is part of the Item Service in the Repository API for Call Quality Dashboard.
  
## Get Sub-Items

Get Sub-Items returns a specific Item's sub-items.
  

|**Method**|**Request URI**|**HTTP Version**|
|:-----|:-----|:-----|
|GET  <br/> |https://\<portal\>/QoERepositoryService/repository/item/{itemId}/subitem  <br/> |HTTP/1.1  <br/> |
   
 **URI Parameters** - None.
  
 **Request Headers** - No additional headers.
  
 **Request Body** - None.
  
 **Response** - The response includes an HTTP status code and a set of response headers.
  
 **Status Code** - A successful operation returns status code 200 (OK). If a specified user ID is not found, it returns status code 404 (Not Found).
  
 **Response Headers** - No additional headers.
  
 **Response Body** - Below is a sample response payload in JSON.
  
> [!NOTE]
> An array of Item object is returned. 
  
```
[{
"itemId": 1653,
"userId": 0,
"type": "application/json"
},
{
"itemId": 1710,
"userId": 0,
"type": "json"
}]
```

The Item object returned by Sub-Items operation only contains the following three fields. 
  
 *itemId*  - ID of the item.
  
 *userId*  - ID of the User who owns this Item.
  
 *type*  - The type of the content. This field is set by the applications.
  
> [!NOTE]
>  `Content` and `subItems` fields are not included in the response to reduce the amount of data transmitted over the network.
  

