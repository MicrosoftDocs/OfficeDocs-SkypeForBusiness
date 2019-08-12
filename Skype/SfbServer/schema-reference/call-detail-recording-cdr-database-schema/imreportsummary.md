---
title: "IMReportSummary table in Skype for Business Server 2015"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/9/2015
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 27ff9453-53f2-4fae-b637-70a086c9df96
description: "The IMReportSummaryTable provides an overall report on the instant messaging sessions held in an organization. This table was introduced in Microsoft Lync Server 2013."
---

# IMReportSummary table in Skype for Business Server 2015
 
The IMReportSummaryTable provides an overall report on the instant messaging sessions held in an organization. This table was introduced in Microsoft Lync Server 2013.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**StartTime** <br/> |datetime  <br/> |Primary  <br/> |Date and time that the instant messaging session began.  <br/> |
|**TimePeriod** <br/> |char(1)  <br/> |Primary  <br/> ||
|**PoolFQDN** <br/> |nvarchar(257)  <br/> |Primary  <br/> |Fully qualified domain name of the pool hosting the session.  <br/> |
|**AuthType** <br/> |int  <br/> |Primary  <br/> |Priority (for example, urgent or non-urgent) of the call. Priority information is stored in the [CallPriorities table in Skype for Business Server 2015](callpriorities.md).  <br/> |
|**SessionCount** <br/> |bigint  <br/> |||
|**MsgCount** <br/> |bigint  <br/> ||Total number of instant messages exchanged during the session.  <br/> |
   

