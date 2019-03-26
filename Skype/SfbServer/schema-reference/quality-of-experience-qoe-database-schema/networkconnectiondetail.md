---
title: "NetworkConnectionDetail table"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 2/1/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: b48cc9a6-5232-48b5-bd20-53b68229336b
description: "The NetworkConnectionDetail table maps network connection types to the network connection identifiers used elsewhere in the Quality of Experience database. This table was introduced in Microsoft Lync Server 2013."
---

# NetworkConnectionDetail table
 
The NetworkConnectionDetail table maps network connection types to the network connection identifiers used elsewhere in the Quality of Experience database. This table was introduced in Microsoft Lync Server 2013.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**NetworkConnectionDetailKey** <br/> |tinyint  <br/> |Primary  <br/> |Unique identifier for the network connection type.  <br/> |
|**NetworkConnectionDetail** <br/> |varchar(256)  <br/> |Unique  <br/> |Network connection type that corresponds to the NetworkConnectionDetailKey. Allowed values are:  <br/> 0 -- Wired  <br/> 1 -- WiFi  <br/> 2 -- Ethernet  <br/> 3 -- MobileBB  <br/> 4 -- Other  <br/> 5 -- Tunnel  <br/> |
   

