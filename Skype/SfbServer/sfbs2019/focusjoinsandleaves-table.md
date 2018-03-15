---
title: "FocusJoinsAndLeaves table in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: e6f0212c-67e9-4061-8720-d0296e855991
description: "Each record in this table contains the CDR information about one user's join and leave information for one conference. Each conference is represented in this table by one record for each time a user joins and leaves the conference."
---

# FocusJoinsAndLeaves table in Lync Server 2013
[]
Each record in this table contains the CDR information about one user's join and leave information for one conference. Each conference is represented in this table by one record for each time a user joins and leaves the conference.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**SessionIdTime** <br/> |datetime  <br/> |Primary, Foreign  <br/> |Time of conference instance. Used in conjunction with **SessionIdSeq** to uniquely identify a conference instance. See the [Conferences table in Lync Server 2013](conferences-table.md) for more information.  <br/> |
|**SessionIdSeq** <br/> |int  <br/> |Primary, Foreign  <br/> |ID number to identify the conference instance. Used in conjunction with **SessionIdTime** to uniquely identify a conference instance. See the [Conferences table in Lync Server 2013](conferences-table.md) for more information.  <br/> |
|**DialogSessionIdTime** <br/> |datetime  <br/> |Primary, Foreign  <br/> |Time of session request. Used in conjunction with **SessionIdSeq** to uniquely identify a session. See the [Dialogs table in Lync Server 2013](dialogs-table.md) for more information.  <br/> |
|**DialogSessionIdSeq** <br/> |int  <br/> |Primary, Foreign  <br/> |ID number to identify the session. Used in conjunction with **SessionIdTime** to uniquely identify a session. see the [Dialogs table in Lync Server 2013](dialogs-table.md) for more information.  <br/> |
|**UserId** <br/> |int  <br/> |Foreign  <br/> |Unique number identifying this user, referenced from the [Users table in Lync Server 2013](users-table.md).  <br/> |
|**FocusUserInstance** <br/> |int  <br/> ||If a user is logged on at multiple computers or devices at the same time, **UserInstance** is used to uniquely identify the user/device combination.  <br/> |
|**IsUserInternal** <br/> |bit  <br/> | <br/> |Whether the user logged on from internal or not.  <br/> |
|**UserRole** <br/> |int  <br/> | <br/> |This user's role in the conference, such as Presenter or Attendee.  <br/> |
|**UserJoinTime** <br/> |datetime  <br/> | <br/> |The time this user joins the conference.  <br/> |
|**UserLeaveTime** <br/> |datetime  <br/> | <br/> |The time this user leaves the conference.  <br/> |
|**ClientVerId** <br/> |int  <br/> |Foreign  <br/> |Version of the user's client software, referenced to the [ClientVersions table in Lync Server 2013](clientversions-table.md).  <br/> |
|**UserEndpointId** <br/> |uniqueIdentifier  <br/> ||Globally unique identifier (GUID) of the endpoint used in the conference.  <br/> This field was introduced in Microsoft Lync Server 2013.  <br/> |
   

