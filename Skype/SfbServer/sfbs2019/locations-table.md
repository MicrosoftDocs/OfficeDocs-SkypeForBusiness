---
title: "Locations table in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 78dc1b14-5394-4f8e-89d3-4ba593272a04
description: "Each record represents one location reference in an emergency call, like an E9-1-1 call."
---

# Locations table in Lync Server 2013
[]
Each record represents one location reference in an emergency call, like an E9-1-1 call.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**SessionIdTime** <br/> |datetime  <br/> |Primary, Foreign  <br/> |Time of session request. Used in conjunction with **SessionIdSeq** to uniquely identify a session. See the [Dialogs table in Lync Server 2013](dialogs-table.md) for more information.  <br/> |
|**SessionIdSeq** <br/> |int  <br/> |Primary, Foreign  <br/> |ID number to identify the session. Used in conjunction with **SessionIdTime** to uniquely identify a session. See the [Dialogs table in Lync Server 2013](dialogs-table.md) for more information.  <br/> |
|**Location** <br/> |nvarchar(max)  <br/> ||Location of emergency call.  <br/> |
   

