---
title: "ConferenceSessionDetails table in Skype for Business Server 2015"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 7/15/2015
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 9eae6a54-69fd-4966-aa17-7ecee1297ad8
description: "Each record represents one conference session, which could be either the session with Focus or the session with a specific conferencing server."
---

# ConferenceSessionDetails table in Skype for Business Server 2015
 
Each record represents one conference session, which could be either the session with Focus or the session with a specific conferencing server.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**SessionIdTime** <br/> |Datetime  <br/> |Primary, Foreign  <br/> |Time of session request; used in conjunction with **SessionIdSeq** to uniquely identify a conference session. See the [Dialogs table in Skype for Business Server 2015](dialogs.md) for more information. <br/> |
|**SessionIdSeq** <br/> |int  <br/> |Primary, Foreign  <br/> |ID number to identify the session. Used in conjunction with **SessionIdTime** to uniquely identify a conference session. See the [Dialogs table in Skype for Business Server 2015](dialogs.md) for more information. * <br/> |
|**ConferenceUriId** <br/> |int  <br/> |Foreign  <br/> |Focus conference URI related to this session. See the [ConferenceUris table in Skype for Business Server 2015](conferenceuris.md) for more information. This URI is a Focus-based conference URI. <br/> |
|**ConfInstance** <br/> |uniqueIdentifier  <br/> ||Identifier that differentiates between instances of recurring conferences. Each recurring conference instance has the same ConferenceURI but a different ConfInstance value.  <br/> This field was introduced in Microsoft Lync Server 2013.  <br/> |
|**McuConferenceUriId** <br/> |int  <br/> |Foreign  <br/> |Conferencing server conference URI related to this session. See the [ConferenceUris table in Skype for Business Server 2015](conferenceuris.md) for more information. This URI is the conferencing server-based conference URI. For Focus conference sessions, this column will be null. <br/> |
|**UserId** <br/> |int  <br/> |Foreign  <br/> |ID of one user in the conference session. See the [Users table](users.md) for more information. <br/> |
|**UserEndpointId** <br/> |uniqueidentifier  <br/> ||A GUID to identify the instance of endpoint. For example, if one user logs on to different machines with the same account, then each machine will have a different endpoint ID.  <br/> |
|**OnBehalfOfId** <br/> |int  <br/> |Foreign  <br/> |Indicates the ID of the user of who the caller is on behalf. See the [Users table](users.md) for more information. <br/> |
|**ReferredById** <br/> |int  <br/> |Foreign  <br/> |ID of the user by who the call is referred. See the [Users table](users.md) for more information. <br/> |
|**UserClientVersionId** <br/> |int  <br/> |Foreign  <br/> |Client version used by the conference user. See the [ClientVersions table in Skype for Business Server 2015](clientversions.md) for more information. <br/> |
|**ConfClientVersionId** <br/> |int  <br/> |Foreign  <br/> |Client version used by the conference server. See the [ClientVersions table in Skype for Business Server 2015](clientversions.md) for more information. <br/> |
|**ReplaceDialogIdTime** <br/> |datetime  <br/> |Foreign  <br/> |ID number to identify the dialog which was replaced by current session. See the [Dialogs table in Skype for Business Server 2015](dialogs.md) for more information. <br/> |
|**ReplaceDialogIdSeq** <br/> |int  <br/> |Foreign  <br/> |ID number to identify the session. Used in conjunction with **ReplacesDialogIdTime** to uniquely identify a session that is replaced by this session. See the [Dialogs table in Skype for Business Server 2015](dialogs.md) for more information. <br/> |
|**IsStartedByConfServer** <br/> |bit  <br/> ||Indicates if the session started by the conferencing Server.  <br/> |
|**IsEndedByConfServer** <br/> |bit  <br/> ||Indicates if the session ended by the conferencing server.  <br/> |
|**IsUserInternal** <br/> |bit  <br/> ||Whether user is logged on from internal or not.  <br/> |
|**ResponseCode** <br/> |int  <br/> ||Session Initiation Protocol (SIP) response code to the session invitation. This field is typically populated by data generated from the initial INVITE message in the session. If there is no INVITE message then the field is populated with the date and time of the first relevant SIP message (BYE, CANCEL, MESSAGE, or INFO).  <br/> |
|**DiagnosticId** <br/> |int  <br/> ||Diagnostic ID captured from SIP header.  <br/> |
|**ServerId** <br/> |int  <br/> |Foreign  <br/> |ID of the front-end server used for this session. See the [Servers table](servers.md) for more information. <br/> |
|**PoolId** <br/> |int  <br/> |Foreign  <br/> |ID of the pool in which the session was captured. See the [Pools table](pools.md) for more information. <br/> |
|**MediationServerId** <br/> |int  <br/> |Foreign  <br/> |The Mediation Server the call is using. See the [MediationServers table](mediationservers.md) for more information. <br/> |
|**GatewayId** <br/> |int  <br/> |Foreign  <br/> |The gateway the call is using. See the [Gateways table in Skype for Business Server 2015](gateways.md) for more information. <br/> |
|**EdgeServerId** <br/> |int  <br/> |Foreign  <br/> |The Edge Server the call is using. See the [EdgeServers table in Skype for Business Server 2015](edgeservers.md) for more information. <br/> |
|**ContentTypeId** <br/> |int  <br/> |Foreign  <br/> |Content type used in the session. See the [ContentTypes table in Skype for Business Server 2015](contenttypes.md) for more information. <br/> |
|**InviteTime** <br/> |datetime  <br/> ||The time of the first INVITE request. This field is typically populated by data generated from the initial INVITE message in the session. If there is no INVITE message then the field is populated with the date and time of the first relevant SIP message (BYE, CANCEL, MESSAGE, or INFO).  <br/> |
|**ResponseTime** <br/> |datetime  <br/> ||Time of the first SIP RESPONSE. This field is typically populated by data generated from the initial INVITE message in the session. If there is no INVITE message then the field is populated with the date and time of the first relevant SIP message (BYE, CANCEL, MESSAGE, or INFO).  <br/> |
|**SessionEndTime** <br/> |datetime  <br/> ||The time when the session is ended.  <br/> |
|**UriTypeId** <br/> |tinyint  <br/> |Foreign  <br/> |Contains the MCU URI type value from the [UriTypes table](uritypes.md). This field is used for improving query performance.  <br/> This field was introduced in Microsoft Lync Server 2013.  <br/> |
|**UserFlag** <br/> |smallint  <br/> || A bit set that indicates the user attributes. The following attribute definitions are listed: <br/>  Integrated with desktop phone - 1 <br/> |
|**CallFlag** <br/> |smallint  <br/> || A bit set that indicates the call attributes. The following attribute definitions are listed: <br/>  Retried Session - 1 <br/> |
|**LastModifiedTime** <br/> |Datetime  <br/> ||For internal use by the Monitoring service.  <br/> This field was introduced in Skype for Business Server 2015.  <br/> |
   
\* For most sessions, SessionIdSeq will have the value of 1. If multiple sessions start at exactly the same time, the SessionIdSeq for one will be 1, for another will be 2, and so on.
  

