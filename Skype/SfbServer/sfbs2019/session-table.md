---
title: "Session table in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 7f05529c-794d-41ed-bca4-2e85b87b2dec
description: "Each record represents one session which involves audio or audio and video. It contains overall information about the session. A session is defined as an audio or video Session Initiation Protocol (SIP) dialog between two endpoints."
---

# Session table in Lync Server 2013
[]
Each record represents one session which involves audio or audio and video. It contains overall information about the session. A session is defined as an audio or video Session Initiation Protocol (SIP) dialog between two endpoints.
  
|****Column****|****Data Type****|****Key/Index****|****Details****|
|:-----|:-----|:-----|:-----|
|**ConferenceDateTime** <br/> |datetime  <br/> |Primary  <br/> |Referenced from the [Dialog table in Lync Server 2013](dialog-table.md).  <br/> |
|**SessionSeq** <br/> |int  <br/> |Primary  <br/> |Referenced from the [Dialog table in Lync Server 2013](dialog-table.md).  <br/> |
|**ConferenceKey** <br/> |int  <br/> |Foreign  <br/> |Conference key. Referenced from the [Conference table in Lync Server 2013](conference-table.md).  <br/> |
|**CorrelationKey** <br/> |int  <br/> |Foreign  <br/> |Correlation key. Referenced from the [SessionCorrelation table in Lync Server 2013](sessioncorrelation-table.md).  <br/> |
|**DialogCategory** <br/> |bit  <br/> | <br/> |Dialog category; 0 is Lync Server to Mediation Server leg; 1 is Mediation Server to PSTN gateway leg.  <br/> |
|**MediationServerBypassFlag** <br/> |bit  <br/> ||Flag indicating if the call was bypassed or not.  <br/> |
|**MediaBypassWarningFlag** <br/> |int  <br/> ||This field, if present, indicates why a call was not bypassed even if the bypass IDs matched. For Lync Server, only one value is defined.  <br/> 0x0001 - Unknown bypass ID for Default network adapter.  <br/> |
|**StartTime** <br/> |datetime  <br/> | <br/> |Call start time.  <br/> |
|**EndTime** <br/> |datetime  <br/> | <br/> |Call end time.  <br/> |
|**CallerPool** <br/> |int  <br/> |Foreign  <br/> |The pool of the caller. Referenced from the [Pool table in Lync Server 2013](pool-table.md).  <br/> |
|**CalleePool** <br/> |int  <br/> |Foreign  <br/> |The pool of the call receiver. Referenced from the [Pool table in Lync Server 2013](pool-table.md).  <br/> |
|**CalleePAI** <br/> |int  <br/> |Foreign  <br/> |SIP URI in the SIP p-asserted identity (PAI) of the receiving endpoint. Referenced from the [User table in Lync Server 2013](user-table.md).  <br/> |
|**CallerURI** <br/> |int  <br/> |Foreign  <br/> |Caller's URI. Referenced from the [User table in Lync Server 2013](user-table.md).  <br/> |
|**CallerEndpoint** <br/> |int  <br/> |Foreign  <br/> |Caller's endpoint. Referenced from the [Endpoint table in Lync Server 2013](endpoint-table.md).  <br/> |
|**CallerUserAgent** <br/> |bit  <br/> |Foreign  <br/> |Caller's user agent. Referenced from the [UserAgent table in Lync Server 2013](useragent-table.md).  <br/> |
|**CallPriority** <br/> |smallint  <br/> ||The priority of this call.  <br/> |
|**ClassifiedPoorCall** <br/> |bit  <br/> ||This column has been deprecated and is not used in Microsoft Lync Server 2013. Instead, this information is reported on a per-media line bases. Refer to the [MediaLine table in Lync Server 2013](medialine-table.md) for more information.  <br/> |
|**CallerPAI** <br/> |int  <br/> |Foreign  <br/> |P-Asserted-Identity of the user who placed the call. The P-Asserted-Identity (PAI) is used to convey the true identity of the user who placed the call.  <br/> |
|**CalleeEndpoint** <br/> |int  <br/> |Foreign  <br/> |Endpoint that received the call.  <br/> |
|**CalleeUserAgent** <br/> |int  <br/> |Foreign  <br/> |User agent employed by the user who received the call. User agents represent the client endpoint device.  <br/> |
|**CalleeUri** <br/> |int  <br/> |Foreign  <br/> |SIP URI of the user who received the call.  <br/> |
   

