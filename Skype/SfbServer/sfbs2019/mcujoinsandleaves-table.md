---
title: "McuJoinsAndLeaves table in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 4e073366-0b5d-45b4-a3f6-d63dd5fd9f25
description: "Each record in this table contains call details about one combination of a user join or leave and conferencing server. For example, if a user joins a conference that includes web conferencing and audio/video elements, one record would be created for that user's web conferencing join, and another record would be created for the user's audio/video conferencing join."
---

# McuJoinsAndLeaves table in Lync Server 2013
[]
Each record in this table contains call details about one combination of a user join or leave and conferencing server. For example, if a user joins a conference that includes web conferencing and audio/video elements, one record would be created for that user's web conferencing join, and another record would be created for the user's audio/video conferencing join.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**SessionIdTime** <br/> |datetime  <br/> |Primary, Foreign  <br/> |Time of conference instance. Used in conjunction with **SessionIdSeq** to uniquely identify a conference instance. See the [Conferences table in Lync Server 2013](conferences-table.md) for more information.  <br/> |
|**SessionIdSeq** <br/> |int  <br/> |Primary, Foreign  <br/> |ID number to identify the conference instance. Used in conjunction with **SessionIdTime** to uniquely identify a conference instance. See the [Conferences table in Lync Server 2013](conferences-table.md) for more information.  <br/> |
|**UserId** <br/> |int  <br/> |Primary, Foreign  <br/> |Unique number identifying this user. See the [Users table in Lync Server 2013](users-table.md) for more information.  <br/> |
|**McuUserInstance** <br/> |int  <br/> |Primary  <br/> |If a user is logged on at multiple computers or devices at once, McuUserInstance uniquely identifies the user/device combination.  <br/> |
|**IsFromPstn** <br/> |bit  <br/> | <br/> |Whether the user is joining from a PSTN or not.  <br/> |
|**McuId** <br/> |int  <br/> |Primary, Foreign  <br/> |Unique number identifying this conferencing server. See the [Mcus table in Lync Server 2013](mcus-table.md) for more information.  <br/> |
|**DialogSessionIdTime** <br/> |datetime  <br/> |Foreign  <br/> |Time of session request. Used in conjunction with **SessionIdSeq** to uniquely identify a session. See the [Dialogs table in Lync Server 2013](dialogs-table.md) for more information.  <br/> |
|**DialogSessionIdSeq** <br/> |int  <br/> |Foreign  <br/> |ID number to identify the session. Used in conjunction with **SessionIdTime** to uniquely identify a session. See the [Dialogs table in Lync Server 2013](dialogs-table.md) for more information.  <br/> |
|**UserJoinTime** <br/> |datetime  <br/> | <br/> |The time this user joins this conferencing server.  <br/> |
|**UserLeaveTime** <br/> |datetime  <br/> | <br/> |The time this user leaves this conferencing server.  <br/> |
|**ClientVerId** <br/> |int  <br/> |Foreign  <br/> |Identifier that specifies the version number of the client software use in the conference. See the [ClientVersions table in Lync Server 2013](clientversions-table.md) for more information.  <br/> This field was introduced in Microsoft Lync Server 2013.  <br/> |
   

