---
title: "IPAddress table"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 2/1/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 8ec018b9-158e-4bbe-ad46-869e60315555
description: "The IPAddress table maps IP addresses to the unique IP address identifiers used elsewhere in the Quality of Experience database. This table was introduced in Microsoft Lync Server 2013."
---

# IPAddress table
 
The IPAddress table maps IP addresses to the unique IP address identifiers used elsewhere in the Quality of Experience database. This table was introduced in Microsoft Lync Server 2013.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**IPAddressKey** <br/> |int  <br/> |Primary  <br/> |Unique identifier for the specified IP address.  <br/> |
|**IPAddress** <br/> |varchar(50)  <br/> |Unique  <br/> |Unique IP address (for example, 189.168.1.1) that maps to the IpAddressKey. This may be either an IPv4 or an IPv6 address.  <br/> |
   

