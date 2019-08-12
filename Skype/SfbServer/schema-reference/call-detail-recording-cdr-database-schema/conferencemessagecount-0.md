---
title: "ConferenceMessageCount view"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/9/2015
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 8ee3ee95-fb78-4d4e-bcdd-6ce5a0a23b44
description: "The ConferenceMessageCount view stores information about how many messages were sent by a user to a conference. This view was introduced in Microsoft Lync Server 2013."
---

# ConferenceMessageCount view
 
The ConferenceMessageCount view stores information about how many messages were sent by a user to a conference. This view was introduced in Microsoft Lync Server 2013.
  
> [!NOTE]
> The ConferenceMessageCount view contains all of the columns in the [ConferenceSessionDetails view](conferencesessiondetails.md) in addition the columns listed below.
  
|**Column**|**Data Type**|**Details**|
|:-----|:-----|:-----|
|**UserUri** <br/> |nvarchar(450)  <br/> |URI of the user who sent the message.  <br/> |
|**UserUriType** <br/> |nvarchar(256)  <br/> |Type of URI of the user who sent the messages. See the [UriTypes table](uritypes.md) for more information. <br/> |
|**UserTenant** <br/> |uniqueidentifier  <br/> |Tenant of user who sent the messages. See the [Tenants table](tenants.md) for more information. <br/> |
|**UserMessageCount** <br/> |smallint  <br/> |Number of messages sent by the user during the conference session.  <br/> |
   

