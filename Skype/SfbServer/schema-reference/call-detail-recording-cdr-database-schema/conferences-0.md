---
title: "Conferences view"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: c0e5c4db-c135-401f-9296-e9a49f6499a1
description: "The Conferences View stores information about the conferences. This view was introduced in Microsoft Lync Server 2013."
---

# Conferences view
 
The Conferences View stores information about the conferences. This view was introduced in Microsoft Lync Server 2013.
  
|**Column**|**Data Type**|**Details**|
|:-----|:-----|:-----|
|**SessionIdTime** <br/> |datetime  <br/> |Time of session request. Used in conjunction with SessionIdSeq to uniquely identify a session. See the [Dialogs table in Skype for Business Server 2015](dialogs.md) for more information. <br/> |
|**SessionIdSeq** <br/> |int  <br/> |ID number to identify the session. Used in conjunction with SessionIdTime to uniquely identify a session. See the [Dialogs table in Skype for Business Server 2015](dialogs.md) for more information. <br/> |
|**ConferenceUri** <br/> |nvarchar(450)  <br/> |URI for the conference.  <br/> |
|**ConferenceUriType** <br/> |nvarchar(256)  <br/> |Type of the conference URI. See the [UriTypes table](uritypes.md) for more information. <br/> |
|**ConfInstance** <br/> |uniqueidentifier  <br/> |Used for recurring conferences. Each instance of a recurring conference has the same ConferenceUri but a different ConfInstance.  <br/> |
|**ConferenceStartTime** <br/> |datetime  <br/> |Starting time for the conference.  <br/> |
|**ConferenceEndTime** <br/> |datetime  <br/> |Ending time for the conference.  <br/> |
|**OrganizerUri** <br/> |nvarchar(450)  <br/> |URI of the user who organized the conference.  <br/> |
|**OrganizerType** <br/> |nvarchar(256)  <br/> |Type of URI of the user who organized the conference. See the [UriTypes table](uritypes.md) for more information. <br/> |
|**OrganizerTenant** <br/> |nvarchar(256)  <br/> |Tenant of the user who organized the conference. See the [Tenants table](tenants.md) for more information. <br/> |
|**Pool** <br/> |nvarchar(256)  <br/> |Fully qualified domain name of the pool that hosted the conference.  <br/> |
|**Flag** <br/> |smallint  <br/> |Bit mask that contains Conference Attributes. Possible values are:  <br/> 0X01 - Synthetic Transaction  <br/> |
   

