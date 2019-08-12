---
title: "FocusJoinsAndLeaves view"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/9/2015
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 226460ef-766f-4d61-80cb-f332b65a210d
description: "The FocusJoinsAndLeaves view stores information about join and leave information for one conference. Each conference is represented in this view by a record written each time a user joins and leaves the conference. This view was introduced in Microsoft Lync Server 2013."
---

# FocusJoinsAndLeaves view
 
The FocusJoinsAndLeaves view stores information about join and leave information for one conference. Each conference is represented in this view by a record written each time a user joins and leaves the conference. This view was introduced in Microsoft Lync Server 2013.
  
|**Column**|**Data Type**|**Details**|
|:-----|:-----|:-----|
|**SessionIdTime** <br/> |datetime  <br/> |Time of conference instance. Used in conjunction with SessionIdSeq to uniquely identify a conference instance. See the [Conferences table in Skype for Business Server 2015](conferences.md) for more information. <br/> |
|**SessionIdSeq** <br/> |int  <br/> |ID number to identify the conference instance. Used in conjunction with SessionIdTime to uniquely identify a conference instance. See the [Conferences table in Skype for Business Server 2015](conferences.md) for more information. <br/> |
|**UserUri** <br/> |nvarchar(450)  <br/> |URI of the user whose conference join/leave information was captured.  <br/> |
|**UserUriType** <br/> |nvarchar(256)  <br/> |Type of URI of the user whose conference join/leave information was captured. See the [UriTypes table](uritypes.md) for more information. <br/> |
|**UserTenant** <br/> |nvarchar(256)  <br/> |Tenant of the user whose conference join/leave information was captured. See the [Tenants table](tenants.md) for more information. <br/> |
|**UserEndpointId** <br/> |uniqueidentifier  <br/> |Unique identifier of the user whose conference join/leave information was captured.  <br/> |
|**UserClientVersion** <br/> |nvarchar(256)  <br/> |Version of client used by the user whose conference join/leave information was captured.  <br/> |
|**UserClientType** <br/> |int  <br/> |Client used by the user whose conference join/leave information was captured. See [UserAgentDef table](useragentdef.md) for more details. <br/> |
|**UserClientCategory** <br/> |nvarchar(64)  <br/> |Name of the category of the client used by the user whose conference join/leave information was captured.  <br/> |
|**FocusUserInstance** <br/> |int  <br/> ||
|**IsuserInternal** <br/> |bit  <br/> |Bit that represents whether the user is an internal user or not.  <br/> |
|**DialogSessionIdTime** <br/> |datetime  <br/> |Time of session request. Used in conjunction with SessionIdSeq to uniquely identify a session. See the [Dialogs table in Skype for Business Server 2015](dialogs.md) for more information. <br/> |
|**DialogSessionIdSeq** <br/> |int  <br/> |If a user is logged on at multiple computers or devices at the same time, UserInstance is used to uniquely identify the user/device combination.  <br/> |
|**DialogId** <br/> |varchar(775)  <br/> |SIP dialog ID of the session. The format is: dialog;from-tag;to-tag.  <br/> |
|**UserJoinTime** <br/> |datetime  <br/> |Time that the user joined the conference.  <br/> |
|**UserLeaveTime** <br/> |datetime  <br/> |Time that the user left the conference.  <br/> |
|**UserRole** <br/> |nvarchar(256)  <br/> |User's role in the conference, such as Presenter or Attendee.  <br/> |
   

