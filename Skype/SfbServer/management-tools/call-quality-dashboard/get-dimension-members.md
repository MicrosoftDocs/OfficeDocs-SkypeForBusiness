---
title: "Get Dimension Members"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: bd89bbf7-cb98-4cd8-bbfa-0484663d14db
description: "Summary: Learn about the Get Dimension Members operation. The Get Dimension Members operation is part of the Data API for Call Quality Dashboard. Call Quality Dashboard is a tool for Skype for Business Server."
---

# Get Dimension Members
 
**Summary:** Learn about the Get Dimension Members operation. The Get Dimension Members operation is part of the Data API for Call Quality Dashboard. Call Quality Dashboard is a tool for Skype for Business Server.
  
The Get Dimension Members operation is part of the Data API for Call Quality Dashboard.
  
## Get Dimension Members

Get Dimension Members operation returns the list of members of a specific dimension. It also give the ability to filter the member list and get a subset, to reduce the wire transfer cost.
  

|**Method**|**Request URI**|**HTTP Version**|
|:-----|:-----|:-----|
|POST  <br/> |https://\<portal\>/QoEDataService/DimensionMembers  <br/> |HTTP/1.1  <br/> |
   
 **URI Parameters** - None.
  
 **Request Headers** - No additional headers.
  
 **Request Body** - This contains the name of dimension we want the members for. Also max number of members returned, beside you can specify some filtering to limit the returned members.
  
```
{
"ByPassCache": false,
"DataModelName": "[StartDate].[Month]",
"SearchCaption": "",
"SearchValue": "",
"PageNumber": 0,
"PageSize": 8000
}
```

 **Response** - The response includes an HTTP status code and a set of response headers.
  
 **Status Code** - A successful operation returns status code 200 (OK).
  
 **Response Headers** - No additional headers.
  
 **Response Body** - Below is a sample response payload in JSON in response to a request for "[StartDate].[Month]" dimension.
  
> [!NOTE]
> The list is only showing a small portion of the list. 
  
```
{
"MembersCount": 493,
"Members": [["[1990-01-01T00:00:00]",
"January 1990"],
["[1990-02-01T00:00:00]",
"February 1990"],
["[1990-03-01T00:00:00]",
"March 1990"],
 
    ...
    
["[2030-10-01T00:00:00]",
"October 2030"],
["[2030-11-01T00:00:00]",
"November 2030"],
["[2030-12-01T00:00:00]",
"December 2030"],
["[2031-01-01T00:00:00]",
"January 2031"]]
}
```
