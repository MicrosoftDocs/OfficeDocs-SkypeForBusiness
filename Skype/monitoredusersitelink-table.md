---
title: MonitoredUserSiteLink table
ms.prod: SKYPEFORBUSINESS
ms.assetid: 16edc24a-2718-4bb4-b05c-bc7aafa97963
---


# MonitoredUserSiteLink table
[]
The MonitoredUserSiteLink table is a supporting table. Each record represents one link between two user sites.
  
    
    



|****Column****|****Data Type****|****Key/Index****|****Details****|
|:-----|:-----|:-----|:-----|
|**UserSite1Key** <br/> |int  <br/> |Primary, Foreign  <br/> |Referenced from the  [UserSite table](usersite-table.md).  <br/> |
|**UserSite2Key** <br/> |int  <br/> |Primary, Foreign  <br/> |Reference from the  [UserSite table](usersite-table.md).  <br/> |
   

