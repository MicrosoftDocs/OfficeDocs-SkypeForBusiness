---
title: "Get User Setting"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: 16611a55-79fb-487a-a936-20caca829f87
description: "Summary: Learn about the Get User Setting operation, which is part of the User Settings Service. The User Settings Service is part of the Repository API for Call Quality Dashboard. Call Quality Dashboard is a tool for Skype for Business Server."
---

# Get User Setting
 
**Summary:** Learn about the Get User Setting operation, which is part of the User Settings Service. The User Settings Service is part of the Repository API for Call Quality Dashboard. Call Quality Dashboard is a tool for Skype for Business Server.
  
The Get User Setting operation is part of the User Settings Service in the Repository API for Call Quality Dashboard.
  
## Get User Setting

Get User Setting returns a single user setting.
  

|**Method**|**Request URI**|**HTTP Version**|
|:-----|:-----|:-----|
|GET  <br/> |https://\<portal\>/QoERepositoryService/repository/user/{userId}/setting/{key}  <br/> |HTTP/1.1  <br/> |
   
 **URI Parameters** - None.
  
 **Request Headers** - No additional headers.
  
 **Request Body** - None.
  
 **Response** - The response includes an HTTP status code and a set of response headers.
  
 **Status Code** - A successful operation returns status code 200 (OK).
  
 **Response Headers** - No additional headers.
  
 **Response Body** - Below is a sample response payload in JSON.
  
```
{
"userId": 6,
"key": "ShowDescriptions",
"value": "true"
}
```

 *userId*  - ID of the user.
  
 *key*  - Key of the setting.
  
 *value*  - Value of the setting.
  

