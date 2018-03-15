---
title: "MonitoredUserSiteLink table"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 16edc24a-2718-4bb4-b05c-bc7aafa97963
description: "The MonitoredUserSiteLink table is a supporting table. Each record represents one link between two user sites."
---

# MonitoredUserSiteLink table
[]
The MonitoredUserSiteLink table is a supporting table. Each record represents one link between two user sites.
  
|****Column****|****Data Type****|****Key/Index****|****Details****|
|:-----|:-----|:-----|:-----|
|**UserSite1Key** <br/> |int  <br/> |Primary, Foreign  <br/> |Referenced from the [UserSite table in Lync Server 2013](usersite-table.md).  <br/> |
|**UserSite2Key** <br/> |int  <br/> |Primary, Foreign  <br/> |Reference from the [UserSite table in Lync Server 2013](usersite-table.md).  <br/> |
   

