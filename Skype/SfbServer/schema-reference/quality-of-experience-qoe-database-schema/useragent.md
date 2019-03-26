---
title: "UserAgent table"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 2/1/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: d6bda1c0-b053-457a-9ffa-2ae859788775
description: "The UserAgent table is a supporting table that stores a list of the various user agents that have participated in sessions recorded in the database. Each record in the table represents one user agent"
---

# UserAgent table
 
The UserAgent table is a supporting table that stores a list of the various user agents that have participated in sessions recorded in the database. Each record in the table represents one user agent
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**UserAgentKey** <br/> |int  <br/> |Primary  <br/> |Unique number identifying this user agent.  <br/> |
|**UserAgent** <br/> |nvarchar(256)  <br/> |Unique  <br/> |User Agent string.  <br/> |
|**UAType** <br/> |smallint  <br/> | <br/> |1 is Mediation Server.  <br/> 2 is A/V Conferencing Server.  <br/> 4 is Skype for Business.  <br/> 8 is IP Phone.  <br/> 16 is Live Meeting Console.  <br/> 32 is Deployment Validation Tool (DVT).  <br/> 64 is Skype for Business Server on Macintosh computers.  <br/> 128 is Skype for Business Server Attendant.  <br/> 256 is Conferencing Announcement service.  <br/> 512 is Conferencing Auto Attendant.  <br/> 1024 is Response Group application.  <br/> 2048 is Outside Voice Control.  <br/> |
   

