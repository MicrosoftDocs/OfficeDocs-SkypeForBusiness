---
title: "Capacity planning for Call Park in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 75520310-760a-4b1b-bcc1-4d724d13f87a

---

# Capacity planning for Call Park in Lync Server 2013
[]The following table describes the Call Park user model that you can use as the basis for capacity planning requirements.
  
> [!IMPORTANT]
> Keep in mind that, for disaster recovery capacity planning, each pool of a paired pool should be able to handle the workloads for Call Park services in both pools. 
  
**Call Park User Model**

|**Metric**|**Per Front End pool  <br/>  (with 8 Front End Servers)**|**Per Standard Edition server**|
|:-----|:-----|:-----|
|Park rate  <br/> |8 per minute  <br/> |1 per minute  <br/> |
|Retrieve parked call rate  <br/> |8 per minute  <br/> |1 per minute  <br/> |
|Average park duration  <br/> |60 seconds  <br/> |60 seconds  <br/> |
   

