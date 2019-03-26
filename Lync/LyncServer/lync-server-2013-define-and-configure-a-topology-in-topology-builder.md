---
title: 'Lync Server 2013: Define and configure a topology in Topology Builder'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Define and configure a topology in Topology Builder
ms:assetid: 99231ff5-1c21-432b-ad65-8675fcd484f9
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398788(v=OCS.15)
ms:contentKeyID: 48184953
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Define and configure a topology in Topology Builder for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

Running Topology Builder to define a new topology or to modify an existing topology does not require membership in a local administrator or privileged domain group. Topology Builder guides you through the steps necessary to define your topology for an Enterprise Edition Front End pool or a Standard Edition, based on your configuration requirements.

You must use Topology Builder to complete and publish the topology before you can install Lync Server 2013 on servers. The following procedure includes the steps required to define a new topology.

<div>

## To define a topology

1.  Start Topology Builder: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Topology Builder**.

2.  In Topology Builder, select **New Topology**. You are prompted for a location and file name for saving the topology. Give the topology file a meaningful name and accept the default extension of .tbxml. Click **OK**.

3.  Navigate to the location where you want to save the new topology XML file, enter a name for the file, and then click **Save**.

4.  On the **Define the primary domain** page, enter the name of the primary SIP domain for your organization, and then click **Next**.

5.  On the **Specify additional supported domains** page, enter the names of additional domains, if any, and then click **Next**.

6.  On the **Define the first site** page, enter a name and a description for the first site, and then click **Next**.

7.  On the **Specify site details** page, enter the location information for the site, and then click **Next**.

8.  On the **New topology was successfully defined** page, make sure the **Open the New Front End Wizard when this wizard closes** check box is selected, and then click **Finish**.

After you’ve defined and saved the topology, use the New Front End Wizard to define a Front End pool or Standard Edition server for your site. For details, see [Define and configure a Front End pool or Standard Edition server in Lync Server 2013](lync-server-2013-define-and-configure-a-front-end-pool-or-standard-edition-server.md).

</div>

</div>

<span> </span>

</div>

</div>

</div>

