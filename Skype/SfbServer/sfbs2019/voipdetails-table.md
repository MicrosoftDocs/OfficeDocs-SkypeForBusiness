---
title: "VoipDetails table in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 74ffbb71-569b-4018-be1f-4db2bbafcf36
description: "Each record represents one two-party call in which at least one user is a VoIP user."
---

# VoipDetails table in Lync Server 2013
[]
Each record represents one two-party call in which at least one user is a VoIP user.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**SessionIdTime** <br/> |datetime  <br/> |Primary  <br/> |Time of session request. Used in conjunction with **SessionIdSeq** to uniquely identify a session. See the [Dialogs table in Lync Server 2013](dialogs-table.md) for more information.  <br/> |
|**SessionIdSeq** <br/> |int  <br/> |Primary  <br/> |ID number to identify the session. Used in conjunction with **SessionIdTime** to uniquely identify a session. See the [Dialogs table in Lync Server 2013](dialogs-table.md) for more information.  <br/> |
|**FromNumberId** <br/> |int  <br/> |Foreign  <br/> |**PhoneId** of the caller. See the [Phones table in Lync Server 2013](phones-table.md) for more information. If not NULL and **FromGatewayId** is not NULL, then the caller was a PSTN user.  <br/> |
|**ConnectedNumberId** <br/> |int  <br/> |Foreign  <br/> |**PhoneId** of the call receiver. See the [Phones table in Lync Server 2013](phones-table.md) for more information. If not NULL and **ToGatewayId** is not NULL, then the call receiver was a PSTN user.  <br/> |
|**FromMediationServerId** <br/> |int  <br/> |Foreign  <br/> |The Mediation Server the call is coming from. See the [MediationServers table in Lync Server 2013](mediationservers-table.md) for more information.  <br/> |
|**ToMediationServerId** <br/> |int  <br/> |Foreign  <br/> |The Mediation Server called is going to. See the [MediationServers table in Lync Server 2013](mediationservers-table.md) for more information.  <br/> |
|**FromGatewayId** <br/> |int  <br/> |Foreign  <br/> |Gateway the call is coming from. See the [Gateways table in Lync Server 2013](gateways-table.md) for more information.  <br/> |
|**ToGatewayId** <br/> |int  <br/> |Foreign  <br/> |Gateway the call is going to. See the [Gateways table in Lync Server 2013](gateways-table.md) for more information.  <br/> |
|**DisconnectedbyURIId** <br/> |int  <br/> |Foreign  <br/> |URI of the user who disconnected the call, if the user has a URI. See the [Users table in Lync Server 2013](users-table.md) for more information.  <br/> |
|**DisconnectedbyPhoneId** <br/> |int  <br/> |Foreign  <br/> |ID of the phone that disconnected the call was disconnected from a phone. See the [Phones table in Lync Server 2013](phones-table.md) for more information.  <br/> |
   

