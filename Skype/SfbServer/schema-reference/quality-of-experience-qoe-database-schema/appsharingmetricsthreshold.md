---
title: "AppSharingMetricsThreshold table"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 2/1/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 782cfab9-01a6-4843-aea1-28f47b0b51f7
description: "The AppSharingMetricsThreshold table contains optimal and acceptable values for the Quality of Experience metrics used with application sharing. These thresholds are used to determine if the application sharing experience should be classified as poor."
---

# AppSharingMetricsThreshold table
 
The AppSharingMetricsThreshold table contains optimal and acceptable values for the Quality of Experience metrics used with application sharing. These thresholds are used to determine if the application sharing experience should be classified as poor.
  
This table was introduced in Microsoft Lync Server 2013.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**CallType** <br/> |int  <br/> |Primary  <br/> |Type of call that was placed.  <br/> |
|**AppliedBandwidthLimitOptimal** <br/> |int  <br/> ||Optimal bandwidth limitation for application sharing. The default value is 1000000.  <br/> |
|**AppliedBandwidthLimitAcceptable** <br/> |int  <br/> ||Acceptable bandwidth limitation for application sharing. The default value is 500000.  <br/> |
|**SpoiledTilePercentTotalOptimal** <br/> |decimal(5,2)  <br/> ||Optimal percentage rate for "spoiled" tiles for classifying an Application Sharing quality. This value is the percentage of the content from the sharer that did not reach the viewer. Content may be discarded (or spoiled) when the sharer discards tiles from the graphics source or the ASMCU tiles discards tiles from Sharer respectively. The default value is 11 percent.  <br/> |
|**SpoiledTilePercentTotalAcceptable** <br/> |decimal(5,2)  <br/> ||Acceptable percentage rate for "spoiled" tiles for classifying an Application Sharing quality. This value is the percentage of the content from the sharer that did not reach the viewer. Content may be discarded (or spoiled) when the sharer discards tiles from the graphics source or the ASMCU tiles discards tiles from Sharer respectively. The default value is 36 percent.  <br/> |
|**JitterInterArrivalOptimal** <br/> |int  <br/> ||This column is not used in Microsoft Lync Server 2013.  <br/> |
|**JitterInterArrivalAcceptable** <br/> |int  <br/> ||This column is not used in Microsoft Lync Server 2013.  <br/> |
|**RelativeOneWayBurstDensityOptimal** <br/> |float  <br/> ||This column is not used in Microsoft Lync Server 2013.  <br/> |
|**RelativeOneWayBurstDensityAcceptable** <br/> |float  <br/> ||This column is not used in Microsoft Lync Server 2013.  <br/> |
|**RDPTileProcessingLatencyBurstDensityOptimal** <br/> |float  <br/> ||This column is not used in Microsoft Lync Server 2013.  <br/> |
|**RDPTileProcessingLatencyBurstDensityAcceptable** <br/> |float  <br/> ||This column is not used in Microsoft Lync Server 2013.  <br/> |
|**RelativeOneWayAverageOptimal** <br/> |float  <br/> ||Optimal value for the relative one-way delay between the two media endpoints involved in the application sharing. This is a single-hop latency measure. The default value is 1.0 seconds.  <br/> The column was introduced in Microsoft Lync Server 2013.  <br/> |
|**RelativeOneWayAverageAcceptable** <br/> |float  <br/> ||Optimal value for the relative one-way delay between the two media endpoints involved in the application sharing. This is a single-hop latency measure. The default value is 1.75 seconds.  <br/> The column was introduced in Microsoft Lync Server 2013.  <br/> |
|**RDPTileProcessingLatencyAverageOptimal** <br/> |float  <br/> ||Optimal value of the average RDP tile processing latency in the AS Conferencing Server over the duration of the viewing session. Latency is the time difference between when the Start Frame is encoded on the server (sharer or MCU depending on the scenario) and the same Start Frame is decoded on the viewer.  <br/> A high average reflects a longer delay in the viewing experience. An overloaded conferencing server may experience higher average delays. The default value is 200ms.  <br/> The column was introduced in Microsoft Lync Server 2013.  <br/> |
|**RDPTileProcessingLatencyAverageAcceptable** <br/> |float  <br/> ||Acceptable value of the average RDP tile processing latency in the AS Conferencing Server over the duration of the viewing session. Latency is the time difference between when the Start Frame is encoded on the server (sharer or MCU depending on the scenario) and the same Start Frame is decoded on the viewer.  <br/> A high average reflects a longer delay in the viewing experience. An overloaded conferencing server may experience higher average delays. The default value is 200ms.  <br/> The column was introduced in Microsoft Lync Server 2013.  <br/> |
   

