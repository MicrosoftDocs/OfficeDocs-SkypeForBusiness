---
title: "Pool table in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 92ded8fd-d0ad-4f8a-9e6f-2e8a690fda3a
description: "The Pool table is a supporting table that stores information about the various Front End pools. Each record in the table represents one pool."
---

# Pool table in Lync Server 2013
[]
The Pool table is a supporting table that stores information about the various Front End pools. Each record in the table represents one pool.
  
|****Column****|****Data Type****|****Key/Index****|****Details****|
|:-----|:-----|:-----|:-----|
|**PoolKey** <br/> |int  <br/> |Primary  <br/> |Unique number identifying this pool.  <br/> |
|**PoolName** <br/> |nvarchar(256)  <br/> |Unique  <br/> |Pool FQDN.  <br/> |
   

