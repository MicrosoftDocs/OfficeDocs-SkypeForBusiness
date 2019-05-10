---
title: 'Lync Server 2013: Configuring Archiving options at the global level'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configuring Archiving options at the global level
ms:assetid: bfe415f7-2abf-41ee-a1cb-cf48b2d59c0c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205233(v=OCS.15)
ms:contentKeyID: 48185303
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring Archiving options at the global level in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-10_

When you add Archiving to your topology and publish the topology, Lync Server creates a global configuration for Archiving. By default, no Archiving options are enabled in the global configuration. The global configuration controls which options are enabled for your entire deployment, unless you set up site or pool configurations, which override the global configuration.

For details about how Archiving configurations work, including the hierarchy for global, site, and pool configurations, see [How Archiving works in Lync Server 2013](lync-server-2013-how-archiving-works.md) in the Planning documentation, Deployment documentation, or Operations documentation.

<div>


> [!NOTE]  
> You should specify all appropriate options in the Archiving configurations before enabling Archiving.



</div>

<div>

## To configure archiving options at the global level

1.  From a user account that is assigned to the CsArchivingAdministrator or CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server 2013 Control Panel. For details about the different methods that you can use to start Lync Server 2013 Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Monitoring and Archiving**, and then click **Archiving Configuration**.

4.  On the **Archiving Configuration** page, click **Global**, click **Edit**, and then click **Show details**.

5.  In **Edit Archiving Setting - Global**, in the **Archiving setting** drop-down list, select one of the following archiving options:
    
      - **Disable archiving**
    
      - **Archive IM sessions**
    
      - **Archive IM and web conferencing sessions**

6.  Also on the **Edit Archiving Setting – Global** page, do the following:
    
      - To block activity when archiving is not available, select the **Block instant messaging (IM) or web conferencing sessions if archiving fails** check box.
    
      - To use Microsoft Exchange Server to store archiving data, click the **Microsoft Exchange integration** check box.
    
      - To enable data purging, select the **Enable purging of archiving data** check box, and then do one of the following:
        
          - To specify purging after a specific number of days, click **Purge exported archiving data and stored archiving data after maximum duration (days)**, and then specify the number of days.
        
          - To limit purging to archiving data that has been exported, click **Purge exported archiving data only**.

7.  Click **Commit**.

</div>

</div>

<span> </span>

</div>

</div>

</div>

