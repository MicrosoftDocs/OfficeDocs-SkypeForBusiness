---
title: "VoipDetails table"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 7/15/2015
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 74ffbb71-569b-4018-be1f-4db2bbafcf36
description: "Each record represents one two-party call in which at least one user is a VoIP user."
---

# VoipDetails table
 
Each record represents one two-party call in which at least one user is a VoIP user.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**SessionIdTime** <br/> |datetime  <br/> |Primary  <br/> |Time of session request. Used in conjunction with **SessionIdSeq** to uniquely identify a session. See the [Dialogs table in Skype for Business Server 2015](dialogs.md) for more information. <br/> |
|**SessionIdSeq** <br/> |int  <br/> |Primary  <br/> |ID number to identify the session. Used in conjunction with **SessionIdTime** to uniquely identify a session. See the [Dialogs table in Skype for Business Server 2015](dialogs.md) for more information. <br/> |
|**FromNumberId** <br/> |int  <br/> |Foreign  <br/> |**PhoneId** of the caller. See the [Phones table](phones.md) for more information. If not NULL and **FromGatewayId** is not NULL, then the caller was a PSTN user. <br/> |
|**ConnectedNumberId** <br/> |int  <br/> |Foreign  <br/> |**PhoneId** of the call receiver. See the [Phones table](phones.md) for more information. If not NULL and **ToGatewayId** is not NULL, then the call receiver was a PSTN user. <br/> |
|**FromMediationServerId** <br/> |int  <br/> |Foreign  <br/> |The Mediation Server the call is coming from. See the [MediationServers table](mediationservers.md) for more information. <br/> |
|**ToMediationServerId** <br/> |int  <br/> |Foreign  <br/> |The Mediation Server called is going to. See the [MediationServers table](mediationservers.md) for more information. <br/> |
|**FromGatewayId** <br/> |int  <br/> |Foreign  <br/> |Gateway the call is coming from. See the [Gateways table in Skype for Business Server 2015](gateways.md) for more information. <br/> |
|**ToGatewayId** <br/> |int  <br/> |Foreign  <br/> |Gateway the call is going to. See the [Gateways table in Skype for Business Server 2015](gateways.md) for more information. <br/> |
|**DisconnectedbyURIId** <br/> |int  <br/> |Foreign  <br/> |URI of the user who disconnected the call, if the user has a URI. See the [Users table](users.md) for more information. <br/> |
|**DisconnectedbyPhoneId** <br/> |int  <br/> |Foreign  <br/> |ID of the phone that disconnected the call was disconnected from a phone. See the [Phones table](phones.md) for more information. <br/> |
|**LastModifiedTime** <br/> |Datetime  <br/> ||For internal use by the Monitoring service.  <br/> This field was introduced in Skype for Business Server 2015.  <br/> |
   

