---
title: "Disabling network media bypass in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 936d2678-d712-4589-b172-b5793013652f
description: "Media bypass settings apply globally across a Microsoft Lync Server 2013 deployment. Media bypass allows calls to bypass the Mediation Server. For details about when to use Media bypass, see Planning for media bypass in Lync Server 2013 in the Planning section.You can disable media bypass from the Lync Server Control Panel. For details on enabling and configuring medial bypass, see Enabling network media bypass in Lync Server 2013"
---

# Disabling network media bypass in Lync Server 2013
[]
Media bypass settings apply globally across a Microsoft Lync Server 2013 deployment. Media bypass allows calls to bypass the Mediation Server. For details about when to use Media bypass, see [Planning for media bypass in Lync Server 2013](planning-for-media-bypass.md) in the Planning section.You can disable media bypass from the Lync Server Control Panel. For details on enabling and configuring medial bypass, see [Enabling network media bypass in Lync Server 2013](enabling-network-media-bypass.md)
  
### To disable media bypass

1. From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Network Configuration** and then click **Global**.
    
4. On the **Global** page, click the **Global** configuration. There is always only one configuration, and it is always named Global. 
    
5. On the **Edit** menu, click **View details**.
    
6. On the **Edit Global Setting** page, clear the **Enable media bypass** check box. 
    
7. Click **Commit** to save your changes. 
    
## See also

#### 

[Enabling network media bypass in Lync Server 2013](enabling-network-media-bypass.md)

