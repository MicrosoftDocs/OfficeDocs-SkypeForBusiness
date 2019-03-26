---
title: "Media view"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 1a7b2e59-082e-4188-98ae-48ae9bd3494a
description: "The Media view stores information about one media type used in a peer-to-peer session. One session would be represented by multiple records in the table, if more than one media type is used. This view was introduced in Microsoft Lync Server 2013."
---

# Media view
 
The Media view stores information about one media type used in a peer-to-peer session. One session would be represented by multiple records in the table, if more than one media type is used. This view was introduced in Microsoft Lync Server 2013.
  
> [!NOTE]
> The Media view should not be used to calculate the media duration for a session. This view contains the signaling details of media exchange in a session. Media exchange is done by the INVITE request, and StartTime indicates the time that the INVITE was sent out. The invite time does not necessarily mean the media start time, because media starts only after the session is accepted. 
  
The Media view contains all of the columns in the [SessionDetails view](sessiondetails-0.md) in addition the ones listed below.
  
|**Column**|**Data Type**|**Details**|
|:-----|:-----|:-----|
|**Media** <br/> |nvarchar(256)  <br/> |Media type. See the [MediaList table](medialist.md) for more information. <br/> |
|**MediaStartTime** <br/> |datetime  <br/> |Time that a media request was sent out.  <br/> |
|**MediaEndTime** <br/> |datetime  <br/> |End time of the session.  <br/> |
   

