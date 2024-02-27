---
ms.date: 03/17/2018
title: "Skype Room System migration considerations"
ms.author: serdars
author: SerdarSoysal
manager: serdars
audience: ITPro
ms.reviewer: sohailta
ms.topic: quickstart
ms.service: skype-for-business-server
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.assetid: df9f33b6-0360-4354-b651-bd35da533e33
description: "Read this article to learn about how to deploy Skype Room System in an environment that has multiple versions of Skype for Business Server and Lync Server."
---

# Skype Room System migration considerations
 
Read this article to learn about how to deploy Skype Room System in an environment that has multiple versions of Skype for Business Server and Lync Server.
  
## Migration considerations

This section provides guidance if you're deploying Skype Room System in a multi-pool environment that includes different versions of Skype for Business Server, or Lync Server. 
  
The User Replicator (UR) component in Lync Server gets user objects from Active Directory and places them into the Lync Server back-end SQL Server database. Only the UR in Lync Server 2013 is aware of Skype Room System objects. The UR in previous versions of Lync Server and Office Communications Server don't detect the Active Directory attributes that designate LRS objects, and therefore wasn't aware of them. 
  
If a Skype Room System account tries to sign in to Lync, and performs auto discovery based on SRV record or DNS A record lookup, and if those accounts point to a previous version of Lync Server or Office Communications Server, LRS receives a 404 Not Found response from the legacy pool. The legacy pool won't be able to redirect Skype Room System to its Lync Server 2013 home pool. 
  
You can address this problem with the following options: 
  
- Point your autodiscover SRV record (_sipinternaltls._tcp.contoso.com) to Lync Server 2013 pool.
    
- If the first option isn't possible, you must manually configure LRS and provide the Lync Server 2013 pool address by directly configuring it in the Skype Room System console application. 
    
- If Skype Room System is deployed outside the corporate network, and a Lync Edge Server is deployed and configured to point to a legacy pool or director, a secondary Edge Server site is required, which points to the Lync Server 2013 pool. Refer to the Edge Server deployment documentation for more information about deploying a secondary Edge Server. 
    
## Skype Room System Interoperability with a Lync Server 2010 Pool

During migration, if a user who is homed on a Lync Server 2010 pool schedules a meeting and invites the Skype Room System account, the Skype Room System client has limited functionality while attending the meeting. 
  
When the Skype Room System client joins a scheduled conference call that is organized by a user homed on Lync Server 2010, Skype Room System has the following in-meeting limitations: 
  
- Skype Room System can't show the multi-view video gallery.
    
- If the Skype Room System client is the presenter, it can't apply video lock on participants.
    
- Skype Room System can't show 1080p video resolution (inbound or outbound), even if the Lync Server 2013 conferencing policy allows it, because of the following: 
    
  - Lync Server 2010 doesn't support 1080p resolution.
    
  - Skype Room System is always limited by the organizer's conferencing policy for video resolution. Therefore, even if the Lync 2010 pool supports 720p resolution, Skype Room System can't take advantage of 720p resolution as long as organizer's policy doesn't support it. 
    
- Lync 2013 clients detect LRS presence in the meeting room, and they automute themselves to avoid echo in the physical meeting room. This feature does not work in meetings hosted on Lync Server 2010.
    
- There are limitations on desktop sharing performance for meetings hosted on Lync Server 2010.
    
- Users can't join private (restricted) meetings that are hosted on Lync 2010 with Skype Room System.
    


