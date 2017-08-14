---
title: UserSite table
ms.prod: SKYPEFORBUSINESS
ms.assetid: 1c2a3cf2-dc05-472e-8097-a31f3a1aafcb
---


# UserSite table
[]
The UserSite table is a supporting table. Each record represents one user site defined in network configuration setting.
  
    
    



|****Column****|****Data Type****|****Key/Index****|****Details****|
|:-----|:-----|:-----|:-----|
|**UserSiteKey** <br/> |int  <br/> |Primary  <br/> |Unique number identifying the user site.  <br/> |
|**UserSiteName** <br/> |nvarchar(128)  <br/> |Unique  <br/> |User site's name.  <br/> |
|**RegionKey** <br/> |int  <br/> |Foreign  <br/> |Referenced from  [Region table](region-table.md).  <br/> |
   

