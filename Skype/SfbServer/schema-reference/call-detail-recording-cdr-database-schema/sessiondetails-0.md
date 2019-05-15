---
title: "SessionDetails view"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 7/15/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: ea328c6f-cf22-48dd-8f7f-f1666c9148c8
description: "The SessionDetails view stores information about peer-to-peer sessions, which could be a VoIP-VoIP phone call, two-party IM session, or other type of session. This view was introduced in Microsoft Lync Server 2013."
---

# SessionDetails view
 
The SessionDetails view stores information about peer-to-peer sessions, which could be a VoIP-VoIP phone call, two-party IM session, or other type of session. This view was introduced in Microsoft Lync Server 2013.
  
|**Column**|**Data Type**|**Details**|
|:-----|:-----|:-----|
|**SessionIdTime** <br/> |datetime  <br/> |Time of session request. Used in conjunction with SessionIdSeq to uniquely identify a session. See the [Dialogs table in Skype for Business Server 2015](dialogs.md) Table for more information. <br/> |
|**SessionIdSeq** <br/> |int  <br/> |ID number to identify the session. Used in conjunction with SessionIdTime to uniquely identify a session. See the [Dialogs table in Skype for Business Server 2015](dialogs.md) for more information. <br/> |
|**InviteTime** <br/> |datetime  <br/> |Time of the first INVITE request. This field is typically populated by data generated from the initial INVITE message in the session. If there is no INVITE message then the field is populated with the date and time of the first relevant SIP message (BYE, CANCEL, MESSAGE, or INFO). This field is typically populated by data generated from the initial INVITE message in the session. If there is no INVITE message then the field is populated with the date and time of the first relevant SIP message (BYE, CANCEL, MESSAGE, or INFO).  <br/> |
|**FromUri** <br/> |nvarchar(450)  <br/> |URI of the user who started the session.  <br/> |
|**ToUri** <br/> |nvarchar(450)  <br/> |URI of the user who joined the session.  <br/> |
|**FromUriType** <br/> |nvarchar(256)  <br/> |Type of URI of the user who started the session. See the [UriTypes table](uritypes.md) for more information. <br/> |
|**ToUriType** <br/> |nvarchar(256)  <br/> |Type of URI of the user who joined the session. See the [UriTypes table](uritypes.md) for more information. <br/> |
|**FromTenant** <br/> |nvarchar(450)  <br/> |Tenant of the user who started the session. See the [Tenants table](tenants.md) for more information. <br/> |
|**ToTenant** <br/> |nvarchar(256)  <br/> |The tenant of the user who joined the session. See the [Tenants table](tenants.md) for more information. <br/> |
|**FromEndpointId** <br/> |uniqueidentifier  <br/> |Unique identifier of the endpoint of the user who started the session.  <br/> |
|**ToEndpointId** <br/> |uniqueidentifier  <br/> |Unique identifier of the endpoint of the user who joined the session.  <br/> |
|**EndTime** <br/> |datetime  <br/> |End time of the session.  <br/> |
|**FromMessageCount** <br/> |int  <br/> |Number of messages sent by the user who started the session.  <br/> |
|**ToMessageCount** <br/> |int  <br/> |Number of messages sent by the user who joined the session.  <br/> |
|**FromClientVersion** <br/> |nvarchar(256)  <br/> |Version of client used by the user who started the session.  <br/> |
|**FromClientType** <br/> |int  <br/> |Client used by the user who started the session. See the [UserAgentDef table](useragentdef.md) for more details. <br/> |
|**FromClientCategory** <br/> |nvarchar(64)  <br/> |Name of the category of the client used by the user who started the session.  <br/> |
|**ToClientVersion** <br/> |nvarchar(256)  <br/> |Version of client used by the user who joined the session  <br/> |
|**ToClientType** <br/> |int  <br/> |Client used by the user who joined the session. See the [UserAgentDef table](useragentdef.md) for more details. <br/> |
|**ToClientCategory** <br/> |nvarchar(64)  <br/> |Name of the category of the client used by the user who joined the session.  <br/> |
|**TargetUri** <br/> |nvarchar(450)  <br/> |URI of the target user of the session.  <br/> |
|**TargetUriType** <br/> |nvarchar(450)  <br/> |Type of URI of the target user for the session. See the [UriTypes table](uritypes.md) for more information. <br/> |
|**OnBehalfOfUri** <br/> |nvarchar(450)  <br/> |URI of the user on whose behalf the session was started.  <br/> |
|**OnnnBehalfOfUriType** <br/> |nvarchar(256)  <br/> |Type of URI of the user on whose behalf the session was started. See the [UriTypes table](uritypes.md) for more information. <br/> |
|**OnBehalfOfTenant** <br/> |nvarchar(256)  <br/> |Tenant of the user whose on behalf the session was started. See the [Tenants table](tenants.md) for more information. <br/> |
|**ReferredByUri** <br/> |nvarchar(450)  <br/> |URI of the user who referred the session.  <br/> |
|**ReferredByUriType** <br/> |nvarchar(256)  <br/> |Type of URI of the user who referred the session. See the [UriTypes table](uritypes.md) for more information. <br/> |
|**ReferredByTenant** <br/> |nvarchar(256)  <br/> |Tenant of the user who referred the session. See the [Tenants table](tenants.md) for more information. <br/> |
|**DialogId** <br/> |varchar(775)  <br/> |SIP dialog ID. The format is:  <br/> dialog;from-tag;to-tag  <br/> |
|**CorrelationId** <br/> |uniqueidentifier  <br/> |GUID used to correlate multiple sessions.  <br/> |
|**ReplaceDialogIdTime** <br/> |datetime  <br/> |Time of the dialog which was replaced by the session. Used in conjunction with ReplaceDialogIdSeq to uniquely identify a dialog that is replaced by the session. See the [Dialogs table in Skype for Business Server 2015](dialogs.md) for more information. <br/> |
|**ReplaceDialogIdSeq** <br/> |int  <br/> |ID number to identify the session. Used in conjunction with ReplaceDialogIdTime to uniquely identify a dialog that is replaced by the session. See the [Dialogs table in Skype for Business Server 2015](dialogs.md) for more information. <br/> |
|**ReplacesDialogId** <br/> |varchar(775)  <br/> |SIP dialog ID the session replaces. The format is:  <br/> dialog;from-tag;to-tag  <br/> |
|**ResponseTime** <br/> |datetime  <br/> |Time of the response to the first INVITE message. This field is typically populated by data generated from the initial INVITE message in the session. If there is no INVITE message then the field is populated with the date and time of the first relevant SIP message (BYE, CANCEL, MESSAGE, or INFO).  <br/> |
|**ResponseCode** <br/> |int  <br/> |SIP response code to the session invitation. This field is typically populated by data generated from the initial INVITE message in the session. If there is no INVITE message then the field is populated with the date and time of the first relevant SIP message (BYE, CANCEL, MESSAGE, or INFO).  <br/> |
|**DiagnosticId** <br/> |int  <br/> |Diagnostic ID captured from SIP headers.  <br/> |
|**ContentType** <br/> |nvarchar(256)  <br/> |Type of content for the session.  <br/> |
|**FrontEnd** <br/> |nvarchar(256)  <br/> |FQDN of the Front End server that captured the data for the session.  <br/> |
|**Pool** <br/> |nvarchar(256)  <br/> |FQDN of the pool that captured the data for the session.  <br/> |
|**FromEdgeServer** <br/> |nvarchar(256)  <br/> |FQDN of the Edge server used by the user who started the session.  <br/> |
|**ToEdgeServer** <br/> |nvarchar(256)  <br/> |FQDN of the Edge server used by the user who started the session  <br/> |
|**IsFromInternal** <br/> |bit  <br/> |Indicates whether the user who started the session logged on from the internal network.  <br/> |
|**IsToInternal** <br/> |bit  <br/> |Indicates whether the user who joined the session logged on from the internal network.  <br/> |
|**CallPriority** <br/> |nvarchar(256)  <br/> |Call priority of the session.  <br/> |
|**FromUserFlag** <br/> |smallint  <br/> |Indicates the attributes of the user who started the session. The following attribute definitions are allowed:  <br/> 0x01 - Integrated with desktop phone  <br/> |
|**ToUserFlag** <br/> |smallint  <br/> |Indicates the attributes of the user who started the session. The following attribute definitions are allowed:  <br/> 0x01 - Integrated with desktop phone  <br/> |
|**CallFlag** <br/> |smallint  <br/> |Indicates the call attributes. The following attribute definitions are allowed:  <br/> 0x01 - Retried Session  <br/> 0x02 - A call made by agent on behalf of a Response Group  <br/> |
|**Location** <br/> |varchar(max)  <br/> |Location of emergency call.  <br/> |
|**LastModifiedTime** <br/> |Datetime  <br/> |For internal use by the Monitoring service.  <br/> This field was introduced in Skype for Business Server 2015.  <br/> |
   

