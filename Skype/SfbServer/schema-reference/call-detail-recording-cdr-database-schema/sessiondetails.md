---
title: "SessionDetails table"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 2/1/2018
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 783d2508-e31f-4b54-be0c-63aa5ec21c04
description: "Each record represents one peer-to-peer session, which could be a VoIP-VoIP phone call, two-party IM session, or other type of session. You can perform a table join with the Media table to find the details of each media involved in this session."
---

# SessionDetails table
 
Each record represents one peer-to-peer session, which could be a VoIP-VoIP phone call, two-party IM session, or other type of session. You can perform a table join with the [Media table](media.md) to find the details of each media involved in this session.
  
Note that the IsUser1IntegratedWithDeskPhone and the IsUser2IntegratedWithDeskPhone fields have been dropped from the SessionDetails table used in Skype for Business Server 2015.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**SessionIdTime** <br/> |datetime  <br/> |Primary, Foreign  <br/> |Time of session request. Used in conjunction with **SessionIdSeq** to uniquely identify a session. See the [Dialogs table in Skype for Business Server 2015](dialogs.md) for more information. <br/> |
|**SessionIdSeq** <br/> |int  <br/> |Primary, Foreign  <br/> |ID number to identify the session. Used in conjunction with **SessionIdTime** to uniquely identify a session.* See the [Dialogs table in Skype for Business Server 2015](dialogs.md) for more information. <br/> |
|**CorrelationId** <br/> |uniqueidentifier  <br/> ||A GUID to correlate multiple sessions.  <br/> |
|**ReplaceDialogIdTime** <br/> |datetime  <br/> |Foreign  <br/> |ID number to identify the dialog which was replaced by current session. See the [Dialogs table in Skype for Business Server 2015](dialogs.md) for more information. <br/> |
|**ReplaceDialogIdSeq** <br/> |int  <br/> |Foreign  <br/> |ID number to identify the session. Used in conjunction with **ReplacesDialogIdTime** to uniquely identify a session that is replaced by this session. See the [Dialogs table in Skype for Business Server 2015](dialogs.md) for more information. <br/> |
|**User1Id** <br/> |int  <br/> |Foreign  <br/> |ID of one user in the session. See the [Users table](users.md) for more information. <br/> |
|**User2Id** <br/> |int  <br/> |Foreign  <br/> |ID of the other user in the session. See the [Users table](users.md) for more information. <br/> |
|**User1EndpointId** <br/> |uniqueIdentifier  <br/> ||GUID that identifies the endpoint used by the first user in the session.  <br/> This field was introduced in Microsoft Lync Server 2013.  <br/> |
|**User2EndpointId** <br/> |uniqueIdentifier  <br/> ||GUID that identifies the endpoint used by the second user in the session.  <br/> This field was introduced in Microsoft Lync Server 2013.  <br/> |
|**TargetUserId** <br/> |int  <br/> |Foreign  <br/> |The original To user URI in the SIP request. see the [Users table](users.md) for more information. <br/> |
|**SessionStartedById** <br/> |int  <br/> |Foreign  <br/> |ID of the user who started the session. See the [Users table](users.md) for more information. <br/> |
|**OnBehalfOfId** <br/> |int  <br/> |Foreign  <br/> |Indicates the ID of the user of who the caller is on behalf. See the [Users table](users.md) for more information. <br/> |
|**ReferredById** <br/> |int  <br/> |Foreign  <br/> |ID of the user by who the call is referred. See the [Users table](users.md) for more information. <br/> |
|**ServerId** <br/> |int  <br/> |Foreign  <br/> |ID of the front-end server used for this session. See the [Servers table](servers.md) for more information. <br/> |
|**PoolId** <br/> |int  <br/> |Foreign  <br/> |ID of the pool in which the session was captured. See the [Pools table](pools.md) for more information. <br/> |
|**ContentTypeID** <br/> |int  <br/> |Foreign  <br/> |Content type used in the session. See the [ContentTypes table in Skype for Business Server 2015](contenttypes.md) for more information. <br/> |
|**User1ClientVerId** <br/> |int  <br/> |Foreign  <br/> |Client version used by User1. See the [ClientVersions table in Skype for Business Server 2015](clientversions.md) for more information. <br/> |
|**User2ClientVerId** <br/> |int  <br/> |Foreign  <br/> |Client version used by User2. See the [ClientVersions table in Skype for Business Server 2015](clientversions.md) for more information. <br/> |
|**User1EdgeServerid** <br/> |int  <br/> |Foreign  <br/> |Edge Server used by User1. See the [EdgeServers table in Skype for Business Server 2015](edgeservers.md) for more information. <br/> |
|**User2EdgeServerid** <br/> |int  <br/> |Foreign  <br/> |Edge Server used by User2. See the [EdgeServers table in Skype for Business Server 2015](edgeservers.md) for more information. <br/> |
|**IsUser1Internal** <br/> |bit  <br/> ||Whether User1 is logged on from internal or not.  <br/> |
|**IsUser2Internal** <br/> |bit  <br/> ||Whether User2 is logged on from internal or not.  <br/> |
|**InviteTime** <br/> |datetime  <br/> ||The time of the first INVITE request. This field is typically populated by data generated from the initial INVITE message in the session. If there is no INVITE message then the field is populated with the date and time of the first relevant SIP message (BYE, CANCEL, MESSAGE, or INFO). This field is typically populated by data generated from the initial INVITE message in the session. If there is no INVITE message then the field is populated with the date and time of the first relevant SIP message (BYE, CANCEL, MESSAGE, or INFO).  <br/> |
|**ResponseTime** <br/> |datetime  <br/> ||The time of the response to the first INVITE message. This field is typically populated by data generated from the initial INVITE message in the session. If there is no INVITE message then the field is populated with the date and time of the first relevant SIP message (BYE, CANCEL, MESSAGE, or INFO).  <br/> |
|**ResponseCode** <br/> |int  <br/> ||SIP response code to the session invitation. This field is typically populated by data generated from the initial INVITE message in the session. If there is no INVITE message then the field is populated with the date and time of the first relevant SIP message (BYE, CANCEL, MESSAGE, or INFO).  <br/> |
|**DiagnosticId** <br/> |int  <br/> ||Diagnostic ID captured from SIP header.  <br/> |
|**CallPriority** <br/> |int  <br/> |Foreign  <br/> |Call priority. See the [CallPriorities table in Skype for Business Server 2015](callpriorities.md) for more information. <br/> |
|**User1MessageCount** <br/> |int  <br/> ||Number of messages sent by User1 during the session.  <br/> |
|**User2MessageCount** <br/> |int  <br/> ||Number of messages sent by User2 during the session.  <br/> |
|**SessionEndTime** <br/> |datetime  <br/> ||Time at the end of the session.  <br/> |
|**MediaTypes** <br/> |int  <br/> ||A bit set that indicates the media type of this session. Listed are the definitions of the types:  <br/> 1- IM  <br/> 2- FILE_TRANSFER  <br/> 4- REMOTE_ASSISTANCE  <br/> 8- APP_SHARING  <br/> 16- AUDIO  <br/> 32- VIDEO  <br/> 64- APP_INVITE  <br/> |
|**User1Flag** <br/> |smallint  <br/> ||A bit set that indicates the User1 attributes. The following attribute definitions are listed:  <br/> 0x01 - Integrated with desktop phone  <br/> |
|**User2Flag** <br/> |smallint  <br/> ||A bit set that indicates the User2 attributes. The following attribute definitions are listed:  <br/> 0x01 - Integrated with desktop phone  <br/> |
|**CallFlag** <br/> |smallint  <br/> ||A bit set that indicates the call attributes. The following attribute definitions are listed:  <br/> 0x01 - Retried Session  <br/> 0x02 - A call made by agent on behalf of a response group  <br/> |
|**Processed** <br/> |bit  <br/> ||For internal use by the Monitoring service.  <br/> This field was introduced in Microsoft Lync Server 2013.  <br/> |
|**LastModifiedTime** <br/> |Datetime  <br/> ||For internal use by the Monitoring service.  <br/> This field was introduced in Skype for Business Server 2015.  <br/> |
   
\* For most sessions, SessionIdSeq will have the value of 1. If multiple sessions start at exactly the same time, the SessionIdSeq for one will be 1, for another will be 2, and so on.
  

