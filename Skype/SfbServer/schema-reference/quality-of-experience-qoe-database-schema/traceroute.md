---
title: "TraceRoute table"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 2/1/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: b9493cef-6ece-4f13-bf68-dbf132aab4f4
description: "The TraceRoute table contains routing information from calls. This table was introduced in Microsoft Lync Server 2013."
---

# TraceRoute table
 
The TraceRoute table contains routing information from calls. This table was introduced in Microsoft Lync Server 2013.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**ConferenceDateTime** <br/> |datetime  <br/> |Primary, Foreign  <br/> |Date and time that the call began.  <br/> |
|**SessionSeq** <br/> |int  <br/> |Primary, Foreign  <br/> |Unique identifier used to distinguish between multiple calls that might have begun on the same date and at the same time.  <br/> |
|**MediaLineLabel** <br/> |tinyint  <br/> |Primary, Foreign  <br/> |Represents the type of video line used in the call. Allowed values are:  <br/> 0 - Audio  <br/> 1 - Video  <br/> 2 - Panoramic video  <br/> 3 - Application/Desktop sharing  <br/> |
|**FromCaller** <br/> |bit  <br/> |Primary  <br/> |Endpoint that placed the call.  <br/> |
|**Hop** <br/> |int  <br/> ||Network hop/  <br/> |
|**IPAddressKey** <br/> |int  <br/> |Foreign  <br/> |Unique identifier for the IP address. IP address information is stored in the [IPAddress table](ipaddress.md).  <br/> |
|**RTT** <br/> |int  <br/> ||Roundtrip time. The roundtrip time measures the amount of time it takes for a voice packet to reach its destination and then send back notification that it was received.  <br/> |
   

