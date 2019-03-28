---
title: "Run Query"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: 45a77f7e-b137-462b-9146-3a0f43d8e0c7
description: "Summary: Learn about the Run Query operation, which is part of the Data API for Call Quality Dashboard. Call Quality Dashboard is a tool for Skype for Business Server."
---

# Run Query

**Summary:** Learn about the Run Query operation, which is part of the Data API for Call Quality Dashboard. Call Quality Dashboard is a tool for Skype for Business Server.

The Run Query operation is part of the Data API for Call Quality Dashboard.

## Run Query

Run Query operation provides the ability to run a query on the cube based on specified dimensions, measurements, and filters and return back the data.


|**Method**|**Request URI**|**HTTP Version**|
|:-----|:-----|:-----|
|POST  <br/> |https://\<portal\>/QoEDataService/RunQuery  <br/> |HTTP/1.1  <br/> |

 **URI Parameters** - None.

 **Request Headers** - No additional headers.

 **Request Body** - Here is a sample request payload in JSON. It contains dimensions, filters, and measurement required for a query.

```
{
"Filters": [{
"DataModelName": "[StartDate].[Month]",
"Caption": "July 2013",
"Value": "[2015-03-01T00:00:00]",
"Operand": 0,
"UnionGroup": ""
}],
"Dimensions": [{
"DataModelName": "[StartDate].[Month]"
}],
"Measurements": [{
"DataModelName": "[Measures].[Audio Good Streams Count]"
},
{
"DataModelName": "[Measures].[Audio UnClassified Streams Count]"
},
{
"DataModelName": "[Measures].[Audio Poor Streams Count]"
},
{
"DataModelName": "[Measures].[AudioPoorPercentage]"
}],
"Trend": {
"EnableTrend": true,
"SpanCount": 7,
"TrendDate": "2015-3",
"Type": 0
}
}
```

 *Filters*  - A list of filter expressions to be applied such that the resulting data set will reflect only the subset of the data that are of interest.

 *Dimensions*  - A list of dimensions that will be used for aggregating the data. At least one dimension is required but multiple dimensions may be specified to obtain additional level of sub-aggregations.

 *Measurements*  - A list of measurements, also known as facts, that are the desired metrics to be aggregated based on the dimensions you specified.

 *Trend*  - Additional control instructions to customize the result data.

 **Response** - The response includes an HTTP status code and a set of response headers.

 **Status Code** - A successful operation returns status code 200 (OK).

 **Response Headers** - No additional headers.

 **Response Body** - Below is a sample response payload in JSON. It contains a data table which contains the data, also it will contain a meta data, which shows query execution time and whether or not the data is from the cache.

```
{
"ExecutionTime": "00:00:00.2102630",
"DataResult": [["September 2014",
        1792,
        34,
        78,
        4.171],
        ["October 2014",
        37017,
        1731,
        3305,
        8.197],
        ["November 2014",
        79184,
        3033,
        5556,
        6.557],
        ["December 2014",
        122253,
        4050,
        5444,
        4.263],
        ["January 2015",
        31246,
        1069,
        1342,
        4.118]],
"ResultIsFromCache": false,
"ErrorType": 0
}
```

 *Execution Time*  - The total time it took for the server to return the data. This may or may not involve cache.

 *Data Result*  - The result of the query. It is a two-dimensional array containing all permutations of the dimensions' members, and each element containing the dimensions' member names as well as the aggregated values of the specified Measurements.

 *Result is From Cache*  - For diagnostics. Indicates whether the result came from the cache or from the QoE Cube.
