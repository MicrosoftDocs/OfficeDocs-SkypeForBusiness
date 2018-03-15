---
title: "ConferenceMessageCount view in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8ee3ee95-fb78-4d4e-bcdd-6ce5a0a23b44
description: "The ConferenceMessageCount view stores information about how many messages were sent by a user to a conference. This view was introduced in Microsoft Lync Server 2013."
---

# ConferenceMessageCount view in Lync Server 2013
[]
The ConferenceMessageCount view stores information about how many messages were sent by a user to a conference. This view was introduced in Microsoft Lync Server 2013.
  
> [!NOTE]
> The ConferenceMessageCount view contains all of the columns in the [ConferenceSessionDetails view in Lync Server 2013](conferencesessiondetails-view.md) in addition the columns listed below. 
  
|**Column**|**Data Type**|**Details**|
|:-----|:-----|:-----|
|**UserUri** <br/> |nvarchar(450)  <br/> |URI of the user who sent the message.  <br/> |
|**UserUriType** <br/> |nvarchar(256)  <br/> |Type of URI of the user who sent the messages. See the [UriTypes table in Lync Server 2013](uritypes-table.md) for more information.  <br/> |
|**UserTenant** <br/> |uniqueidentifier  <br/> |Tenant of user who sent the messages. See the [Tenants table in Lync Server 2013](tenants-table.md) for more information.  <br/> |
|**UserMessageCount** <br/> |smallint  <br/> |Number of messages sent by the user during the conference session.  <br/> |
   

