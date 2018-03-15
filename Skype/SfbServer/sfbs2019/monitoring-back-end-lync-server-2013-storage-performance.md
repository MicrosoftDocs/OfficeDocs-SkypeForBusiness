---
title: "Monitoring back end Lync Server 2013 storage performance"
ms.author: jambirk
author: jambirk
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 71627c70-1953-4ac2-afbe-f3ad85be0f44
description: "The Lync Server 2013 back-end databases are a very important part of the Lync Server 2013 deployment. We recommend constantly monitoring the databases and respective transaction logs to help to make sure that the Lync Server 2013 back end is performing optimally."
---

# Monitoring back end Lync Server 2013 storage performance
[]
The Lync Server 2013 back-end databases are a very important part of the Lync Server 2013 deployment. We recommend constantly monitoring the databases and respective transaction logs to help to make sure that the Lync Server 2013 back end is performing optimally. 
  
The following table identifies performance counters that should be monitored to learn information about Storage Performance. The baseline values for these counters must be determined first (when system is at its normal, expected load) to understand the performance changes when system is stressed.
  
**Performance counters to be monitored**

|**Performance Counter**|**Baseline thresholds**|
|:-----|:-----|
|Transactions/sec (RTC)  <br/> ||
|Transactions/sec (rtcdyn)  <br/> ||
|Transactions/sec (tempdb)  <br/> ||
|Log Flushes/sec (RTC)  <br/> ||
|Log Flushes/sec (rtcdyn)  <br/> ||
|Log Flushes/sec (tempdb)  <br/> ||
|Disk Transfers/sec (read+write) - RTC db  <br/> ||
|Disk Transfers/sec - RTC log  <br/> ||
|Disk Transfers/sec - rtcdyn db  <br/> ||
|Disk Transfers/sec - rtcdyn log  <br/> ||
   

