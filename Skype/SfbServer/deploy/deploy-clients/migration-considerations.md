---
title: "Skype Room System migration considerations"
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.reviewer: davgroom
ms.topic: quickstart
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: df9f33b6-0360-4354-b651-bd35da533e33
description: "Read this topic to learn about how to deploy Skype Room System in an environment that has multiple versions of Skype for Business Server and Lync Server."
---

# Skype Room System migration considerations
 
Read this topic to learn about how to deploy Skype Room System in an environment that has multiple versions of Skype for Business Server and Lync Server.
  
## Migration considerations

This section provides guidance if you are deploying Skype Room System in a multi-pool environment that includes different versions of Skype for Business Server, or Lync Server. 
  
The User Replicator (UR) component in Lync Server gets user objects from Active Directory and places them into the Lync Server back-end SQL Server database. Only the UR in Lync Server 2013 is aware of Skype Room System objects. The UR in previous versions of Lync Server and Office Communications Server do not detect the Active Directory attributes that designate LRS objects, and therefore was not aware of them. 
  
If a Skype Room System account tries to sign in to Lync , and performs auto discovery based on SRV record or DNS A record look up, and if those accounts point to a previous version of Lync Server or Office Communications Server, LRS will receive a 404 Not Found response from the legacy pool. The legacy pool will not be able to redirect Skype Room System to its Lync Server 2013 home pool. 
  
You can address this problem with the following options: 
  
- Point your autodiscover SRV record (_sipinternaltls._tcp.contoso.com) to Lync Server 2013 pool.
    
- If the first option isn't possible, you must manually configure LRS and provide the Lync Server 2013 pool address by directly configuring it in the Skype Room System console application. 
    
- If Skype Room System is deployed outside the corporate network, and a Lync Edge Server has been deployed and configured to point to a legacy pool or director, a secondary Edge Server site is required, which points to the Lync Server 2013 pool. Refer to the Edge Server deployment documentation for more information about deploying a secondary Edge Server. 
    
## Skype Room System Interoperability with a Lync Server 2010 Pool

During migration, if a user who is homed on a Lync Server 2010 pool schedules a meeting and invites the Skype Room System account, the Skype Room System client will have limited functionality while attending the meeting. 
  
When the Skype Room System client joins a scheduled conference call that has been organized by a user homed on Lync Server 2010, Skype Room System has the following in-meeting limitations: 
  
- Skype Room System cannot show the multi-view video gallery.
    
- If the Skype Room System client is the presenter, it cannot apply video lock on participants.
    
- Skype Room System cannot show 1080p video resolution (inbound or outbound), even if the Lync Server 2013 conferencing policy allows it, because of the following: 
    
  - Lync Server 2010 doesn't support 1080p resolution.
    
  - Skype Room System is always limited by the organizer's conferencing policy for video resolution. Therefore, even if the Lync 2010 pool supports 720p resolution, Skype Room System will not be able to take advantage of 720p resolution as long as organizer's policy doesn't support it. 
    
- Lync 2013 clients detect LRS presence in the meeting room, and they auto-mute themselves to avoid echo in the physical meeting room. This feature does not work in meetings hosted on Lync Server 2010.
    
- There are limitations on desktop sharing performance for meetings hosted on Lync Server 2010.
    
- Users won't be able to join private (restricted) meetings that are hosted on Lync 2010 with Skype Room System.
    

