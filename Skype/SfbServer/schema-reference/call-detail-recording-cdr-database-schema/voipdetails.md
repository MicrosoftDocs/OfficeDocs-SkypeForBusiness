---
title: "VoIPDetails view"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 14c44736-71ba-4fc5-82c7-1df65bf6261c
description: "The VoIPDetails view stores information about peer-to-peer sessions, where at least one user is a VoIP user. This view was introduced in Microsoft Lync Server 2013."
---

# VoIPDetails view
 
The VoIPDetails view stores information about peer-to-peer sessions, where at least one user is a VoIP user. This view was introduced in Microsoft Lync Server 2013.
  
> [!NOTE]
> The VoIPDetails view contains all of the columns in the [SessionDetails view](sessiondetails-0.md) in addition the columns listed below.
  
|**Column**|**Data Type**|**Details**|
|:-----|:-----|:-----|
|**FromPhone** <br/> |nvarchar(450)  <br/> |Phone URI of the user who started the session.  <br/> |
|**ToPhone** <br/> |nvarchar(450)  <br/> |Phone URI of the user who joined the session.  <br/> |
|**DisconnectedByUri** <br/> |nvarchar(450)  <br/> |URI of the user who disconnected the session.  <br/> |
|**DisconnectedByUriType** <br/> |nvarchar(256)  <br/> |Type of URI of the user who disconnected the session. See the [UriTypes table](uritypes.md) for more information. <br/> |
|**DisconnectedByTenant** <br/> |nvarchar(256)  <br/> |Tenant of the user who disconnected the session.  <br/> |
|**DisconnectedByPhone** <br/> |nvarchar(450)  <br/> |Phone URI of the user who disconnected the session.  <br/> |
|**FromMediationServer** <br/> |nvarchar(256)  <br/> |Mediation Server used by the user who started the session.  <br/> |
|**ToMediationServer** <br/> |nvarchar(256)  <br/> |Mediation Server used by the user who joined the session.  <br/> |
|**FromGateway** <br/> |nvarchar(256)  <br/> |Gateway used by the user who started the session.  <br/> |
|**ToGateway** <br/> |nvarchar(256)  <br/> |Gateway used by the user who joined the session.  <br/> |
   

