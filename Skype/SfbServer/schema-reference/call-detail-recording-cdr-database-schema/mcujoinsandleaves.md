---
title: "McuJoinsAndLeaves table in Skype for Business Server 2015"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 7/15/2015
audience: ITPro
ms.topic: article
ms.service: skype-for-business-server
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.assetid: 4e073366-0b5d-45b4-a3f6-d63dd5fd9f25
description: "Each record in this table contains call details about one combination of a user join or leave and conferencing server. For example, if a user joins a conference that includes web conferencing and audio/video elements, one record would be created for that user's web conferencing join, and another record would be created for the user's audio/video conferencing join."
---

# McuJoinsAndLeaves table in Skype for Business Server 2015
 
Each record in this table contains call details about one combination of a user join or leave and conferencing server. For example, if a user joins a conference that includes web conferencing and audio/video elements, one record would be created for that user's web conferencing join, and another record would be created for the user's audio/video conferencing join.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**SessionIdTime** <br/> |datetime  <br/> |Primary, Foreign  <br/> |Time of conference instance. Used with **SessionIdSeq** to uniquely identify a conference instance. For more information, see the [Conferences table in Skype for Business Server 2015](conferences.md). <br/> |
|**SessionIdSeq** <br/> |int  <br/> |Primary, Foreign  <br/> |ID number to identify the conference instance. Used with **SessionIdTime** to uniquely identify a conference instance. For more information, see the [Conferences table in Skype for Business Server 2015](conferences.md). <br/> |
|**UserId** <br/> |int  <br/> |Primary, Foreign  <br/> |Unique number identifying this user. For more information, see the [Users table](users.md). <br/> |
|**McuUserInstance** <br/> |int  <br/> |Primary  <br/> |If a user is logged on at multiple computers or devices at once, McuUserInstance uniquely identifies the user/device combination.  <br/> |
|**IsFromPstn** <br/> |bit  <br/> | <br/> |Whether the user is joining from a PSTN or not.  <br/> |
|**McuId** <br/> |int  <br/> |Primary, Foreign  <br/> |Unique number identifying this conferencing server. For more information, see the [Mcus table in Skype for Business Server 2015](mcus.md). <br/> |
|**DialogSessionIdTime** <br/> |datetime  <br/> |Foreign  <br/> |Time of session request. Used with **SessionIdSeq** to uniquely identify a session. For more information, see the [Dialogs table in Skype for Business Server 2015](dialogs.md). <br/> |
|**DialogSessionIdSeq** <br/> |int  <br/> |Foreign  <br/> |ID number to identify the session. Used with **SessionIdTime** to uniquely identify a session. For more information, see the [Dialogs table in Skype for Business Server 2015](dialogs.md). <br/> |
|**UserJoinTime** <br/> |datetime  <br/> | <br/> |The time this user joins this conferencing server.  <br/> |
|**UserLeaveTime** <br/> |datetime  <br/> | <br/> |The time this user leaves this conferencing server.  <br/> |
|**ClientVerId** <br/> |int  <br/> |Foreign  <br/> |Identifier that specifies the version number of the client software use in the conference.  For more information, see the [ClientVersions table in Skype for Business Server 2015](clientversions.md). <br/> This field was introduced in Microsoft Lync Server 2013.  <br/> |
|**LastModifiedTime** <br/> |Datetime  <br/> ||For internal use by the Monitoring service.  <br/> This field was introduced in Skype for Business Server 2015.  <br/> |
   

