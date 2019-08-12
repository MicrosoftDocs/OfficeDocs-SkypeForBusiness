---
title: "ClientVersions view"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/9/2015
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: caf7678f-83a0-46c8-83cc-fee4c3991f52
description: "The ClientVersions view stores information about the various client types and versions that have participated in sessions recorded in the database. Each record in the view represents one client version. This view was introduced in Microsoft Lync Server 2013."
---

# ClientVersions view
 
The ClientVersions view stores information about the various client types and versions that have participated in sessions recorded in the database. Each record in the view represents one client version. This view was introduced in Microsoft Lync Server 2013.
  
> [!NOTE]
> There may be multiple records for certain columns. 
  
|**Column**|**Data Type**|**Details**|
|:-----|:-----|:-----|
|**VersionId** <br/> |int  <br/> |Unique number identifying this client type and version.  <br/> |
|**Version** <br/> |nvarchar(256)  <br/> |Represents the user agent.  <br/> |
|**ClientType** <br/> |int  <br/> |Type of client.  <br/> |
|**ClientCategory** <br/> |nvarchar(64)  <br/> |Category that the client belongs to. For example, the client Conferencing_Attendant_1.0 belongs to the ClientCategory CAA.  <br/> |
   

