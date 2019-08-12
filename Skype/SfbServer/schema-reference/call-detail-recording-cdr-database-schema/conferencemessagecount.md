---
title: "ConferenceMessageCount table in Skype for Business Server 2015"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/9/2015
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 78569dbf-5217-42fa-ba1a-4380f56e2a3d
description: "Each record in this table represents one user in one IM conference and includes the number of messages sent by that user. Each conference is represented by multiple records in this table; one record for each user."
---

# ConferenceMessageCount table in Skype for Business Server 2015
 
Each record in this table represents one user in one IM conference and includes the number of messages sent by that user. Each conference is represented by multiple records in this table; one record for each user.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**SessionIdTime** <br/> |datetime  <br/> |Primary, Foreign  <br/> |Time of conference instance. Used in conjunction with **SessionIdSeq** to uniquely identify a conference instance. See the [Conferences table in Skype for Business Server 2015](conferences.md) for more information. <br/> |
|**SessionIdSeq** <br/> |int  <br/> |Primary, Foreign  <br/> |ID number to identify the conference instance. Used in conjunction with **SessionIdTime** to uniquely identify a conference instance. See the [Conferences table in Skype for Business Server 2015](conferences.md) for more information. <br/> |
|**UserId** <br/> |int  <br/> |Foreign  <br/> |Unique number identifying this user, referenced from the [Users table](users.md).  <br/> |
|**MessageCount** <br/> |smallint  <br/> | <br/> |The number of messages sent by this user during this conference.  <br/> |
   

