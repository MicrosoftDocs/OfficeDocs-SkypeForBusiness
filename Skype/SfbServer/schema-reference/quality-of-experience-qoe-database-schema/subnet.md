---
title: "Subnet table"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 2/1/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 76f5c995-96c8-4aa3-bc30-1d74991d7c42
description: "The Subnet table is a supporting table. Each record represents one subnet defined in network configuration setting."
---

# Subnet table
 
The Subnet table is a supporting table. Each record represents one subnet defined in network configuration setting.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**SubnetIP** <br/> |int  <br/> |Primary, Foreign  <br/> |Integer representation for the subnet IP.  <br/> |
|**SubnetMask** <br/> |int  <br/> ||Subnet mask.  <br/> |
|**UserSiteKey** <br/> |int  <br/> |Foreign  <br/> |Referenced from the [UserSite table](usersite.md).  <br/> |
|**SubnetDescription** <br/> |nvarchar(512)  <br/> ||The description for the subnet.  <br/> |
   

