---
title: "MonitoredUserSiteLink table"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 2/1/2018
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 16edc24a-2718-4bb4-b05c-bc7aafa97963
description: "The MonitoredUserSiteLink table is a supporting table. Each record represents one link between two user sites."
---

# MonitoredUserSiteLink table
 
The MonitoredUserSiteLink table is a supporting table. Each record represents one link between two user sites.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**UserSite1Key** <br/> |int  <br/> |Primary, Foreign  <br/> |Referenced from the [UserSite table](usersite.md).  <br/> |
|**UserSite2Key** <br/> |int  <br/> |Primary, Foreign  <br/> |Reference from the [UserSite table](usersite.md).  <br/> |
   

