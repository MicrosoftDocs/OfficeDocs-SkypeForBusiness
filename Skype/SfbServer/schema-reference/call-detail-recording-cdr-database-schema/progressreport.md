---
title: "ProgressReport table"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 10/20/2015
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 38e5f060-5e9b-4185-87b2-7ef61c4bb75f
description: "Progress reports are based on data uploaded by the client to the database after a call or session is completed. Progress reports will be written only for calls and sessions that Skype for Business Server 2015 determines might be useful for diagnostic purposes."
---

# ProgressReport table
 
Progress reports are based on data uploaded by the client to the database after a call or session is completed. Progress reports will be written only for calls and sessions that Skype for Business Server 2015 determines might be useful for diagnostic purposes.
  
The ErrorTime, ErrorReportSeq and ProgressReportSeq fields don't necessarily refer to errors but to messages that indicate the status of calls or messages.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**ErrorTime** <br/> |datetime  <br/> |Primary, Foreign  <br/> |Date and time of the progress error report that contains this progress report. See the [ErrorReport table in Skype for Business Server 2015](errorreport.md) for more information. <br/> |
|**ErrorId** <br/> |int  <br/> |Primary, Foreign  <br/> |ID number used in conjunction with ErrorTime, ProgressReportSeq to uniquely identify a progress report. See the [ErrorReport table in Skype for Business Server 2015](errorreport.md) for more information. <br/> |
|**ErrorReportSeq** <br/> |int  <br/> |Primary, Foreign  <br/> |ID number that identifies the error report. ErrorReporSeq is used in conjunction with ErrorTime to uniquely identify an error report. See the [ErrorReport table in Skype for Business Server 2015](errorreport.md) for more information <br/> This field was introduced in Microsoft Lync Server 2013.  <br/> |
|**ProgressReportSeq** <br/> |int  <br/> |Primary  <br/> |ID number to identify the progress report. Used in conjunction with ErrorTime and ErrorReportSeq to uniquely identify a progress report.  <br/> |
|**MsDiagId** <br/> |int  <br/> ||Diagnostic ID of the progress report.  <br/> This field was introduced in Microsoft Lync Server 2013.  <br/> |
|**SourceId** <br/> |int  <br/> |Foreign  <br/> |Server that sent the error report (if the report was sent from a server component). See the [Servers table](servers.md) for more information.This field was introduced in Microsoft Lync Server 2013. <br/> |
|**ApplicationId** <br/> |int  <br/> ||The Lync Server process that the report is about. See the Application Table for more information.  <br/> |
|**Detail** <br/> |image  <br/> ||Progress report details, stored in binary format to save space.This data can be converted to text format using this syntax:  <br/> cast(cast(Detail as varbinary(max)) as varchar(max))  <br/> |
|**TelemetryId** <br/> |uniqueIdentifier  <br/> ||Unique identifier that correlates join time information for the different components involved in a conference.  <br/> This field was introduced in Microsoft Lync Server 2013.  <br/> |
|**SessionSetupTime** <br/> |int  <br/> ||Time (in milliseconds) for a specific component to join a conference.  <br/> This field was introduced in Microsoft Lync Server 2013.  <br/> |
   

