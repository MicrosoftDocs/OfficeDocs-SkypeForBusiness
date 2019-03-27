---
title: "Conferences table in Skype for Business Server 2015"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 7/15/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: c3da6271-b3c6-4898-894f-10456ec794d0
description: "Each record in this table contains call details about one conference."
---

# Conferences table in Skype for Business Server 2015
 
Each record in this table contains call details about one conference.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**SessionIdTime** <br/> |datetime  <br/> |Primary  <br/> |Time that the conference request was captured by the CDR agent. Used only as a primary key to uniquely identify a conference instance.  <br/> |
|**SessionIdSeq** <br/> |int  <br/> |Primary  <br/> |ID number to identify the session. Used in conjunction with **SessionIdTime** to uniquely identify a conference instance. * <br/> |
|**ConferenceUriId** <br/> |int  <br/> |Foreign  <br/> |Conference URI. See the [ConferenceUris table in Skype for Business Server 2015](conferenceuris.md) for more information. <br/> |
|**ConfInstance** <br/> |uniqueidentifier  <br/> | <br/> |Useful for recurring conferences; each instance of a recurring conference has the same **ConferenceUri**, but will have a different **ConfInstance**. <br/> |
|**ConferenceStartTime** <br/> |datetime  <br/> | <br/> |Conference start time.  <br/> |
|**ConferenceEndTime** <br/> |datetime  <br/> | <br/> |Conference start time.  <br/> |
|**PoolId** <br/> |int  <br/> |Foreign  <br/> |ID number to identify the pool in which the conference was captured. See the [Pools table](pools.md) for more information. <br/> |
|**OrganizerId** <br/> |Int  <br/> |Foreign  <br/> |ID number to identify the organizer URI of this conference. See the [Users table](users.md) for more information. <br/> |
|**Flag** <br/> |smallint  <br/> || A bit mask that contains Conference Attributes. Possible values are: <br/>  0X01 <br/>  Synthetic <br/>  Transaction <br/> |
|**Processed** <br/> |bit  <br/> ||Internal field used by the Monitoring service.  <br/> This field was introduced in Microsoft Lync Server 2013.  <br/> |
|**LastModifiedTime** <br/> |Datetime  <br/> ||For internal use by the Monitoring service.  <br/> This field was introduced in Skype for Business Server 2015.  <br/> |
   
\* For most sessions, SessionIdSeq will have the value of 1. If two sessions start at exactly the same time, the SessionIdSeq for one will be 1, and for the other will be 2, and so on.
  

