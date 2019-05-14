---
title: 'Lync Server 2013: Configure media bypass to always bypass the Mediation Server'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configure media bypass to always bypass the Mediation Server
ms:assetid: 370c4f54-e520-4d77-96a3-84c5e84a9996
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425846(v=OCS.15)
ms:contentKeyID: 48183819
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure media bypass in Lync Server 2013 to always bypass the Mediation Server

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-25_

<div>


> [!NOTE]  
> This topic assumes that you have already configured media bypass for any trunk connections to a peer (a public switched telephone network (PSTN) gateway, an IP-PBX, or a Session Border Controller (SBC) at an Internet Telephony Service Provider (ITSP)) for a specific site or service for which you want media to bypass the Mediation Server.<BR>You cannot configure media to always bypass the Mediation Server while also enabling call admission control. These settings are incompatible and are therefore mutually exclusive settings in the Lync Server Control Panel user interface.



</div>

In addition to enabling media bypass for individual trunk connections associated with a peer to the Mediation Server, you must also configure global settings for media bypass. If you use the steps in this topic to configure global settings for media bypass, the assumption is that you have good connectivity between Lync endpoints and any peer for which you configured media bypass on the trunk connection.

If you do not have good connectivity between Lync Server endpoints and all peers to the Mediation Server whose respective trunk connections have been enabled for media bypass, you must configure global media bypass settings to use site and region information when employing media bypass. This allows for more control in determining when media bypasses the Mediation Server. To do this, use the steps in [Configure media bypass global settings in Lync Server 2013 to use site and region information](lync-server-2013-configure-media-bypass-global-settings-to-use-site-and-region-information.md) and [Associate a subnet with a network site in Lync Server 2013](lync-server-2013-associate-a-subnet-with-a-network-site.md) instead.

<div>

## To Enable Media Bypass Globally to Always Bypass the Mediation Server

1.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

2.  In the left navigation bar, click **Network Configuration**.

3.  Double-click the **Global** configuration in the list.

4.  On the **Edit Global Setting** page, select the **Enable media bypass** check box.

5.  Click **Always bypass**.

6.  Click **Commit**.

</div>

<div>

## See Also


[Configure media bypass in Lync Server 2013](lync-server-2013-configure-media-bypass.md)  
[Global media bypass options in Lync Server 2013](lync-server-2013-global-media-bypass-options.md)  
[Media bypass and Mediation Server in Lync Server 2013](lync-server-2013-media-bypass-and-mediation-server.md)  


[Planning for media bypass in Lync Server 2013](lync-server-2013-planning-for-media-bypass.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

