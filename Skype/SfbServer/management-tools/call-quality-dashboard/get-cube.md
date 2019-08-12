---
title: "Get Cube"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: c8eeb387-dc1e-44e0-bbf9-a566f8bda551
description: "Summary: Learn about the Get Cube operation, which is part of the Data API for Call Quality Dashboard. Call Quality Dashboard is a tool for Skype for Business Server."
---

# Get Cube
 
**Summary:** Learn about the Get Cube operation, which is part of the Data API for Call Quality Dashboard. Call Quality Dashboard is a tool for Skype for Business Server.
  
The Get Cube operation is part of the Data API for Call Quality Dashboard.
  
## Get Cube

Get Cube operation returns the list of available dimensions and measurements.
  

|**Method**|**Request URI**|**HTTP Version**|
|:-----|:-----|:-----|
|GET  <br/> |https://\<portal\>/QoEDataService/CubeStructure  <br/> |HTTP/1.1  <br/> |
   
 **URI Parameters** - None.
  
 **Request Headers** - No additional headers.
  
 **Request Body** - None.
  
 **Response** - The response includes an HTTP status code and a set of response headers.
  
 **Status Code** - A successful operation returns status code 200 (OK).
  
 **Response Headers** - No additional headers.
  
 **Response Body** - Below is a sample response payload in JSON.
  
> [!NOTE]
> This sample is only showing first two elements of each groups of Cube elements. 
  
```
{
"Kpis": [{
"FriendlyName": "Poor Trend Month",
"DataModelName": "[KPIValue].Poor Trend Month",
"Description": null
},
{
"FriendlyName": "Poor Rate Trend Month",
"DataModelName": "[KPIValue].Poor Rate Trend Month",
"Description": null
}],
"Dimensions": [{
"Category": "Access Location Pair",
"Attributes": [{
"FriendlyName": "Location Pair",
"DataModelName": "[Access Location Pair].[Location Pair]",
"Description": "Description of Location Pair"
}]
},
{
"Category": "Audio Bandwidth Est",
"Attributes": [{
"FriendlyName": "Metric",
"DataModelName": "[Audio Bandwidth Est].[Metric]",
"Description": "Description of Metric"
}]
}],
"Measurements": [{
"FriendlyName": "Audio Streams Count",
"DataModelName": "[Measures].[Audio Streams Count]",
"Description": "Description of Audio Streams Count"
},
{
"FriendlyName": "Audio Good Streams JPDR Count",
"DataModelName": "[Measures].[Audio Good Streams JPDR Count]",
"Description": "Description of Audio Good Streams JPDR Count"
}]
}
```

 *KPIs*  - Reserved. The KPIs section of a request payload allows Run Query operation to return values for the KPIs defined in the cube. No KPIs exist in the QoE Cube yet.
  
 *Dimensions*  - The list of dimensions that may be used in Filters and Dimensions sections of a request payload for Run Query operation. To use a dimension in a filter expression, you need to specify a dimension member, which can be obtained using Get Dimension Members operation.
  
 *Measurements*  - The list of measurements that may be used in Measurements section of a request payload for Run Query operation.
  

