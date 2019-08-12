---
title: "Get User"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: 52b89a4b-a0bd-493d-bb5e-e21904eb8e48
description: "Summary: Learn about the Get User operation, which is part of the User Service. The User Service is part of the Repository API for Call Quality Dashboard. Call Quality Dashboard is a tool for Skype for Business Server."
---

# Get User
 
**Summary:** Learn about the Get User operation, which is part of the User Service. The User Service is part of the Repository API for Call Quality Dashboard. Call Quality Dashboard is a tool for Skype for Business Server.
  
The Get Users operation is part of the User Service in the Repository API for Call Quality Dashboard.
  
## Get User

Get User returns a user record from the repository.
  
|**Method**|**Request URI**|**HTTP Version**|
|:-----|:-----|:-----|
|GET  <br/> |https://\<portal\>/QoERepositoryService/repository/user/{userId}  <br/> |HTTP/1.1  <br/> |
   
 **URI Parameters** - None.
  
 **Request Headers** - No additional headers.
  
 **Request Body** - None.
  
 **Response** - The response includes an HTTP status code and a set of response headers.
  
 **Status Code** - A successful operation returns status code 200 (OK). If a specified user ID is not found, it returns status code 404 (Not Found).
  
 **Response Headers** - No additional headers.
  
 **Response Body** - Below is a sample response payload in JSON.
  
```
{
"userId": 0,
"loginName": "system",
"defaultItemId": 1655
}
```

 *userId*  - ID of the user.
  
 *loginName*  - External user identification for regular users. If Windows Authentication is used for authenticating users, then this may be a FQDN of the user.
  
 *defaultItemId*  - ID of the default Item for this user. The default Item is the top-most Item that is associated to the user. All other Items this user owns can be navigated from the default Item.
  
> [!NOTE]
> Supply the  `defaultItemId` value to Get Item operation to retrieve the details of the default Item.
  

