---
title: "Get User Settings"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: bdfe063b-e808-4f3c-884a-acbbabb9be0a
description: "Summary: Learn about the Get User Settings operation, which is part of the User Settings Service. The User Settings Service is part of the Repository API for Call Quality Dashboard. Call Quality Dashboard is a tool for Skype for Business Server."
---

# Get User Settings
 
**Summary:** Learn about the Get User Settings operation, which is part of the User Settings Service. The User Settings Service is part of the Repository API for Call Quality Dashboard. Call Quality Dashboard is a tool for Skype for Business Server.
  
The Get User Settings operation is part of the User Settings Service in the Repository API for Call Quality Dashboard.
  
## Get User Settings

Get User Settings returns a list of settings for a specified user.
  

|**Method**|**Request URI**|**HTTP Version**|
|:-----|:-----|:-----|
|GET  <br/> |https://\<portal\>/QoERepositoryService/repository/user/{userId}/setting  <br/> |HTTP/1.1  <br/> |
   
 **URI Parameters**
  
- *effective*  - Optional. This parameter applies only when the special user ID default is used. In other cases, it will be ignored. `True` returns effective user settings and `false` returns just user settings (default).
    
  **Request Headers** - No additional headers.
  
  **Request Body** - None.
  
  **Response** - The response includes an HTTP status code and a set of response headers.
  
  **Status Code** - A successful operation returns status code 200 (OK).
  
  **Response Headers** - No additional headers.
  
  **Response Body** - Below is a sample response payload in JSON.
  
```
[{
"userId": 6,
"key": "ShowDescriptions",
"value": "true"
},
{
"userId": 6,
"key": "ShowTimeStamps",
"value": "true"
}]
```
