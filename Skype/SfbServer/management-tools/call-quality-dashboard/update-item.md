---
title: "Update Item"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: b1c15c56-cdae-4f3e-838a-52f0940cf729
description: "Summary: Learn about the Update Item operation, which is part of the Item Service. The Item Service is part of the Repository API for Call Quality Dashboard. Call Quality Dashboard is a tool for Skype for Business Server."
---

# Update Item
 
**Summary:** Learn about the Update Item operation, which is part of the Item Service. The Item Service is part of the Repository API for Call Quality Dashboard. Call Quality Dashboard is a tool for Skype for Business Server.
  
The Update Item operation is part of the Item Service in the Repository API for Call Quality Dashboard.
  
## Update Item

Update Item updates a specific item in the repository.
  

|**Method**|**Request URI**|**HTTP Version**|
|:-----|:-----|:-----|
|PUT  <br/> |https://\<portal\>/QoERepositoryService/repository/item/{itemId}  <br/> |HTTP/1.1  <br/> |
   
 **URI Parameters** - None.
  
 **Request Headers** -Content-Type: application/json.
  
 **Request Body** - JSON.
  
Sample request payload:
  
```
{
  content : "{ 'Product' : 'New Product Name'",
  type: "application/json"
}
```

 *content*  JSON formatted data to be stored as the new content of an existing sub-Item. Technically, a repository can store any content of any schema, but when used for Call Quality Dashboard, it should be either a report or a query. *type*  Always specify "application/json" for Call Quality Dashboard.
  
 **Response** - The response includes an HTTP status code and a set of response headers.
  
 **Status Code** - A successful operation returns status code 204 (No Content). If a specified item ID is not found, it returns status code 404 (Not Found).
  
> [!IMPORTANT]
> "No Content" is not an error status. It means that a response did not return anything in the body (in contrast, 200 OK returns content in Body). It indicates that the Item was successfully updated. 
  
 **Response Headers** - None.
  
 **Response Body** - None.
  

