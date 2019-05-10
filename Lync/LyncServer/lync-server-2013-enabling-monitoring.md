---
title: 'Lync Server 2013: Enabling monitoring'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Enabling monitoring
ms:assetid: 244df419-d0a8-4b1d-aedd-a92114172ab6
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ687994(v=OCS.15)
ms:contentKeyID: 49733584
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Enabling monitoring in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-17_

Although the unified data collection agents are automatically installed and activated on each Front End server, that does not mean that you will automatically begin to collect monitoring data the moment you finish installing Microsoft Lync Server 2013. Instead, you must do two things: you must associate your Front End servers/Front End pools with a monitoring database, and you must enable call detail recording (CDR) and/or Quality of Experience (QoE) monitoring at the global scope and/or the site scope.

For step-by-step instructions on associating Front End servers or Front End pools with a monitoring database, see the topic [Associating a monitoring store with a Front End pool in Lync Server 2013](lync-server-2013-associating-a-monitoring-store-with-a-front-end-pool.md) in the Deployment guide. After these associations have been made, and after your new Lync Server topology has been published, you will still not be able to collect monitoring data. That's because, by default, both CDR and QoE data collection is disabled when you install Lync Server 2013.

In order to begin data collection you will need to enable CDR and/or QoE monitoring. (Note that you do not have to enable both CDR and QoE monitoring; if you prefer, you can enable one type of monitoring while leaving the other type disabled.) To enable CDR monitoring at the global scope run the following command from within the Lync Server Management Shell:

    Set-CsCdrConfiguration -Identity "global" -EnableCDR $True

Alternatively, you can enable CDR monitoring from within the Lync Server 2013 Control Panel. From within the Lync Server Control Panel, complete the following procedure:

1.  Click **Monitoring**.

2.  On the **Call Detail Recording** tab, double-click the **Global** setting.

3.  In the **Edit Call Detail Recording (CDR) Setting** pane, select **Enable monitoring of CDRs** and then click **Commit**.

To enable QoE monitoring at the global scope, run this command from within the Lync Server Management Shell:

    Set-CsQoEConfiguration -Identity "global" -EnableQoE $True

If you prefer, you can also enable QoE monitoring from within the Lync Server Control Panel. From within the Control Panel, complete the following procedure:

1.  Click **Monitoring**.

2.  On the **Quality of Experience Data** tab, double-click the **Global** setting.

3.  In the **Edit Quality of Experience (QoE) Setting** pane, select **Enable monitoring of QoE data** and then click **Commit**.

As noted, the preceding examples enable monitoring at the global scope; that is, they enable CDR and QoE monitoring throughout your organization. Alternatively, you can create separate CDR and QoE configuration settings at the site scope, and then selectively enable or disable monitoring for each site. For example, you could enable CDR monitoring for your Redmond site, yet disable CDR monitoring for your Dublin site. For more information on managing your monitoring configuration settings, see the Deployment guide topic [Configuring call detail recording and Quality of Experience settings in Lync Server 2013](lync-server-2013-configuring-call-detail-recording-and-quality-of-experience-settings.md).

</div>

<span> </span>

</div>

</div>

</div>

