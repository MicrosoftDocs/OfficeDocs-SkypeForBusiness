---
title: "ProgressReport view"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: b49f3fc7-0e2f-498f-8505-aaaf54e435f9
description: "The ProgressReport view stores information about completed sessions. Progress reports will be written only for calls and sessions that Lync Server 2013 determines might be useful for diagnostic purposes. This view was introduced in Microsoft Lync Server 2013."
---

# ProgressReport view
 
The ProgressReport view stores information about completed sessions. Progress reports will be written only for calls and sessions that Lync Server 2013 determines might be useful for diagnostic purposes. This view was introduced in Microsoft Lync Server 2013.
  
> [!NOTE]
> The ErrorTime, ErrorReportSeq and ProgressReportSeq fields don't necessarily refer to errors but to messages that indicate the status of calls or messages. 
  
|**Column**|**Data Type**|**Details**|
|:-----|:-----|:-----|
|**ErrorTime** <br/> |datetime  <br/> |Time of error occurred. Used in conjunction with ErrorReportSeq to uniquely identify an error.  <br/> |
|**ErrorReportSeq** <br/> |int  <br/> |ID number to identify the error. Used in conjunction with ErrorTime to uniquely identify an error.  <br/> |
|**ProgressReportSeq** <br/> |int  <br/> |ID to identify the progress report. Used to distinguish progress reports of the same error report.  <br/> |
|**MsDiagId** <br/> |int  <br/> |Diagnostic ID for the error report.  <br/> |
|**Source** <br/> |nvarchar(256)  <br/> |Name of server that originated the error (if report was sent from a server component).  <br/> |
|**Application** <br/> |nvarchar(256)  <br/> |Name of application that originated the error (if report was sent from a server component).  <br/> |
|**TelemetryId** <br/> |uniqueidentifier  <br/> |Unique identifier correlating join time information for the different components involved in a conference.  <br/> |
|**SessionSetupTime** <br/> |int  <br/> |Time (in milliseconds) required for a specific component to join a conference.  <br/> |
|**MsDiagHeader** <br/> |varchar(max)  <br/> |Additional error information.  <br/> |
   

