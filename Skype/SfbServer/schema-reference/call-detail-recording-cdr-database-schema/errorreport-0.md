---
title: "ErrorReport view"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: ca873f7e-b18b-4eaf-8db0-5f9d5a9b60a1
description: "The ErrorReport view stores information about errors reported. Each record is one error occurrence. The errors are captured either by the CDR agent running on the front-end server or sent from the client. This view was introduced in Microsoft Lync Server 2013."
---

# ErrorReport view
 
The ErrorReport view stores information about errors reported. Each record is one error occurrence. The errors are captured either by the CDR agent running on the front-end server or sent from the client. This view was introduced in Microsoft Lync Server 2013.
  
|**Column**|**Data Type**|**Details**|
|:-----|:-----|:-----|
|**ErrorTime** <br/> |datetime  <br/> |Time of error occurred. Used in conjunction with ErrorReportSeq to uniquely identify an error.  <br/> |
|**ErrorReportSeq** <br/> |int  <br/> |ID number to identify the error. Used in conjunction with ErrorTime to uniquely identify an error.  <br/> |
|**MsDiagId** <br/> |int  <br/> |Diagnostic ID for the error report.  <br/> |
|**FromUri** <br/> |nvarchar(450)  <br/> |URI of the user who originated the error.  <br/> |
|**FromUriType** <br/> |nvarchar(256)  <br/> |Type of URI of the user who originated the error. See the [UriTypes table](uritypes.md) for more information. <br/> |
|**FromTenant** <br/> |nvarchar(256)  <br/> |Tenant of the user who originated the error. See the [Tenants table](tenants.md) for more information. <br/> |
|**ToUri** <br/> |nvarchar(450)  <br/> |URI of the user who was the target of the error report.  <br/> |
|**ToUriType** <br/> |nvarchar(256)  <br/> |Type of URI of the user who target of the error report. See the UriTypes Table for more information.  <br/> |
|**ToTenant** <br/> |nvarchar(256)  <br/> |Tenant of the user who target of the error report. See the [Tenants table](tenants.md) for more information. <br/> |
|**ConferenceUri** <br/> |nvarchar(450)  <br/> |URI of the conference that was the target of the error report.  <br/> |
|**ConferenceUriType** <br/> |nvarchar(256)  <br/> |URI type of the conference that was the target of the error report. See the [UriTypes table](uritypes.md) for more information. <br/> |
|**SessionIdTime** <br/> |datetime  <br/> |Time of session request that originated the error report. Used in conjunction with SessionIdSeq to uniquely identify a session. See the [Dialogs table in Skype for Business Server 2015](dialogs.md) for more information. <br/> |
|**SessionIdSeq** <br/> |int  <br/> |ID number to identify the session request that originated the error report. Used in conjunction with SessionIdTime to uniquely identify a session. See the [Dialogs table in Skype for Business Server 2015](dialogs.md) for more information. <br/> |
|**DialogId** <br/> |varstring(775)  <br/> |SIP dialog ID of session that originated the error. The format is:  <br/> dialog;from-tag;to-tag  <br/> This data can be converted to text format by using this syntax:  <br/> cast(cast(ExternalId as varbinary(max)) as varchar(max))  <br/> |
|**ClientVersion** <br/> |nvarchar(256)  <br/> |Version of client used by the user who originated the error.  <br/> |
|**ClientType** <br/> |int  <br/> |Client used by the user who originated the error. See the [UserAgentDef table](useragentdef.md) for more details. <br/> |
|**ClientCategory** <br/> |nvarchar(64)  <br/> |Name of the category of the client used by the user who originated the error.  <br/> |
|**Source** <br/> |nvarchar(256)  <br/> |Name of server that originated the error (if report was sent from a server component).  <br/> |
|**Application** <br/> |nvarchar(256)  <br/> |Name of application that originated the error (if report was sent from a server component).  <br/> |
|**ResponseCode** <br/> |int  <br/> |SIP response code to the session of the SIP message containing the error report.  <br/> |
|**RequestType** <br/> |varchar(max)  <br/> |Type of request that failed.  <br/> |
|**ContentType** <br/> |varchar(max)  <br/> |Content type of the request that failed.  <br/> |
|**CallType** <br/> |nvarchar(256)  <br/> |Type of session. See the [CallType table in Skype for Business Server 2015](calltype.md) for more information. <br/> |
|**TelemetryId** <br/> |uniqueidentifier  <br/> |Unique identifier correlating join time information for the different components involved in a conference.  <br/> |
|**SetupTime** <br/> |int  <br/> |Time (in milliseconds) required for a specific component to join a conference.  <br/> |
|**IsCapturedByServer** <br/> |bit  <br/> |Indicates whether the error report was captured by the CDR agent running on the Front End server, or sent by the client.  <br/> |
|**Flag** <br/> |smallint  <br/> |Reserved for future use.  <br/> |
|**MsDiagHeader** <br/> |varchar(max)  <br/> |Additional information about the error.  <br/> |
|**FrontEnd** <br/> |nvarchar  <br/> |Fully qualified domain name of the Front End server that submitted the report.  <br/> |
|**Pool** <br/> |nvarchar  <br/> |Fully qualified domain name of the pool containing the Front End server that submitted the report.  <br/> |
   

