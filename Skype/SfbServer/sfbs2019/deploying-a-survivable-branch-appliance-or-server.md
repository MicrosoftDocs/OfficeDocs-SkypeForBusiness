---
title: "Deploying a Survivable Branch Appliance or Server with Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 12/10/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: cb780c14-dc5f-41ba-8092-f20ae905bd16
description: "Resilient Enterprise Voice refers to branch-site resiliency, that is, the ability to provide continuous Enterprise Voice service to branch site users in the event that the link to the central site becomes unavailable."
---

# Deploying a Survivable Branch Appliance or Server with Lync Server 2013
[]
Resilient Enterprise Voice refers to branch-site resiliency, that is, the ability to provide continuous Enterprise Voice service to branch site users in the event that the link to the central site becomes unavailable. 
  
For small and medium-sized branch sites (branch sites with 25 to 1,000 users), we recommend deploying a Survivable Branch Appliance, which will terminate public switched telephone network (PSTN) calls by using its built-in PSTN gateway or a SIP trunk to a telephone service provider. A Survivable Branch Appliance is a third-party device that includes a blade server running the Windows Server 2008 R2 operating system, Lync Server 2013 Registrar, Mediation Server software, and a PSTN gateway, all in a single appliance chassis. 
  
For branch sites with 1,000 to 5,000 users and no resilient WAN, we recommend a Survivable Branch Server connected to either a PSTN gateway or a SIP trunk to a telephone service provider. A Survivable Branch Server is a Windows Server-based computer that has Registrar and Mediation Server software installed on it. 
  
> [!NOTE]
> For branch sites with more than 5,000 users and dedicated Lync Server administrators, we recommend a full Lync Server 2013 deployment, separate from that of the central site. > For details about choosing the best resiliency solution for the branch sites in your organization, including prerequisites and planning considerations, see [Branch-site resiliency requirements for Lync Server 2013](branch-site-resiliency-requirements.md) in the Planning documentation. 
  
> [!NOTE]
> Users who are homed on a Lync Server Survivable Branch Appliance are unable to create new chat rooms or view the room card for existing rooms. 
  
## In this section

- [Deploying a Survivable Branch Appliance or Server with Lync Server 2013 - central site tasks](deploying-a-survivable-branch-appliance-or-servercentral-site-tasks.md)
    
- [Deploy a Survivable Branch Appliance or Server with Lync Server 2013 - branch site task](deploy-a-survivable-branch-appliance-or-serverbranch-site-task.md)
    
- [Configuring users for branch site resiliency in Lync Server 2013](configuring-users-for-branch-site-resiliency.md)
    
- [Home users on a Survivable Branch Appliance or Server in Lync Server 2013](home-users-on-a-survivable-branch-appliance-or-server.md)
    
- [Appendices: Survivable Branch Appliances and Servers in Lync Server 2013](appendices-survivable-branch-appliances-and-servers.md)
    
## See also

#### 

[Deploying Lync Server 2013](deploying-lync-server-2013.md)

