---
title: "Session view"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 10/20/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 49e33f5b-45d0-4146-a5a4-76954d895a98
description: "The Session View stores information about sessions that have records in the database. This view was introduced in Microsoft Lync Server 2013."
---

# Session view
 
The Session View stores information about sessions that have records in the database. This view was introduced in Microsoft Lync Server 2013.
  
|**Column**|**Data Type**|**Details**|
|:-----|:-----|:-----|
|ConferenceDateTime  <br/> |datetime  <br/> |Referenced from the MediaLine Table.  <br/> |
|ConferenceURI  <br/> |nvarchar(450)  <br/> |Conference URI if this is a conference, or DialogID if this is a peer-to-peer session.  <br/> |
|Correlation  <br/> |varchar(max)  <br/> |Correlation ID of the session.  <br/> |
|DialogCategory  <br/> |bit  <br/> |Dialog category; 0 is Skype for Business Server to Mediation Server leg; 1 is Mediation Server to PSTN gateway leg.  <br/> |
|MediationServerBypassFlag  <br/> |bit  <br/> |Indicates whether or not the call was bypassed.  <br/> |
|MediaBypassWarningFlag  <br/> |int  <br/> |This field, if present, indicates why a call was not bypassed even if the bypass IDs matched. For Skype for Business Server, only one value is defined:  <br/> 0x0001 - Unknown bypass ID for Default network adapter  <br/> |
|StartTime  <br/> |datetime  <br/> |Call start time.  <br/> |
|EndTime  <br/> |datetime  <br/> |Call end time.  <br/> |
|CallerPool  <br/> |nvarchar(256)  <br/> |Caller pool FQDN.  <br/> |
|CalleePool  <br/> |nvarchar(256)  <br/> |Callee pool FQDN.  <br/> |
|CallerPAI  <br/> |nvarchar(450)  <br/> |Caller's p-asserted identity URI.  <br/> |
|CalleePAI  <br/> |nvarchar(450)  <br/> |Callee's p-asserted identity URI.  <br/> |
|CallerEndpoint  <br/> |nvarchar(256)  <br/> |Caller's endpoint name.  <br/> |
|CalleeEndpoint  <br/> |nvarchar(256)  <br/> |Caller's endpoint name.  <br/> |
|CallerUserAgent  <br/> |nvarchar(256)  <br/> |Caller's user agent string.  <br/> |
|CallerUserAgentType  <br/> |smallint  <br/> |Type of caller's user agent. See the [UserAgent table](useragent.md) for details. <br/> |
|CallerUserAgentCategory  <br/> |nvarchar (64)  <br/> |Category of caller's user agent. See the [UserAgentDef table (QoE)](useragentdef-qoe.md) for details. <br/> |
|CalleeUserAgent  <br/> |nvarchar(256)  <br/> |Callee's user agent string.  <br/> |
|CalleeUserAgentType  <br/> |smallint  <br/> |Type of user agent for the callee. See the [UserAgent table](useragent.md) for details. <br/> |
|CalleeUserAgentCategory  <br/> |nvarchar (64)  <br/> |User agent category for the callee. See the [UserAgentDef table (QoE)](useragentdef-qoe.md) for details. <br/> |
|CallerURI  <br/> |nvarchar(450)  <br/> |Caller's URI.  <br/> |
|CalleeURI  <br/> |nvarchar(450)  <br/> |Callee's URI.  <br/> |
|CallPrioirty  <br/> |int  <br/> |Priority of the call.  <br/> |
   

