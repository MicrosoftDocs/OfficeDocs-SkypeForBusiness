---
title: "Get Integration Log"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: 8856f6bc-5460-4f35-acf2-f7662f01579b
description: "Summary: Learn about the Get Integration Log operation, which is part of the Data API for Call Quality Dashboard. Call Quality Dashboard is a tool for Skype for Business Server."
---

# Get Integration Log
 
**Summary:** Learn about the Get Integration Log operation, which is part of the Data API for Call Quality Dashboard. Call Quality Dashboard is a tool for Skype for Business Server.
  
The Get Integration Log operation is part of the Data API for Call Quality Dashboard
  
## Get Integration Log

Get Integration Log operation returns a list of log entries describing the activities in QoE Cube processing.
  
This operation is disabled by default for security reasons. When disabled, it returns an empty string. To enable this operation, administrators need to configure the web.config for Data API's host web application.
  

|Method|**Request URI**|**HTTP Version**|
|:-----|:-----|:-----|
|GET  <br/> |https://\<portal\>/QoEDataService/IntegrationLog  <br/> |HTTP/1.1  <br/> |
   
 **URI Parameters** - None.
  
 **Request Headers** - No additional headers.
  
 **Request Body** - None.
  
 **Response** - The response includes an HTTP status code and a set of response headers.
  
 **Status Code** - A successful operation returns status code 200 (OK).
  
 **Response Headers** - No additional headers.
  
 **Response Body** - Below is a sample structure of log entries.
  
```
[
{"LogCategory":"<category>","LogTime":"2015-03-18T10:28:29.10","LogDescription":"<log description>"}
]
```


