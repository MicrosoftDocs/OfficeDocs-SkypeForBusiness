---
title: "Subnet table in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 76f5c995-96c8-4aa3-bc30-1d74991d7c42
description: "The Subnet table is a supporting table. Each record represents one subnet defined in network configuration setting."
---

# Subnet table in Lync Server 2013
[]
The Subnet table is a supporting table. Each record represents one subnet defined in network configuration setting.
  
|****Column****|****Data Type****|****Key/Index****|****Details****|
|:-----|:-----|:-----|:-----|
|**SubnetIP** <br/> |int  <br/> |Primary, Foreign  <br/> |Integer representation for the subnet IP.  <br/> |
|**SubnetMask** <br/> |int  <br/> ||Subnet mask.  <br/> |
|**UserSiteKey** <br/> |int  <br/> |Foreign  <br/> |Referenced from the [UserSite table in Lync Server 2013](usersite-table.md).  <br/> |
|**SubnetDescription** <br/> |nvarchar(512)  <br/> ||The description for the subnet.  <br/> |
   

