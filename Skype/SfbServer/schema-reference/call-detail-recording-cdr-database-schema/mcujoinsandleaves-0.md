---
title: "McuJoinsAndLeaves view"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 6f00b8e7-b8b6-4657-ac5e-d8a571806ae2
description: "The McuJoinsAndLeaves view stores information about users join and leave information for one conference server. Each record in this view contains call details about one combination of a user join or leave and conferencing server. This view was introduced in Microsoft Lync Server 2013."
---

# McuJoinsAndLeaves view
 
The McuJoinsAndLeaves view stores information about users join and leave information for one conference server. Each record in this view contains call details about one combination of a user join or leave and conferencing server. This view was introduced in Microsoft Lync Server 2013.
  
|**Column**|**Data Type**|**Details**|
|:-----|:-----|:-----|
|**SessionIdTime** <br/> |datetime  <br/> |Time of conference instance. Used in conjunction with SessionIdSeq to uniquely identify a conference instance. See the [Conferences table in Skype for Business Server 2015](conferences.md) for more information. <br/> |
|**SessionIdSeq** <br/> |int  <br/> |ID number to identify the conference instance. Used in conjunction with SessionIdTime to uniquely identify a conference instance. See the [Conferences table in Skype for Business Server 2015](conferences.md) for more information. <br/> |
|**McuUri** <br/> |nvarchar(256)  <br/> |The URI of the conferencing server that the user connected to.  <br/> |
|**McuUriType** <br/> |nvarchar(256)  <br/> |The URI of the conferencing server that the user connected to. See the [UriTypes table](uritypes.md) for more information. <br/> |
|**UserUri** <br/> |nvarchar(450)  <br/> |The URI of the user whose conferencing server join/leave information was captured.  <br/> |
|**UserUriType** <br/> |nvarchar(256)  <br/> |The type of URI of the user whose conferencing server join/leave information was captured. See the [UriTypes table](uritypes.md) for more information. <br/> |
|**UserTenant** <br/> |nvarchar(256)  <br/> |The tenant of the user whose conferencing server join/leave information was captured. See the [Tenants table](tenants.md) for more information. <br/> |
|**UserClientVersion** <br/> |nvarchar(256)  <br/> |The version of client used by the user whose conferencing server join/leave information was captured.  <br/> |
|**UserClientType** <br/> |int  <br/> |The client used by the user whose conferencing server join/leave information was captured. See the [UserAgentDef table](useragentdef.md) for more details. <br/> |
|**UserClientCategory** <br/> |nvarchar(64)  <br/> |The name of the category of the client used by the user whose conferencing server join/leave information was captured.  <br/> |
|**McuUserInstance** <br/> |int  <br/> |Uniquely identifies the user/device combination for users simultaneously logged on to multiple devices.  <br/> |
|**IsUserFromPstn** <br/> |bit  <br/> |Bit that represents whether the user is an internal user or not.  <br/> |
|**DialogSessionIdTime** <br/> |datetime  <br/> |Time of session request. Used in conjunction with SessionIdSeq to uniquely identify a session. See the [Dialogs table in Skype for Business Server 2015](dialogs.md) for more information. <br/> |
|**DialogSessionIdSeq** <br/> |int  <br/> |ID number to identify the session. Used in conjunction with SessionIdTime to uniquely identify a session. See the [Dialogs table in Skype for Business Server 2015](dialogs.md) for more information. <br/> |
|**DialogId** <br/> |varchar(775)  <br/> |SIP dialog ID of the session. The format is: dialog;from-tag;to-tag.  <br/> |
|**UserJoinTime** <br/> |datetime  <br/> |Time the user joined the conferencing server.  <br/> |
|**UserLeaveTime** <br/> |datetime  <br/> |Time the user left the conferencing server.  <br/> |
   

