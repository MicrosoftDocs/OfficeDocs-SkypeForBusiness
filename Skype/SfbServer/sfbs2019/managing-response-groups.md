---
title: "Managing response groups in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 2/2/2018
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 5a804d7d-3c1a-4647-a0e0-d5c4c8c23b73
description: "Response groups are a call management feature that enables you to queue calls that are made to a specific area, such as a Help Desk, and then route the calls to a designated group of people, called agents."
---

# Managing response groups in Lync Server 2013
[]
Response groups are a call management feature that enables you to queue calls that are made to a specific area, such as a Help Desk, and then route the calls to a designated group of people, called agents. 
  
To manage response groups, you configure agent groups, queues, and workflows, which define what happens to a call from the time it is placed until an agent answers it.
  
> [!NOTE]
> If you have more than 300 workflows in a single pool in your Response Group deployment, it is better to use Lync Server Management Shell cmdlets to create the workflows. If you use the Response Group Configuration Tool to create workflows for a pool that has more than 300 workflows, the webpage takes a long time to load. The number of agents that are indirectly associated with workflows through the queues also has a proportional effect on page loading. 
  
Topics in this section provide step-by-step procedures for tasks that you can perform to customize and maintain the Response Group application in your deployment
  
## In this section

- [Managing Response Group agent groups in Lync Server 2013](managing-response-group-agent-groups.md)
    
- [Managing Response Group queues in Lync Server 2013](managing-response-group-queues.md)
    
- [Managing Response Group workflows in Lync Server 2013](managing-response-group-workflows.md)
    
- [Managing application-level Response Group settings in Lync Server 2013](managing-application-level-response-group-settings.md)
    
- [Moving response groups to a new pool in Lync Server 2013](moving-response-groups-to-a-new-pool.md)
    
- [Managing response groups in Lync Server 2013 during a disaster](managing-response-groups-during-a-disaster.md)
    

