---
title: "UserStatistics table"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: cfaf803b-1679-4169-92d3-533fad3e56ed
description: "The UserStatistics table is a supporting table. Each record in the table stores information about an individual user's usage of the system. This table was introduced in Microsoft Lync Server 2013."
---

# UserStatistics table
 
The UserStatistics table is a supporting table. Each record in the table stores information about an individual user's usage of the system. This table was introduced in Microsoft Lync Server 2013.
  
|**Column**|**Data Type**|**Key/Index**|**Details**|
|:-----|:-----|:-----|:-----|
|**UserId** <br/> |int  <br/> |Primary  <br/> |Unique number identifying this user.  <br/> |
|**LastLogInTime** <br/> |datetime  <br/> ||Last time the user logged in.  <br/> |
|**LastConfOrganizedTime** <br/> |datetime  <br/> ||Last time the user organized a conference.  <br/> |
|**LastCallOrganizerCallFailureTime** <br/> |datetime  <br/> ||Last time the user experienced a call failure.  <br/> |
|**LastConfOrganizerCallFailureTime** <br/> |datetime  <br/> ||Last time the user experienced a call failure as a conference organizer.  <br/> |
   

