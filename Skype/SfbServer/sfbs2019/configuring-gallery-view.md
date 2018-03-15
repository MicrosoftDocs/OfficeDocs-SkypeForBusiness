---
title: "Configuring Gallery View in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 4a609178-47d8-4682-ac8d-29f882801924
description: "In Lync Server 2013, you configure Gallery View video conferencing in conferencing policy. Gallery View is turned on by default. If you do not want to allow Gallery View, or want to allow it for only some users, you need to turn off the feature in conferencing policy."
---

# Configuring Gallery View in Lync Server 2013
[]
In Lync Server 2013, you configure Gallery View video conferencing in conferencing policy. Gallery View is turned on by default. If you do not want to allow Gallery View, or want to allow it for only some users, you need to turn off the feature in conferencing policy.
  
When a conference participant's video is not available, the users' Gallery View experience can be enhanced if you deploy high-resolution photos, a new feature in Lync Server 2013. High-resolution photos provide an alternative to the smaller, limited resolution contact photos stored in Active Directory Domain Services. High-resolution photos are stored in a user's Exchange 2013 mailbox, and, therefore, require you to integrate Lync Server 2013 with Exchange 2013. For details, see the NextHop blog article, "Integrating Exchange 2013 and Lync Server 2013," at [https://go.microsoft.com/fwlink/p/?LinkId=260987](https://go.microsoft.com/fwlink/p/?LinkId=260987). 
  
> [!NOTE]
> The content of each blog and its URL are subject to change without notice. 
  
You can view or modify the Gallery View parameters by using Lync Server 2013 Control Panel or by using one of the following cmdlets: 
  
- **Get-CsConferencingPolicy**
    
- **Set-CsConferencingPolicy**
    
- **New-CsConferencingPolicy**
    
Configure Gallery View with the following conferencing policy settings:
  
- **AllowMultiview** This parameter controls whether a user is allowed to organize Gallery View video conferences. This parameter applies to scheduled and ad-hoc meetings created by the user. 
    
    Examples:
    
  - This parameter is set to True for User A, who is homed on a Lync Server 2013 pool. Meetings organized by User A enable users to join and receive multiple video streams.
    
  - This parameter is set to False for User B, who is homed on a Lync Server 2013 pool. Meetings organized by User B have a single video stream that is similar to the video conference experience provided by Lync Server 2010.
    
    This parameter determines who can organize meetings that allow multiple video streams. Participants in meetings that allow multiple video streams may or may not be allowed to receive multiple video streams, based on their individual permissions (see the description for the EnableMultiviewJoin parameter).
    
- **EnableMultiviewJoin** This parameter controls whether a participant in a meeting receives the Gallery View video experience in meetings that allow it. This parameter controls the user's experience in any meeting in which he or she participates. 
    
    Examples:
    
  - This parameter is set to True for User C. User C can receive multiple video streams when participating in a meeting organized or started by User A. User C receives a single video stream that is similar to the video conference experience provided by Lync Server 2010 when participating in a meeting organized or started by User B.
    
  - This parameter is set to False for User D. User D receives single video stream that is similar to the video conference experience provided by Lync Server 2010 when participating in any meeting organized by User A or User B.
    
The following procedure is an example of using Lync Server Management Shell to enable Gallery View video conferencing.
  
### To modify conferencing policy for Gallery View video conferencing

1. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
2. At the command line, run the following cmdlet to edit conferencing policy:
    
  ```
  Set-CsConferencingPolicy -Identity Pool01ConferencingPolicy -AllowMultiview $true -EnableMultiviewJoin $true 
  ```


