---
title: "Get Users"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: 87d34baf-4c31-468d-b8f7-4faca0bc7a54
description: "Summary: Learn about the Get Users operation, which is part of the User Service. The User Service is part of the Repository API for Call Quality Dashboard. Call Quality Dashboard is a tool for Skype for Business Server."
---

# Get Users
 
**Summary:** Learn about the Get Users operation, which is part of the User Service. The User Service is part of the Repository API for Call Quality Dashboard. Call Quality Dashboard is a tool for Skype for Business Server.
  
The Get Users operation is part of the User Service in the Repository API for Call Quality Dashboard.
  
## Get Users

Get Users returns a list of users in the repository.
  
|**Method**|**Request URI**|**HTTP Version**|
|:-----|:-----|:-----|
|GET  <br/> |https://\<portal\>/QoERepositoryService/repository/user  <br/> |HTTP/1.1  <br/> |
   
 **URI Parameters** - None.
  
 **Request Headers** - No additional headers.
  
 **Request Body** - None.
  
 **Response** - The response includes an HTTP status code and a set of response headers.
  
 **Status Code** - A successful operation returns status code 200 (OK).
  
 **Response Headers** - No additional headers.
  
 **Response Body** - Below is a sample response payload in JSON.
  
> [!NOTE]
> An array of User objects is returned. For details about the User object, see Get User. 
  
```
[{
"userId": 0,
"loginName": "system",
"defaultItemId": 1652
},
{
"userId": 1,
"loginName": "SAMPLEDOMAIN\\testuser1",
"defaultItemId": 1652
},
{
"userId": 2,
"loginName": "SAMPLEDOMAIN\\testuser2",
"defaultItemId": 1774
}]
```


