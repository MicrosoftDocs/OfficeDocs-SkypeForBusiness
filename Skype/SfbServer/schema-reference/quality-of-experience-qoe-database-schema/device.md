---
title: "Device table"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 2/1/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: d5a4f777-bc12-4ce8-bc0d-867d5e22b436
description: "The Device table is a supporting table that stores information about the various capture or render devices. Each record in the table represents one device."
---

# Device table
 
The Device table is a supporting table that stores information about the various capture or render devices. Each record in the table represents one device.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**DeviceKey** <br/> |int  <br/> |Primary  <br/> |Unique number identifying this device.  <br/> |
|**DeviceName** <br/> |nvarchar(256)  <br/> |DeviceName + DeviceType is unique  <br/> |Device name.  <br/> |
|**DeviceType** <br/> |bit  <br/> |DeviceName + DeviceType is unique  <br/> |Device type. 1 is a capture device, 0 is a render device.  <br/> |
   

