---
title: "UserAgent table in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d6bda1c0-b053-457a-9ffa-2ae859788775
description: "The UserAgent table is a supporting table that stores a list of the various user agents that have participated in sessions recorded in the database. Each record in the table represents one user agent"
---

# UserAgent table in Lync Server 2013
[]
The UserAgent table is a supporting table that stores a list of the various user agents that have participated in sessions recorded in the database. Each record in the table represents one user agent
  
|****Column****|****Data Type****|****Key/Index****|****Details****|
|:-----|:-----|:-----|:-----|
|**UserAgentKey** <br/> |int  <br/> |Primary  <br/> |Unique number identifying this user agent.  <br/> |
|**UserAgent** <br/> |nvarchar(256)  <br/> |Unique  <br/> |User Agent string.  <br/> |
|**UAType** <br/> |smallint  <br/> | <br/> |1 is Mediation Server.  <br/> 2 is A/V Conferencing Server.  <br/> 4 is Lync.  <br/> 8 is IP Phone.  <br/> 16 is Live Meeting Console.  <br/> 32 is Deployment Validation Tool (DVT).  <br/> 64 is Lync on Macintosh computers.  <br/> 128 is Office Communications Server 2007 R2 Attendant.  <br/> 256 is Conferencing Announcement service.  <br/> 512 is Conferencing Auto Attendant.  <br/> 1024 is Response Group application.  <br/> 2048 is Outside Voice Control.  <br/> |
   

