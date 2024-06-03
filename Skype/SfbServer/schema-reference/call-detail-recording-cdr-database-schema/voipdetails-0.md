---
title: "VoipDetails table"
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
ms.assetid: 74ffbb71-569b-4018-be1f-4db2bbafcf36
description: "Each record represents one two-party call in which at least one user is a VoIP user."
---

# VoipDetails table
 
Each record represents one two-party call in which at least one user is a VoIP user.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**SessionIdTime** <br/> |datetime  <br/> |Primary  <br/> |Time of session request. Used with **SessionIdSeq** to uniquely identify a session. For more information, see the [Dialogs table in Skype for Business Server 2015](dialogs.md) for more. <br/> |
|**SessionIdSeq** <br/> |int  <br/> |Primary  <br/> |ID number to identify the session. Used with **SessionIdTime** to uniquely identify a session. For more information, see the [Dialogs table in Skype for Business Server 2015](dialogs.md). <br/> |
|**FromNumberId** <br/> |int  <br/> |Foreign  <br/> |**PhoneId** of the caller. For more information, see the [Phones table](phones.md). If not NULL and **FromGatewayId** isn't NULL, then the caller was a PSTN user. <br/> |
|**ConnectedNumberId** <br/> |int  <br/> |Foreign  <br/> |**PhoneId** of the call receiver. For more information, see the [Phones table](phones.md). If not NULL and **ToGatewayId** isn't NULL, then the call receiver was a PSTN user. <br/> |
|**FromMediationServerId** <br/> |int  <br/> |Foreign  <br/> |The Mediation Server the call is coming from. For more information, see the [MediationServers table](mediationservers.md). <br/> |
|**ToMediationServerId** <br/> |int  <br/> |Foreign  <br/> |The Mediation Server called is going to. See the [MediationServers table](mediationservers.md) for more information. <br/> |
|**FromGatewayId** <br/> |int  <br/> |Foreign  <br/> |Gateway the call is coming from. For more information, see the [Gateways table in Skype for Business Server 2015](gateways.md). <br/> |
|**ToGatewayId** <br/> |int  <br/> |Foreign  <br/> |Gateway the call is going to. See the [Gateways table in Skype for Business Server 2015](gateways.md) for more information. <br/> |
|**DisconnectedbyURIId** <br/> |int  <br/> |Foreign  <br/> |URI of the user who disconnected the call, if the user has a URI. See the [Users table](users.md) for more information. <br/> |
|**DisconnectedbyPhoneId** <br/> |int  <br/> |Foreign  <br/> |ID of the phone that disconnected the call was disconnected from a phone. See the [Phones table](phones.md) for more information. <br/> |
|**LastModifiedTime** <br/> |Datetime  <br/> ||For internal use by the Monitoring service.  <br/> This field was introduced in Skype for Business Server 2015.  <br/> |
   

