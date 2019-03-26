---
title: Configure Mediation Server
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Configure Mediation Server
ms:assetid: 583236fd-33cd-4045-81df-baa58ed07779
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204913(v=OCS.15)
ms:contentKeyID: 48184207
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure Mediation Server

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-28_

This procedure details the steps to configure the Lync Server 2013 pool to use the Lync Server 2013 Mediation Server, instead of the legacy Office Communications Server 2007 R2 Mediation Server.

To successfully publish, enable, or disable a topology when adding or removing a server role, you should be logged in as a user who is a member of the RTCUniversalServerAdmins and Domain Admins groups. It is also possible to delegate the proper administrator rights and permissions for adding server roles. For details, see Delegate Setup Permissions in the Standard Edition server or Enterprise Edition server Deployment documentation. For other configuration changes, only membership in the RTCUniversalServerAdmins group is required.

<div>


> [!NOTE]  
> For the latest information on finding qualified PSTN gateways, IP-PBXs, and SIP trunking services that work with Lync Server 2013, see "Microsoft Unified Communications Open Interoperability Program" at <A href="http://go.microsoft.com/fwlink/p/?linkid=206015">http://go.microsoft.com/fwlink/p/?linkId=206015</A>.



</div>

<div>

## To configure Mediation Server Using Topology Builder

1.  Open an existing topology from Topology Builder.

2.  In the left pane, navigate to **PSTN gateways**.

3.  Right-click **PSTN gateways**, and then click **New IP/PSTN Gateway**.

4.  Complete the **Define New IP/PSTN Gateway** page with the following information:
    
      - Enter the gateway FQDN or IP address. The FQDN of the gateway is required if the gateway uses the TLS protocol.
    
      - Accept the default value of the **Listening port for IP/PSTN gateway** or enter the new listening port if it was modified.
    
      - Set the **Sip Transport Protocol**.

5.  In the left pane, navigate to the **Enterprise Edition Front End pool** or the **Standard Edition Server**.

6.  Right-click the pool, and then click **Edit Properties**.

7.  Under **Mediation Server**, set the **Listening ports**.

8.  Next, associate the newly created PSTN gateway by selecting it and clicking **Add**.

9.  In **Topology Builder**, select the top-most node **Lync Server**.

10. From the **Action** menu, select **Publish Topology** and then click **Next**.

11. When the **Publishing wizard** completes, click **Finish** to close the wizard.

<div>


> [!NOTE]  
> It is important that you complete the next topic, <A href="change-voice-routes-to-use-the-new-lync-server-2013-mediation-server.md">Change voice routes to use the new Lync Server 2013 Mediation Server</A> to ensure that the voice routes are pointing to the correct Mediation Server.



</div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

