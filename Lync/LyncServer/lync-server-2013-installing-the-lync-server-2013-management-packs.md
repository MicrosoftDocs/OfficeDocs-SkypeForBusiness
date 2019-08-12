---
title: 'Lync Server 2013: Installing the Lync Server 2013 management packs'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: nstalling the Lync Server 2013 management packs
ms:assetid: b800d4ab-fdc8-4c72-a76a-b78932779fe3
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205202(v=OCS.15)
ms:contentKeyID: 48185233
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Installing the Lync Server 2013 management packs

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-22_

By itself, System Center Operations Manager has the ability to monitor only a small portion of the Windows operating system. However, you can extend the capabilities of System Center Operations Manager by installing management packs, software that dictates which items System Center Operations Manager can monitor, including how those items should be monitored and how alerts should be triggered and reported. Microsoft Lync Server 2013 includes two System Center Operations Manager management packs that provide the following capabilities:

  - The Component and User Management Pack (Microsoft.LS.2013.Monitoring.ComponentAndUser.mp) tracks Lync Server issues recorded in event logs, registered by performance counters, or logged in the call detail records (CDR) or the Quality of Experience (QoE) databases. For critical problems, System Center Operations Manager can be configured to immediately notify administrators via email, instant message, or Short Message Service (SMS) messaging. SMS is the technology used to send text messages from one mobile device to another.
    
    <div>
    

    > [!NOTE]  
    > For more information on configuring Operations Manager notification, see Configuring Notification in the TechNet Library at <A class=uri href="http://go.microsoft.com/fwlink/p/?linkid=268785">http://go.microsoft.com/fwlink/p/?linkid=268785</A>.

    
    </div>

  - The Active Monitoring Pack (Microsoft.LS.2013.Monitoring.ActiveMonitoring.mp) proactively tests key Lync Server components such as logging on to the system, exchanging instant messages, or making calls to a phone located on the public switched telephone network (PSTN). These tests are conducted using the Lync Server synthetic transaction cmdlets. For example, the **Test-CsIM** cmdlet is used to simulate an instant messaging conversation between a pair of test users. If this simulated messaging conversation fails an alert will be generated.

The two management packs included with Lync Server 2013 include a large number of enhancements over the management packs used with Microsoft Lync Server 2010. For example, the Lync Server 2013 Component Management Pack is not limited to monitoring Lync Server itself. In addition to monitoring event logs and performance counters for Lync Server, the Component Management pack can also track the performance of, and issue alerts for, crucial items such as:

  - **Internet Information Services (IIS)**   Alerts will be issued if Internet Information Services goes offline. This is important, because the Lync Server web services rely on IIS.

  - **Process usage**   Alerts will be issued if system resources (such as available memory) begin to run low. These alerts will be issued even if Lync Server is not responsible for the high system usage.

  - **Computer failure events**   Alerts will be issued in case of a hardware or software issue that threatens the viability of a server. For example, Lync Server administrators will be notified if a server appears to be in danger of experiencing a hard disk failure.

The new management packs also feature enhanced reporting. New reports for Lync Server 2013 include:

  - **End to End Scenario Availability Report**   This report details the availability/uptime for key Lync Server services such as registration or presence.

  - **Capacity Report**   Using performance counter information, this report shows trends for system components such as memory availability and processor usage.

  - **Component Report**   This report lists the top alert generators grouped by Lync Server component.

In addition to these predesigned reports, the management packs for Lync Server 2013 automatically report alerts for both Call Reliability (metrics measured by Call Detail Recording) and QoE states (metrics measured by Quality of Experience). If you have enabled Call Detail Recording, you can review Call Reliability alerts by completing the following procedure from the System Center Operations Manager console:

  - Expand **Monitoring**, expand **Microsoft Lync Server 2013 Health**, expand **Call Reliability and Media Quality**, and then click **Call Reliability**.

To view Quality of Experience alerts, complete this procedure from the System Center Operations Manager console:

  - Expand **Monitoring**, expand **Microsoft Lync Server 2013 Health**, expand **Call Reliability and Media Quality**, and then expand **Media Quality**.

The management packs for Lync Server 2013 now use machine-level discovery instead of the central discovery mechanism used in Microsoft Lync Server 2010. This means that each System Center agent essentially discovers itself and reports its existence to the Central Management Server. Using machine-level discovery simplifies administration of your System Center infrastructure and also allows different versions of the Lync Server management packs (for example, management packs for Lync Server 2010 and management packs for Lync Server 2013) to coexist.

</div>

<span> </span>

</div>

</div>

</div>

