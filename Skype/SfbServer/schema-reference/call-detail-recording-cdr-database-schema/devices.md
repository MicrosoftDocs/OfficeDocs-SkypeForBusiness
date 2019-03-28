---
title: "Devices table in Skype for Business Server 2015"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 532e2280-4bbc-4a6c-93da-45d9f80a30a0
description: "The Devices table is a supporting table. Each record stores information about one device (desk phone)."
---

# Devices table in Skype for Business Server 2015
 
The Devices table is a supporting table. Each record stores information about one device (desk phone).
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**DeviceId** <br/> |int  <br/> |Primary  <br/> |Unique number identifying this hardware version.  <br/> |
|**ManufacturerId** <br/> |int  <br/> |Foreign  <br/> |Manufacturer of this device. See the [Manufacturers table in Skype for Business Server 2015](manufacturers.md) for more information. <br/> |
|**HardwareVersionId** <br/> |int  <br/> |Foreign  <br/> |Hardware version of this device. See the [HardwareVersions table in Skype for Business Server 2015](hardwareversions.md) for more information. <br/> |
|**MacAddress** <br/> |bigint  <br/> ||MAC Address  <br/> |
   

