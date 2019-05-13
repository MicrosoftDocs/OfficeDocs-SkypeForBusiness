---
title: 'Deploying a Survivable Branch Appliance or Server - central site tasks'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Deploying a Survivable Branch Appliance or Server - central site tasks
ms:assetid: 0f631a36-fc2e-41cd-8a0d-f27e84f4a89e
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398189(v=OCS.15)
ms:contentKeyID: 48183422
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Deploying a Survivable Branch Appliance or Server with Lync Server 2013 - central site tasks

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-18_

Complete the tasks in this section at the central site. If you’re deploying a Survivable Branch Server, skip the first task.

<div>


> [!IMPORTANT]
> Before you perform the tasks in this section, the following conditions must be in place: 
> <UL>
> <LI>
> <P>Lync Server must be set up at the central site.</P>
> <LI>
> <P>An installation technician at the branch site must be added to the RTCUniversalSBATechnicians group.</P></LI></UL>In addition, we recommend that you do the following: 
> <UL>
> <LI>
> <P>Deploy a DHCP server at each branch site to enable clients to obtain IP addresses.</P>
> <LI>
> <P>As an alternative to deploying a DHCP server at each branch site, enable Lync Server DHCP on the Survivable Branch Appliance or Survivable Branch Server by using the Lync Server Management Shell cmdlet <STRONG>Set-CsRegistrarConfiguration –EnableDHCPServer $true</STRONG>. For details, see the “Hardware and Software Requirements” section of <A href="lync-server-2013-branch-site-resiliency-requirements.md">Branch-site resiliency requirements for Lync Server 2013</A> in the Planning documentation.</P></LI></UL>



</div>

<div>

## In This Section

  - [Add a Survivable Branch Appliance to Active Directory in Lync Server 2013](lync-server-2013-add-a-survivable-branch-appliance-to-active-directory.md)

  - [Add branch sites to your topology in Lync Server 2013](lync-server-2013-add-branch-sites-to-your-topology.md)

  - [Define a Survivable Branch Appliance or Server in Lync Server 2013](lync-server-2013-define-a-survivable-branch-appliance-or-server.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

