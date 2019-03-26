---
title: "ConferenceSessionDetails view"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 5858c84d-baed-421d-ad1d-3726e150e256
description: "The ConferenceSessionDetails view stores information about multiparty sessions. Each record represents one conference session, which could be either the session with Focus or the session with a specific conferencing server. This view was introduced in Microsoft Lync Server 2013."
---

# ConferenceSessionDetails view
 
The ConferenceSessionDetails view stores information about multiparty sessions. Each record represents one conference session, which could be either the session with Focus or the session with a specific conferencing server. This view was introduced in Microsoft Lync Server 2013.
  
|**Column**|**Data Type**|**Details**|
|:-----|:-----|:-----|
|**SessionIdTime** <br/> |datetime  <br/> |Time of session request. Used in conjunction with SessionIdSeq to uniquely identify a session. See the [Dialogs table in Skype for Business Server 2015](dialogs.md) for more information. <br/> |
|**SessionIdSeq** <br/> |int  <br/> |ID number to identify the session. Used in conjunction with SessionIdTime to uniquely identify a session. See the [Dialogs table in Skype for Business Server 2015](dialogs.md) for more information. <br/> |
|**InviteTime** <br/> |datetime  <br/> |Time of the first INVITE request. This field is typically populated by data generated from the initial INVITE message in the session. If there is no INVITE message then the field is populated with the date and time of the first relevant SIP message (BYE, CANCEL, MESSAGE, or INFO).  <br/> |
|**ConferenceUri** <br/> |nvarchar(450)  <br/> |URI of the conference.  <br/> |
|**ConferenceUriType** <br/> |nvarchar(256)  <br/> |Type of conference URI. See the [UriTypes table](uritypes.md) for more information. <br/> |
|**ConfInstance** <br/> |uniqueidentifier  <br/> |Identifier that differentiates between instances of recurring conferences. Each recurring conference instance has the same ConferenceURI but a different ConfInstance value.  <br/> |
|**McuConferenceUri** <br/> |nvarchar(450)  <br/> |URI of the conferencing server.  <br/> |
|**McuConferenceUriType** <br/> |nvarchar(256)  <br/> |Type of conferencing server URI. See the [UriTypes table](uritypes.md) for more information. <br/> |
|**UserUri** <br/> |nvarchar(450)  <br/> |URI of the user involved in the session.  <br/> |
|**UserUriType** <br/> |nvarchar(256)  <br/> |Type of URI of the user whose was part of the session. See the [UriTypes table](uritypes.md) for more information. <br/> |
|**UserTenant** <br/> |nvarchar(256)  <br/> |Tenant of the user whose was part of the session. See the [Tenants table](tenants.md) for more information. <br/> |
|**UserEndpointId** <br/> |uniqueidentifier  <br/> |Unique identifier of the user whose was part of the session.  <br/> |
|**EndTime** <br/> |datetime  <br/> |End time of the session.  <br/> |
|**ConferenceClientVersion** <br/> |nvarchar(256)  <br/> |Version of conference server.  <br/> |
|**ConferenceClientType** <br/> |int  <br/> |Type of conference server. See the [UserAgentDef table](useragentdef.md) for more information. <br/> |
|**ConferenceCategory** <br/> |nvarchar(64)  <br/> |Conference server category.  <br/> |
|**UserClientVersion** <br/> |nvarchar(256)  <br/> |Version of client used by the user who participated in the session.  <br/> |
|**UserClientType** <br/> |int  <br/> |Client used by the user who participated in the session. See the [UserAgentDef table](useragentdef.md) for more details. <br/> |
|**UserClientCategory** <br/> |nvarchar(64)  <br/> |Name of the category of the client used by the user who was part of the session.  <br/> |
|**OnBehalfOfUri** <br/> |nvarchar(450)  <br/> |URI of the user on whose behalf the session was started.  <br/> |
|**OnBehalfOfUriType** <br/> |nvarchar(256)  <br/> |Type of URI of the user on whose behalf the session was started. See the [UriTypes table](uritypes.md) for more information. <br/> |
|**OnBehalfOfTenant** <br/> |nvarchar(256)  <br/> |Tenant of the user whose on behalf the session was started. See the [Tenants table](tenants.md) for more information. <br/> |
|**ReferredByUri** <br/> |nvarchar(450)  <br/> |URI of the user who referred the session.  <br/> |
|**ReferredByUriType** <br/> |nvarchar(256)  <br/> |Type of URI of the user who referred the session. See the [UriTypes table](uritypes.md) for more information. <br/> |
|**ReferredByUriTenant** <br/> |nvarchar(256)  <br/> |Tenant of the user who referred the session. See the [Tenants table](tenants.md) for more information. <br/> |
|**DialogId** <br/> |varstring(775)  <br/> |SIP dialog ID. The format is  <br/> :dialog;from-tag;to-tag  <br/> |
|**ReplaceDialogIdTime** <br/> |datetime  <br/> |ID number to identify the dialog which was replaced by current session. See the [Dialogs table in Skype for Business Server 2015](dialogs.md) for more information. <br/> |
|**ReplaceDialogIdSeq** <br/> |int  <br/> |ID number to identify the session. Used in conjunction with ReplaceDialogIdTime to uniquely identify a session that is replaced by this session. See the [Dialogs table in Skype for Business Server 2015](dialogs.md) for more information. <br/> |
|**ReplacesDialogId** <br/> |varchar(775)  <br/> |SIP dialog ID the session replaces. The format of the is:  <br/> dialog;from-tag;to-tag  <br/> |
|**IsStartedByConfServer** <br/> |bit  <br/> |Indicates whether the session was started by the conferencing server.  <br/> |
|**IsEndedByConfServer** <br/> |bit  <br/> |Indicates whether the session was ended by the conferencing server.  <br/> |
|**IsUserInternal** <br/> |bit  <br/> |Indicates whether the user logged on from the internal network.  <br/> |
|**ResponseTime** <br/> |datetime  <br/> |Time of the response to the first INVITE message. This field is typically populated by data generated from the initial INVITE message in the session. If there is no INVITE message then the field is populated with the date and time of the first relevant SIP message (BYE, CANCEL, MESSAGE, or INFO).  <br/> |
|**ResponseCode** <br/> |int  <br/> |SIP response code to the session invitation. This field is typically populated by data generated from the initial INVITE message in the session. If there is no INVITE message then the field is populated with the date and time of the first relevant SIP message (BYE, CANCEL, MESSAGE, or INFO).  <br/> |
|**DiagnosticId** <br/> |int  <br/> |Diagnostic ID captured from session SIP headers.  <br/> |
|**ContentType** <br/> |nvarchar(256)  <br/> |Content type for the session.  <br/> |
|**FrontEnd** <br/> |nvarchar(256)  <br/> |FQDN of the Front End server that captured the data for the session.  <br/> |
|**Pool** <br/> |nvarchar(256)  <br/> |FQDN of the pool that captured the data for the session.  <br/> |
|**MediationServer** <br/> |nvarchar(256)  <br/> |Mediation Server used by the user who participated in the session.  <br/> |
|**Gateway** <br/> |nvarchar(256)  <br/> |Gateway used by the user who participated the session.  <br/> |
|**EdgeServer** <br/> |nvarchar(256)  <br/> |FQDN of the Edge server used by the user who participated in the session.  <br/> |
|**UserFlag** <br/> |smallint  <br/> |Indicates the attributes of the user who participated in the session. The following attribute definitions allowed:  <br/> 0x01 - Integrated with desktop phone  <br/> |
|**CallFlag** <br/> |smallint  <br/> |Indicates the call attributes. The following attribute definitions are allowed:  <br/> 0x01 - Retried Session0  <br/> x02 - A call made by agent on behalf of a Response Group  <br/> |
   

