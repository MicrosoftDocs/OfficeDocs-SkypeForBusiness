---
title: 'Lync Server 2013: Configuring Archiving options for a pool'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configuring Archiving options for a pool
ms:assetid: b7cb0fd8-3d31-4858-a75c-c66a7742556e
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205200(v=OCS.15)
ms:contentKeyID: 48185230
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring Archiving options for a pool in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-10_

You can specify Archiving options to be applied to specific pools by creating and configuring options in an Archiving configuration for each of those pools. A pool configuration overrides the global configuration and site configuration, but only for the pool specified in the pool configuration.

For details about how Archiving configurations work, including the hierarchy for global, site, and pool configurations, see [How Archiving works in Lync Server 2013](lync-server-2013-how-archiving-works.md) in the Planning documentation, Deployment documentation, or Operations documentation.

<div>


> [!NOTE]  
> You should specify all appropriate options in the Archiving configurations before enabling Archiving. For details, see <A href="lync-server-2013-configuring-archiving-options.md">Configuring Archiving options in Lync Server 2013</A> in the Deployment documentation.



</div>

<div>

## To configure archiving options at the pool level

1.  From a user account that is assigned to the CsArchivingAdministrator or CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server 2013 Control Panel. For details about the different methods that you can use to start Lync Server 2013 Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Monitoring and Archiving**, and then click **Archiving Configuration**.

4.  On the **Archiving Configuration** page, click **New**, and then click **Pool Configuration**.

5.  In **Select a Service**, select the pool to be configured for archiving.

6.  In **New Archiving Setting**, in the **Archiving setting** drop-down list, select one of the following archiving options:
    
      - **Disable archiving**
    
      - **Archive IM sessions**
    
      - **Archive IM and web conferencing sessions**

7.  Also in **New Archiving Setting** page, do the following:
    
      - To block activity when archiving is not available, select the **Block instant messaging (IM) or web conferencing sessions if archiving fails** check box.
    
      - To use Microsoft Exchange Server to store archiving data, click the **Microsoft Exchange integration** check box.
    
      - To enable data purging, select the **Enable purging of archiving data** check box, and then do one of the following:
        
          - To specify purging after a specific number of days, click **Purge exported archiving data and stored archiving data after maximum duration (days)**, and then specify the number of days.
        
          - To limit purging to archiving data that has been exported, click **Purge exported archiving data only**.

8.  Click **Commit**.

</div>

</div>

<span> </span>

</div>

</div>

</div>

