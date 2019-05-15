---
title: 'Using the Lync Server 2010 management packs in a coexistence scenario'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Using the Lync Server 2010 management packs in a coexistence scenario
ms:assetid: 8b792503-bd88-47fe-9d97-b071e8d429a5
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205078(v=OCS.15)
ms:contentKeyID: 48184772
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Using the Lync Server 2010 management packs in a coexistence scenario

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-22_

Many customers adopt a rollout program inside of their enterprises in which users are progressively migrated from Microsoft Lync Server 2010 to Lync Server 2013. The administrators at these companies will care about monitoring both versions of Lync Server to help ensure that all of their end users are getting the best possible communication experience. For this scenario, the Lync Server 2013 Management Pack supports a side-by-side migration path with the Lync Server 2010 Management Pack.

In the Lync Server 2010, Lync Server computers were discovered through the topology document stored with the Central Management store. In this configuration, a single computer would report the existence of all the other Lync Server computers.

The management packs for Lync Server 2013 now use machine-level discovery instead of the central discovery mechanism that was used in Lync Server 2010. This means that each System Center agent essentially discovers itself and reports its existence to System Center Operations Manager. Using machine-level discovery simplifies administration of your System Center infrastructure and also enables different versions of the Lync Server management packs (for example, management packs for Lync Server 2010 and management packs for Lync Server 2013) to coexist more easily.

To support this migration, you will first need to upgrade your existing Lync Server 2010 monitoring to avoid gaps in coverage. To do this, elect an existing Lync Server 2010 computer to service the Central Discovery script for the Lync Server 2010 before upgrading your Central Management store to Lync Server 2013. This is a four-step process:

1.  Upgrade the Lync Server 2010 Management Packs to Cumulative Update 7.

2.  Instruct a Lync Server 2010 computer to run the Central Discovery script.

3.  Override the Central Discovery Candidate in the Microsoft Lync Server 2010 Management Pack.

4.  Verify that the new Central Discovery Candidate has been discovered.

<div>

## Instructing a Lync Server 2010 Computer to Run the Central Discovery script

To nominate a non-Central Management store computer (for example, a Lync Server Front End) server to handle central discovery, you will need to create the following registry key on the non-Central Management store server:

HKLM\\Software\\Microsoft\\Real-Time Communications\\Health\\CentralDiscoveryCandidate

You can create this registry key by completing the following procedure:

1.  Click **Start** and then click **Run**.

2.  In the **Run** dialog box, type **regedit** and then press ENTER.

3.  In Registry Editor, expand **HKEY\_LOCAL\_MACHINE**, expand **SOFTWARE**, expand **Microsoft**, and then expand **Real-Time Communications**.

4.  Right-click **Health**, click **New**, and then click **Key**. If the **Health** key does not exist, then right-click **Real-Time Communications**, point to **New**, and then click **Key**. When the new key is created, type Health, and then press ENTER.
    
    After the new key has been created, type **CentralDiscoveryCandidate** and then press ENTER to rename the key.

It may take the computer several hours to pick up this change. To make the change take effect immediately, stop and then restart the Health Agent service. To restart the Health Agent service, complete the following procedure on the Lync Server 2010 computer:

1.  Click **Start**, click **All Programs**, click **Accessories**, right-click **Command Prompt**, and then click **Run as administrator**.

2.  In the console window, type the following command and then press ENTER:
    
        Net stop HealthService

3.  You will see a message that states "The System Center Management service is stopping," followed by a second message that tells you that the service has been stopped. After the service has stopped, you can restart it by typing the following command and pressing ENTER:
    
        Net start HealthService

</div>

<div>

## Overriding the Central Discovery Candidate in the Lync Server 2010 Management Pack

After instructing a Lync Server 2010 computer to report on Lync Server 2010 computers, you will need to inform the Lync Server 2010 Management Pack about this change as well. To do this, you will need to create an override in the Management Pack. That can be done by completing the following procedure:

1.  In the Operations Manager console, click **Authoring**.

2.  On the Authoring tab, expand **Management Pack Objects**, click **Object Discoveries**, and then click **Scope**.

3.  In the **Scope Management Pack Objects** dialog box, select the item with the Target **LS Discovery Candidate** and then click **OK**. Note that LS Discovery Candidate will appear only if you have installed the Lync Server 2010 Management Pack.

4.  In the Operations Manager console, right-click **LS Discovery Candidate**, point to **Overrides**, point to **Override the Object Discovery**, and then click **For all objects of class: LS Discovery Candidate**.

5.  In the **Override Properties** dialog box, select the **Override** check box next to the parameter **Central Discovery WatcherNode Fqdn**. Type the fully qualified domain name of the Lync Server 2010 computer in the **Override Value** and **Effective Value** boxes. Select the **Enforced** check box and click **OK**.

After you have created the override, you need to restart the health service on the Root Management Server. To restart the health service, complete the following procedure on the Root Management Server:

1.  Click **Start**, click **All Programs**, click **Accessories**, right-click **Command Prompt**, and then click **Run as administrator**.

2.  In the console window, type the following command, and then press ENTER:
    
        Net stop HealthService

3.  You will see a message stating that "The System Center Management service is stopping," followed by a second message that tells you that the service has been stopped. After the service has stopped, you can then restart it by typing the following command and pressing ENTER:
    
        Net start HealthService

</div>

<div>

## Verifying that the New Central Discovery Candidate Was Discovered

The final step before upgrading Central Management store is to make sure that the new central discovery candidate was discovered by the Lync Server 2010 Management Pack. To do this, open the Operations Manager console and then click Monitoring. On the Monitoring tab, expand **Microsoft Lync Server 2010 Health**, expand **Topology Discovery**, and then click **Discovery State View**. Verify that a row in the display has a **Path** that lists the fully qualified domain name of the central discovery candidate. You should also verify that the computer state is reported as **Healthy**.

</div>

</div>

<span> </span>

</div>

</div>

</div>

