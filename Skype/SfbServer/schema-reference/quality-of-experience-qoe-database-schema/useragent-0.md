---
title: "UserAgent view"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: b986f76f-f16e-4e5e-96cb-6e8f7f9b42ee
description: "The UserAgent View stores information about the user agents that have been involved in sessions that have records in the database. This view was introduced in Microsoft Lync Server 2013."
---

# UserAgent view
 
The UserAgent View stores information about the user agents that have been involved in sessions that have records in the database. This view was introduced in Microsoft Lync Server 2013.
  
|**Column**|**Data Type**|**Details**|
|:-----|:-----|:-----|
|UserAgentKey  <br/> |int  <br/> |Unique number identifying this user agent.  <br/> |
|UserAgent  <br/> |nvarchar(256)  <br/> |User agent string.  <br/> |
|UAType  <br/> |smallint  <br/> |Type of user agent. See the [UserAgent table](useragent.md) for more details. <br/> |
|UACategory  <br/> |nvarchar(64)  <br/> |Category that the user agent belongs to. For example, the user agent Conferencing_Attendant_1.0 belongs to the UACategory CAA.  <br/> |
   

