---
title: "VideoMetricsThreshold table"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 2/1/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 2e2f4711-35ba-48c6-b15b-5aba61c4eb75
description: "The VideoMetricsThreshold table contains optimal and acceptable values for the Quality of Experience metrics used with video calls."
---

# VideoMetricsThreshold table
 
The VideoMetricsThreshold table contains optimal and acceptable values for the Quality of Experience metrics used with video calls.
  

| **Column**                                               | **Data Type**       | **Key/Index**  | **Details**                          |
|:---------------------------------------------------------|:--------------------|:---------------|:-------------------------------------|
| **CallType** <br/>                                       | int  <br/>          | Primary  <br/> | Type of call that was placed.  <br/> |
| **VideoPostFECPLROptimal** <br/>                         | decimal(5,2)  <br/> |                | The default value is 0.05.  <br/>    |
| **VideoPostFECPLRAcceptable** <br/>                      | decimal(5,2)  <br/> |                | The default value is 0.10.  <br/>    |
| **VideoLocalFrameLostPercentageAverageOptimal** <br/>    | decimal(5,2)  <br/> |                | The default value is 5.0.  <br/>     |
| **VideoLocalFrameLostPercentageAverageAcceptable** <br/> | decimal(5,2)  <br/> |                | The default value is 10.0.  <br/>    |
| **RecvFrameRateAverageOptimal** <br/>                    | decimal(9,4)  <br/> |                | The default value is 12.0000.  <br/> |
| **RecvFramerateAverageAcceptable** <br/>                 | decimal(9,4)  <br/> |                | The default value is 7.0000.  <br/>  |
| **LowFrameRateCallPercentOptimal** <br/>                 | decimal(5,2)  <br/> |                | The default value is 5.0.  <br/>     |
| \****LowFrameRateCallPercentAcceptable***\* <br/>        | decimal(5,2)  <br/> |                | The default value is 10.0/  <br/>    |
| **LowResolutionCallPercentOptimal** <br/>                | decimal(5,2)  <br/> |                | The default value is 5.0.  <br/>     |
| **LowResolutionCallPercentAcceptable** <br/>             | decimal(5,2)  <br/> |                | The default value is 10.0.  <br/>    |
| **VideoPacketLossRateOptimal** <br/>                     | foat  <br/>         |                | The default value is 0.05.  <br/>    |
| **VideoPacketLossRateAcceptable** <br/>                  | float  <br/>        |                | The default value is 0.10.  <br/>    |
| **VideoFrameRateAvgOptimal** <br/>                       | float  <br/>        |                | The default value is 12.  <br/>      |
| **VideoFrameRateAvgAcceptable** <br/>                    | float  <br/>        |                | The default value is 7.  <br/>       |
| **DynamicCapabilityPercentOptimal** <br/>                | decimal(5,2)  <br/> |                | The default value is 5.00.  <br/>    |
| **DynamicCapabilityPercentAcceptable** <br/>             | decimal(5,2)  <br/> |                | The default value is 10.00.  <br/>   |

