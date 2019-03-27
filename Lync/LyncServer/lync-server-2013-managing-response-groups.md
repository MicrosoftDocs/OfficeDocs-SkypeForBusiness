---
title: 'Lync Server 2013: Managing response groups'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Managing response groups
ms:assetid: 5a804d7d-3c1a-4647-a0e0-d5c4c8c23b73
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg520996(v=OCS.15)
ms:contentKeyID: 48184222
ms.date: 02/01/2018
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Managing response groups in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2018-02-01_

Response groups are a call management feature that enables you to queue calls that are made to a specific area, such as a Help Desk, and then route the calls to a designated group of people, called *agents*.

To manage response groups, you configure agent groups, queues, and workflows, which define what happens to a call from the time it is placed until an agent answers it.

<div>


> [!NOTE]  
> If you have more than 300 workflows in a single pool in your Response Group deployment, it is better to use Lync Server Management Shell cmdlets to create the workflows. If you use the Response Group Configuration Tool to create workflows for a pool that has more than 300 workflows, the webpage takes a long time to load. The number of agents that are indirectly associated with workflows through the queues also has a proportional effect on page loading.



</div>

Topics in this section provide step-by-step procedures for tasks that you can perform to customize and maintain the Response Group application in your deployment

<div>

## In This Section

  - [Managing Response Group agent groups in Lync Server 2013](lync-server-2013-managing-response-group-agent-groups.md)

  - [Managing Response Group queues in Lync Server 2013](lync-server-2013-managing-response-group-queues.md)

  - [Managing Response Group workflows in Lync Server 2013](lync-server-2013-managing-response-group-workflows.md)

  - [Managing application-level Response Group settings in Lync Server 2013](lync-server-2013-managing-application-level-response-group-settings.md)

  - [Moving response groups to a new pool in Lync Server 2013](lync-server-2013-moving-response-groups-to-a-new-pool.md)

  - [Managing response groups in Lync Server 2013 during a disaster](lync-server-2013-managing-response-groups-during-a-disaster.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

