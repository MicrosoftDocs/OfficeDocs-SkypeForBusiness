---
title: "ConferenceSessionDetails table in Skype for Business Server 2015"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 7/15/2015
audience: ITPro
ms.topic: article
ms.service: skype-for-business-server
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.assetid: 9eae6a54-69fd-4966-aa17-7ecee1297ad8
description: "Each record represents one conference session, which could be either the session with Focus or the session with a specific conferencing server."
---

# ConferenceSessionDetails table in Skype for Business Server 2015
 
Each record represents one conference session, which could be either the session with Focus or the session with a specific conferencing server.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**SessionIdTime** <br/> |Datetime  <br/> |Primary, Foreign  <br/> |Time of session request; used with **SessionIdSeq** to uniquely identify a conference session. For more information, see the [Dialogs table in Skype for Business Server 2015](dialogs.md). <br/> |
|**SessionIdSeq** <br/> |int  <br/> |Primary, Foreign  <br/> |ID number to identify the session. Used with **SessionIdTime** to uniquely identify a conference session. For more information, see the [Dialogs table in Skype for Business Server 2015](dialogs.md). * <br/> |
|**ConferenceUriId** <br/> |int  <br/> |Foreign  <br/> |Focus conference URI related to this session. For more information, see the [ConferenceUris table in Skype for Business Server 2015](conferenceuris.md). This URI is a Focus-based conference URI. <br/> |
|**ConfInstance** <br/> |uniqueIdentifier  <br/> ||Identifier that differentiates between instances of recurring conferences. Each recurring conference instance has the same ConferenceURI but a different ConfInstance value.  <br/> This field was introduced in Microsoft Lync Server 2013.  <br/> |
|**McuConferenceUriId** <br/> |int  <br/> |Foreign  <br/> |Conferencing server conference URI related to this session. For more information, see the [ConferenceUris table in Skype for Business Server 2015](conferenceuris.md). This URI is the conferencing server-based conference URI. For Focus conference sessions, this column is null. <br/> |
|**UserId** <br/> |int  <br/> |Foreign  <br/> |ID of one user in the conference session. For more information, see the [Users table](users.md). <br/> |
|**UserEndpointId** <br/> |uniqueidentifier  <br/> ||A GUID to identify the instance of endpoint. For example, if one user signs in different machines with the same account, then each machine has a different endpoint ID.  <br/> |
|**OnBehalfOfId** <br/> |int  <br/> |Foreign  <br/> |Indicates the ID of the user of who the caller is on behalf. For more information, see the [Users table](users.md). <br/> |
|**ReferredById** <br/> |int  <br/> |Foreign  <br/> |ID of the user by who the call is referred. For more information, see the [Users table](users.md) for more information. <br/> |
|**UserClientVersionId** <br/> |int  <br/> |Foreign  <br/> |Client version used by the conference user. For more information, see the [ClientVersions table in Skype for Business Server 2015](clientversions.md) for more information. <br/> |
|**ConfClientVersionId** <br/> |int  <br/> |Foreign  <br/> |Client version used by the conference server. For more information, see the [ClientVersions table in Skype for Business Server 2015](clientversions.md). <br/> |
|**ReplaceDialogIdTime** <br/> |datetime  <br/> |Foreign  <br/> |ID number to identify the dialog, which is replaced by current session. For more information, ee the [Dialogs table in Skype for Business Server 2015](dialogs.md). <br/> |
|**ReplaceDialogIdSeq** <br/> |int  <br/> |Foreign  <br/> |ID number to identify the session. Used with **ReplacesDialogIdTime** to uniquely identify a session that is replaced by this session. For more information, see the [Dialogs table in Skype for Business Server 2015](dialogs.md). <br/> |
|**IsStartedByConfServer** <br/> |bit  <br/> ||Indicates if the session started by the conferencing Server.  <br/> |
|**IsEndedByConfServer** <br/> |bit  <br/> ||Indicates if the session ended by the conferencing server.  <br/> |
|**IsUserInternal** <br/> |bit  <br/> ||Whether user is logged on from internal or not.  <br/> |
|**ResponseCode** <br/> |int  <br/> ||Session Initiation Protocol (SIP) response code to the session invitation. This field is typically populated by data generated from the initial INVITE message in the session. If there's no INVITE message, then the field is populated with the date and time of the first relevant SIP message (BYE, CANCEL, MESSAGE, or INFO).  <br/> |
|**DiagnosticId** <br/> |int  <br/> ||Diagnostic ID captured from SIP header.  <br/> |
|**ServerId** <br/> |int  <br/> |Foreign  <br/> |ID of the front-end server used for this session. For more information, see the [Servers table](servers.md). <br/> |
|**PoolId** <br/> |int  <br/> |Foreign  <br/> |ID of the pool in which the session was captured. See the [Pools table](pools.md). <br/> |
|**MediationServerId** <br/> |int  <br/> |Foreign  <br/> |The Mediation Server the call is using. For more information, see the [MediationServers table](mediationservers.md). <br/> |
|**GatewayId** <br/> |int  <br/> |Foreign  <br/> |The gateway the call is using. For more information, see the [Gateways table in Skype for Business Server 2015](gateways.md). <br/> |
|**EdgeServerId** <br/> |int  <br/> |Foreign  <br/> |The Edge Server the call is using. For more information, see the [EdgeServers table in Skype for Business Server 2015](edgeservers.md). <br/> |
|**ContentTypeId** <br/> |int  <br/> |Foreign  <br/> |Content type used in the session. For more information, see the [ContentTypes table in Skype for Business Server 2015](contenttypes.md). <br/> |
|**InviteTime** <br/> |datetime  <br/> ||The time of the first INVITE request. This field is typically populated by data generated from the initial INVITE message in the session. If there's no INVITE message, then the field is populated with the date and time of the first relevant SIP message (BYE, CANCEL, MESSAGE, or INFO).  <br/> |
|**ResponseTime** <br/> |datetime  <br/> ||Time of the first SIP RESPONSE. This field is typically populated by data generated from the initial INVITE message in the session. If there's no INVITE message, then the field is populated with the date and time of the first relevant SIP message (BYE, CANCEL, MESSAGE, or INFO).  <br/> |
|**SessionEndTime** <br/> |datetime  <br/> ||The time when the session is ended.  <br/> |
|**UriTypeId** <br/> |tinyint  <br/> |Foreign  <br/> |Contains the MCU URI type value from the [UriTypes table](uritypes.md). This field is used for improving query performance.  <br/> This field was introduced in Microsoft Lync Server 2013.  <br/> |
|**UserFlag** <br/> |smallint  <br/> || A bit set that indicates the user attributes. The following attribute definitions are listed: <br/>  Integrated with desktop phone - 1 <br/> |
|**CallFlag** <br/> |smallint  <br/> || A bit set that indicates the call attributes. The following attribute definitions are listed: <br/>  Retried Session - 1 <br/> |
|**LastModifiedTime** <br/> |Datetime  <br/> ||For internal use by the Monitoring service.  <br/> This field was introduced in Skype for Business Server 2015.  <br/> |
   
\* For most sessions, SessionIdSeq has the value of 1. If multiple sessions start at exactly the same time, the SessionIdSeq for one is 1, for another is 2, and so on.
  

